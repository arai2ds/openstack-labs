---
date: "2016-12-14"
draft: false
weight: 320
title: "Lab 32 - Ansible"
---
[Click here to find out more about Alta3 Research's Openstack Training](https://alta3.com/courses/openstack)

### THURSDAY - &#x1F528;OPTIONAL&#x1F528;

### Lab Objective

The objective of this lab is to introduce you to the basics of ansible. You will learn the syntax and mechanisms for one-off commands, inventories to reach multiple hosts, and playbooks to accomplish complex and multi-part tasks.

An appropriate `ssh` environment amiable to ansible has been setup for you inside this lab environment. This is usually a non-trivial amount of work which involves setting up passwordless sudoers and distributing public keys.

Ansible documentation is found here: http://devdocs.io/ansible/

### Procedure
 
1. SSH to your controller 

    `[student@beachhead ~]#` `ssh controller`  
    `[student@controller ~]#` `cd`  

3. Ensure ansible is installed.

    `[student@controller ~]$` `ansible --version`  
    `[student@controller ~]$` `ansible -h | less`  
    
    > It's always useful to check out the help file.  
    > Take a second and look for some key words which should be familiar from the lecture.  
    > Type `q` to quit  

4. Create a simple `hosts` file with the following content:

    `[student@controller ~]$` `vim hosts`

    **Enter:** `i` lower case **i** to enter INSERT mode.
   
    **Enter this content:**

    ```
    172.16.1.5
    ```

  **Enter:** `Escape`  `:`  `wq`
  
5. Use the ping ansible module to test connectivity to the controller

    `[student@controller ~]$` `ansible all -i hosts -m ping`

    ```
    172.16.1.5 | success >> { 
        "changed": false,
        "ping": "pong" 
    }
    ```

    > The above text will be <span style="color:green;">GREEN</span>.  
    > Refer back to the help command and read what each of these flags represent.  

6. Gather Facts about controller with ansible

    `[student@controller ~]$` `ansible all -i hosts -m setup | less`
   
    > Skim through these facts and look for interesting values.  
    > How many processor cores does this node have?  Which Linux kernel?  
    > Which release of Ubuntu is it running?  
    > All of these variables are  available to your playbooks.  
    > These can be very useful for eliminating many repetitive information gathering tasksin your environments!

7. Now lets replace what is in our hosts file with the following content. Type the following command:

    `[student@controller ~]$` `vim hosts`

    **Enter:** `i` lower case **i** to enter INSERT mode.

     **Enter this content:**

    ```
    [openstack]
    controller ansible_ssh_host=172.168.1.5
    compute1   ansible_ssh_host=172.168.1.6
    compute2   ansible_ssh_host=172.168.1.7
    ```

  **Enter:** `Escape`  `:`  `wq`

8. Confirm that you did **NOT** forget to make **[openstack]** the fist entry in your hosts file!

    `cat hosts`   

9. Ping all your hosts
   
    `[student@controller ~]$` `ansible all -i hosts -m ping`  

    > The **"all"** pattern targets all hosts in the inventory
    > **-i** specifies a certian inventory file (a listing of hosts)
    > **"hosts"** is the traditional inventory filename.
    > **-m** specifies a certian module, in this case **"ping"**

9. Try different `host-pattern`s and modules 

    `[student@controller ~]$` `ansible openstack -i hosts -m command -a 'hostname'`  
    `[student@controller ~]$` `ansible controller -i hosts -m command -a 'whoami'`  
    `[student@controller ~]$` `ansible openstack -i hosts -m command -a '/sbin/ip addr'`  

    > Read about modules [HERE](http://docs.ansible.com/ansible/list_of_all_modules.html)  
    > Check out the custom Open Stack modules while you are at this link! 

10. Red ink - this command will fail.  The goal here is to demonstrate what ansible looks like when it has a failure.

    `[student@controller ~]$` `ansible openstack -i hosts -m apt -a 'name=htop state=installed'`

    > What is the reason for this error?

11. Gather some information about our compute nodes
   
    `[student@controller ~]$` `ansible compute1 -i hosts -m setup | grep vcpus`  
    `[student@controller ~]$` `ansible compute2 -i hosts -m setup | grep vcpus`  

At this point you now know how to run ansible one-off commands. These can be very useful for making changes and gathering information from your systems quickly and efficiently from a central location. Next we will use an ansible playbook to accomplish an ordered list of tasks.

#### 2. Ansible Playbooks


Ansible playbooks are an efficient way to organize a list of ordered tasks. These tasks are grouped into a play which specify which hosts will be configured. In this section we will make a simple playbook that installs a new program to our controller.

0. Use curl to view the below files, then use wget to fetch them.

    `[student@controller ~]$` `curl https://alta3.com/static/files/jinja-test.yml`  
    `[student@controller ~]$` `curl https://alta3.com/static/files/jinja-test.j2`  
    `[student@controller ~]$` `wget https://alta3.com/static/files/jinja-test.yml`  
    `[student@controller ~]$` `wget https://alta3.com/static/files/jinja-test.j2`  

0. Run `ansible-playbook` to test and demonstrate a Jinja 2 template

    `[student@controller ~]$` `ansible-playbook -i hosts jinja-test.yml`

0. Display the contents of the newly deployed file on all the systems
    
    `[student@controller ~]$` `ansible openstack -i hosts -m command -a 'cat ~/nursery.ini'`

0. Now develop a playbook which will deploy the following `ovs.j2` file into `/tmp/ovs.ini`.  You can use the jinja-test.yml playbook as a starting point.  

 ```
 - hosts: openstack
   remote_user: student
   vars:
     farm_animal: lamb
     fleece_color: white
     fleece_simile: snow
   tasks:
   - name: create nursery song ini file
     template:
       src: jinja-test.j2
       dest: ~/nursery.ini
 ```

  * `[student@controller ~]$` `curl https://alta3.com/static/files/ovs.j2`  
  * `[student@controller ~]$` `wget https://alta3.com/static/files/ovs.j2`  
    
  Make sure these values get deployed into the resulting `ovs.ini` file:  

  * `tunnel_types = vxlan`
  * `bridge_mappings = external:br-ex`
  * `firewall_driver = iptables_hybrid`

  After completion, you should be able to run the below command and view the resulting `/tmp/ovs.ini` on all `openstack` systems.

  `[student@controller ~]$` `ansible openstack -i hosts -m command -a 'cat /tmp/ovs.ini'`  
