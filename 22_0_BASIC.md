---
date: "2016-10-09"
draft: false
weight: 220
title: "Lab 22 - Pick One - BASIC - Install Networking on a freshly booted cloud"
---
[Click here to find out more about Alta3 Research's Openstack Training](https://alta3.com/courses/openstack)

### WEDNESDAY - &#x2B50;REQUIRED&#x2B50;

### Lab Objective

The objective of this lab is to teach what the networking aspects of a freshly deployed OpenStack cloud look like. In this lab, we'll remove any preconfig Alta3 did on your behalf, and then put it back into place.

**NOTE**: There are two versions of this lab. We recommend you pick *one* to do. This version of the lab is sufficient for most OpenStack users and administrators.

### Procedure

0. Close any old terminals you might have open on your remote desktop environment.

0. We can watch the results of the command line in Horizon. This is very instructional, so within your remote dekstop, sign into Horizon as **:default:admin:alta3:**

0. Click on **Project > Network > Network Topology**.

0. Study what is being presented. You can left click on the icons, and little pop-ups will show up explaining those icons in detail. The **provider-net**, **demo-net**, and **demorouter** were set up (by Alta3) for the admin project before you entered class. If you need help figuring out what is being presented to you, check the screenshot below.

	![Virtual Networking](https://alta3.com/static/images/alta3_lab_horizon_network_topology.png)

0. Leave the Horizon session open so you can see it. Meanwhile, launch a new terminal session on your remote desktop, then connect to controller.

    `student@beachhead:/$` `ssh controller`
    
0. Source the admin.rc file

    `student@controller:~$` `source admin.rc`

0. All instances must be deleted, so list all running instances and delete them all.

    `student@controller (admin) :~$` `openstack server list --all-projects`  

    ```
    +--------------------------------------+--------+--------+--------------------------+
    | ID                                   | Name   | Status | Networks                 |
    +--------------------------------------+--------+--------+--------------------------+
    | 8bd0d720-4053-4a36-a243-4b8edca76c3a | vt1    | ACTIVE | provider-net=172.16.2.57 |
    +--------------------------------------+--------+--------+--------------------------+
    ```
    >
    Just an FYI, if you ever get machines showing up in an "ERROR" status, they can be tough to delete. This can happen for a number of reasons, but should not happen by design. See the following thread for some helpful commands you might issue via the openstack-novaclient (https://ask.openstack.org/en/question/50410/nova-cannot-boot-or-delete-image/). If you do have a VM with a state of "ERROR", let the instructor know.
   
0. If you made some additional instances, you might see more. If you already deleted vt1, you'll see less. In any event, issue the following command against each virtual machinE'S uuid that was returned in the ID column of the last step.

    `student@controller (admin) :~$` `openstack server delete <UUID_listed_in_ID_column>`

0. Ask again for a display of all the running instances in the cloud. Nothing should be returned.
    >
    Just another FYI for anyone that has a VM in an "ERROR" status. This lab won't work if the VM is still holding an IP address on provider-net. If that is the case, look at the link above in the last step, and try to force delete the machine.
    
    `student@controller (admin) :~$` `openstack server list --all-projects`  

    ```
    +--------------------------------------+--------+--------+--------------------------+
    | ID                                   | Name   | Status | Networks                 |
    +--------------------------------------+--------+--------+--------------------------+
    +--------------------------------------+--------+--------+--------------------------+
    ```

0. Great! Now we can move on to removing all of that networking.

0. We're admin, so we can ask neutron to discover all routers that must be deleted.

    `student@controller (admin) :~$` `neutron router-list --max-width 60`

    ```
Your output should look something like this:
+--------------------------------------+------------+--------------------------------------------------------------+-------------+-------+
| id                                   | name       | external_gateway_info                                        | distributed | ha    |
+--------------------------------------+------------+--------------------------------------------------------------+-------------+-------+
| a8a2e5d7-2111-4ff9-9c5a-26fe2c9ef0c0 | demorouter | {"network_id": "b3b8d8f8-6668-48dc-b97e-db92be7c6fc7",       | False       | False |
|                                      |            | "enable_snat": true, "external_fixed_ips": [{"subnet_id":    |             |       |
|                                      |            | "571e4cd2-1b9d-4b05-9ee9-f23bc27451ae", "ip_address":        |             |       |
|                                      |            | "172.16.2.51"}]}                                             |             |       |
+--------------------------------------+------------+--------------------------------------------------------------+-------------+-------+
    ```

0. List all available subnets.

    `student@controller (admin) :~$` `neutron subnet-list` 

    ```
Your output should look something like this:
+--------------------------------------+-----------------+-----------------+----------------------------------------------------+
| id                                   | name            | cidr            | allocation_pools                                   |
+--------------------------------------+-----------------+-----------------+----------------------------------------------------+
| 571e4cd2-1b9d-4b05-9ee9-f23bc27451ae | provider-subnet | 172.16.2.0/24   | {"start": "172.16.2.50", "end": "172.16.2.250"}    |
| f2a50b9e-6ba8-4d74-8efa-ea256b253254 | demo-net_subnet | 192.168.30.0/24 | {"start": "192.168.30.2", "end": "192.168.30.254"} |
+--------------------------------------+-----------------+-----------------+----------------------------------------------------+
    ```

0. Now we need to delete all of the preconfigured aspects of networking. The graphic below depicts the order (A through F) that we'll remove this prebuilt virtual network.

    ![Trash the Neutron Preconfiguration](https://alta3.com/static/images/alta3_lab_delete_network_order.png)

0. Delete the interface on the router called demo-net_subnet (See step A in the graphic above)
    
    `student@controller (admin) :~$` `neutron router-interface-delete demorouter demo-net_subnet`

0. Delete the router demorouter (See step B in the graphic above)

    `student@controller (admin) :~$` `neutron router-delete demorouter provider-subnet`    

0. Delete the subnet demo-net_subnet (See step C in the graphic above)

    `student@controller (admin) :~$` `neutron subnet-delete demo-net_subnet`

0. Delete the network demo-net (See step D in the graphic above)

    `student@controller (admin) :~$` `neutron net-delete demo-net`

0. Delete the subnet provider-net (See step E in the graphic above)

    `student@controller (admin) :~$` `neutron subnet-delete provider-subnet`

0. Delete the network provider (See step F in the graphic above)

    `student@controller (admin) :~$` `neutron net-delete provider-net`

0. Congradulations! Now you now have the machine looking the way it did when neturon was originally deployed. All of the demonstration configuration has been removed. Now let's put it all back, step-by-step...

0. For your information, neutron is running on your controller. Controller has two (2) NICs, connected to two subnets, both connecting to the internet. These are defined as follows:

    >
    Admin network: 172.16.1.0/24
    
    >
    Provider network: 172.16.2.0/24

0. So, which NIC is assigned to the admin network, and which is assigned to the provider network? We can find this out by issuing the following command to list details regarding these two NICs within our controller:

    `student@controller (admin) :~$` `ip addr`

    ```
  1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
      link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
      inet 127.0.0.1/8 scope host lo
         valid_lft forever preferred_lft forever
      inet6 ::1/128 scope host
        valid_lft forever preferred_lft forever
  2: ens3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc pfifo_fast state UP group default qlen 1000
      link/ether fa:16:3e:2f:61:74 brd ff:ff:ff:ff:ff:ff
      inet 172.16.1.5/24 brd 172.16.1.255 scope global ens3  
         valid_lft forever preferred_lft forever
      inet6 fe80::f816:3eff:fe2f:6174/64 scope link
         valid_lft forever preferred_lft forever
  3: ens4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000 
      link/ether fa:16:3e:be:52:55 brd ff:ff:ff:ff:ff:ff
      inet6 fe80::f816:3eff:febe:5255/64 scope link   
         valid_lft forever preferred_lft forever
    ```

0. The ens3 is assiged to the admin network by virtue of its ip address 172.16.1.5 /24, which is the physical administration network. So is "ens4" the Provider NIC? Let's find out for sure. We will follow a two-step process. So first you must discover which mechanism_driver is specified in ml2_conf.ini. The egrep filter skips the comments, listing only the configuration:

    `student@controller (admin) :~$` `cat  /etc/neutron/plugins/ml2/ml2_conf.ini | egrep -v "(^#.*|^$)"`

    ```
[DEFAULT]
[ml2]
type_drivers = flat,vlan,vxlan
tenant_network_types = vxlan
mechanism_drivers = linuxbridge,l2population
extension_drivers = port_security
[ml2_type_flat]
flat_networks = provider
[ml2_type_geneve]
[ml2_type_gre]
[ml2_type_vlan]
[ml2_type_vxlan]
vni_ranges = 1:1000
[securitygroup]
enable_ipset = true
    ```
    >
    Looks like the mechanism_drivers = linuxbridge,l2population  

0. So now lets look for the NIC that is associated with the linuxbridge

    `student@controller (admin) :~$` `cat  /etc/neutron/plugins/ml2/linuxbridge_agent.ini | egrep -v "(^#.*|^$)"`

    ```
[DEFAULT]
[agent]
[linux_bridge]
physical_interface_mappings = provider:ens4
[securitygroup]
firewall_driver = neutron.agent.linux.iptables_firewall.IptablesFirewallDriver
enable_security_group = true
[vxlan]
enable_vxlan = true
local_ip = 172.16.1.5
l2_population = true
    ```

    >
    We see `physical_interface_mappings = provider:ens4`. This means the physical network interface is called "provider" and is mapped to "ens4". Some cloud operators call this "external", "public", or "fabric", so your network may use a different name here.

0. Now associate the physical interface to the provider network, with a network name "provider-net"

    `student@controller (admin) :~$` `neutron net-create --shared --provider:physical_network provider --provider:network_type flat provider-net`

0. Define a new subnet, called provider-subnet" and assign it to "provider-net"   

    `student@controller (admin) :~$` `neutron subnet-create --name provider-subnet  --allocation-pool start=172.16.2.50,end=172.16.2.250 --dns-nameserver 10.0.0.1  --gateway 172.16.2.1 provider-net 172.16.2.0/24`

0. Create a new network, sperate from the "provider-net". Call it "demo-net"  

    `student@controller (admin) :~$` `neutron net-create demo-net`

0. Create a new subnet called demo-net_subnet and assign demo-net_subnet to demo-net

    `student@controller (admin) :~$` `neutron subnet-create --name demo-net_subnet --dns-nameserver 10.0.0.1 --gateway 192.168.30.1 demo-net 192.168.30.0/24`  

0. Make the provider-net network the service provider.  
    
    `student@controller (admin) :~$` `neutron net-update provider-net --router:external`

0. Create a virtual router called **demorouter**
    
    `student@controller (admin) :~$` `neutron router-create demorouter`

0. Connect demorouter to demo-net_subnet  
    
    `student@controller (admin) :~$` `neutron router-interface-add demorouter demo-net_subnet`
    
0. Connect demorouter to povider-net.  
    
    `student@controller (admin) :~$` `neutron router-gateway-set demorouter provider-net`

0. Good job! That's it for this lab.
