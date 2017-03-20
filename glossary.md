---
date: "2015-10-30"
draft: false
weight: 10003
title: "Glossary"
---
[Click here to find out more about Alta3 Research's Openstack Training](https://alta3.com/courses/openstack)

* API Token  [0]  Passed on API requests and used by OpenStack services to verify that this particular user is authorized to access and run the requested operation.
* Austin  [0] The first release of OpenStack was called Austin. Unsurprisingly, the first design summit took place in this capital city of Texas. OpenStack versions are short lived, and the release dates are aggressive (about 2 new releases a year). Generally, a customer will fork an OpenStack release version, and stick with it.
* Compute  [0]  The term compute is synonymous with Nova. An OpenStack core project that provides compute services (manages VM instances).
* Compute Controller  [0]  Chooses which hosts to start a VM instance.
* Compute Host  [0]  A set of physical hardware that is dedicated to running compute nodes.
* Daemon  [0] Processes that run in the background and wait for requests. Commonly examples include glance-api, keystone-server, neutron-server, nova-api, nova-scheduler, and so on.
* ceph mds  [0] (ceph-mds) The metadata server daemon for the Ceph distributed file system. One or more instances of ceph-mds collectively manage the file system namespace, coordinating access to the shared OSD cluster. Each ceph-mds daemon instance should have a unique name. The name is used to identify daemon instances in the ceph.conf.
* Flat Mode Injection  [9]  A compute networking method where the OS network configuration information is injected into the image before the VM instance is started.
* FlatDHCP Manager  [9] The compute component that gives dnsmasq (DHCP, DNS, BOOTP, TFTP) and routing services.
* Gateway  [0] An IP addressed assigned to an interface, typically on a router, that can pass network traffic from one network to another.
* Instance Tunnels Network  [0]  A network used for instance traffic tunnels between compute nodes and the network node.
* Linux Bridge  [0]  Software that allows multiple VM instances to share a single Physical NIC within Compute.
* Multi-host  [0]  High-availability mode for legacy (nova) networking. Each compute node handles NAT and DHCP and acts as a gateway for all of the VMs on it. A networking failure on one compute node doesn't affect VMs on other compute nodes.
* Network Manager  [0] The Compute component that manages various network components, such as firewall rules, IP address allocation, and so on.
* Network Node  [0]  Any compute node that runs the network worker daemon.
* Networking  [0]  A core OpenStack project that provides a network connectivity abstraction layer to OpenStack Compute. The project name of Networking is neutron.
* Virtual Networking  [0] A generic term for virtualization of network functions such as switching, routing, load balancing, and security using a combination of VMs and overlays on physical network infrastructure.
* VLAN Network  [0] The Network Controller provides virtual networks to enable compute servers to interact with each other and with the public network. All machines must have a public and private network interface. A VLAN network is a private network interface, which is controlled by the vlan_interface option with VLAN managers.
* Community Project  [0] Projects not officially endorsed by the OpenStack Foundation. If successful, it may become an incubated project and then to a core project, or may be merged with the main code trunk.
* Orchestration  [0]  An integrated project that orchestrates multiple cloud applications for OpenStack. The project name of Orchestration is heat.
* API and API Endpoint [1] Application Programming Interface. A collection of specifications used to access a service, application, or program. In the case of an endpoint, the daemon or worker that provides the service.
* Front End  [1] The point where a user interacts with a service; can be an API endpoint, the horizon dashboard, or a command-line tool.
* Back End  [1] Any processes that are obfuscated from the user. Think daemons waiting in the background waiting for requests, or carrying out tasks in response to messages in a queue; an example might be the creation and deletion of volumes on storage arrays, or passing tokens with API calls.
* aaS [1] Stands for as a Service.  Types of aaS: Metal (MaaS), Infrastructure (IaaS), Platform (PaaS), Desktop (DaaS),  Firewall (Fwaas), Anything (XaaS)
* Core Project [1] Any official OpenStack Foundation projects; Compute (nova), Object Storage (swift), Image service (glance), Identity (keystone), Dashboard (horizon), Networking (neutron), and Block Storage (cinder), the Telemetry module (ceilometer), Orchestration module (heat), Database service (trove), Bare Metal service (ironic), Data processing service (sahara).
* Deprecate [1] This mechanism has lost favor and may be removed from future version. Currently, many of the project specific python-clients are being depreciated in favor of the python-OpenStack client.
* DevStack [1]  Great for testing and (relatively) quick to install. Community project that uses shell scripts to quickly build complete OpenStack development environments. Runs well in Debian (Ubuntu) systems
* Host [1] Synonymous with node. Refers to a physical computer, not a VM instance.
* Linux Supported  [1] OpenStack is supported on many Linux platforms, common deployments include: CentOS, SUSE Linux Enterprise Server (SLES), openSUSE, Debian, Ubuntu, Fedora and Red Hat Enterprise Linux. 
* OpenStack  [1] A cloud operating system that controls large pools of compute, storage, and networking resources throughout a data center, all managed through a dashboard that gives administrators control while empowering their users to provision resources through a web interface. OpenStack is an open source project licensed under the Apache License 2.0.
* Horizon [2]  One of the OpenStack Foundation core projects that provides a Dashboard via a web GUI interface.
* BUI [2]  Browser User Interface. Controls are presented via the web brower, as opposed to a dedicated Graphical User Interface (GUI) or Command Line Interface (CLI).
* CirrOS  [2] A small OS image packaged with Openstack. CirrOS was designed to aid in proof-of-concept testing, and was never intended for use within a production environment. For a deeper dive, check this AWESOME blog, which happens to be written by one of the co-authors of this course: http://rzfeeser.com/2016/04/19/what-is-openstack-cirros/
* Customization Module  [2] Re-skins the Dashboard. A custom made Python module loaded into Horizon to change the dashboard layout. Inclusive of visual-only, and functionality changes enhancements.
* Dashboard  [2] Another name for Horizon, the Web Graphical User Interface (or Browser User Interface) that can be used to control OpenStack. Advanced OpenStack users will not spend much time within Horizon.
* Evacuate  [3] The process of migrating one or all virtual machine (VM) instances from one host to another, compatible with both shared storage live migration and block migration.
* Injection  [3]  Files may be put into a virtual machine image before the instance is started.
* Instance  [3] A running VM, or a VM in a known state such as suspended, that can be used like a hardware server. Instance, VM, VM instance are all interchangeable terms.
* Interface  [3]  Physical or virtualized devices that interconnect devices or medium.
* Live Migration  [3]  Moving a VM instance from one host to another with a minimum service interruption.
* Pause  [3] A state a VM instance may be placed in where no changes occur (no changes in memory, network communications stop, etc); the VM is frozen but not shut down. Also known as a suspended mode.
* RAM Overcommit  [3] The ability to start new VM instances based on the actual memory usage of a host, as opposed to basing the decision on the amount of RAM each running instance thinks it has available. Also known as memory overcommit.
* Rescue Image  [3]  A special type of VM image that is booted when an instance is placed into rescue mode. Allows an administrator to mount the file systems for an instance to correct the problem.
* RESTful [3] A kind of web service API that uses REST, or Representational State Transfer. REST is the style of architecture for hypermedia systems that is used for the World Wide Web.
* Server [3] Two meanings might apply. The first, a computer that provides explicit services to the client software running on that system; LAMP, SIP, Minecraft, etc. The second is a VM instance (running within Compute).
* Snapshot  [3] A point-in-time copy of an OpenStack storage volume or image. Use storage volume snapshots to back up volumes. Use image snapshots to back up data, or as gold images for additional servers.
* Python  [3]  A popular programming language used to develop OpenStack core projects.
* Source  [3] Just like . A bash shell built-in command that executes the content of the file passed as argument, in the current shell. It has a synonym in '.'
* Hypervisor [4] Software that controls VM instance access to the underlying hardware.
* ESXi [4]  One of the hypervisors supported by OpenStack
* Quick Emulator [4] (QEMU) is a generic and open source machine emulator and virtualizer. It is one of the hypervisors supported by OpenStack, generally used for development purposes.
* Hyper V  [4] One of the hypervisors supported by OpenStack.
* VirtualBox  [4]  An OpenStack-supported hypervisor.
* Kernel Based VM  [4] (KVM) An OpenStack-supported hypervisor. KVM is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V), ARM, IBM Power, and IBM zSeries. It consists of a loadable kernel module, that provides the core virtualization infrastructure and a processor specific module.
* Guest OS  [4] The operating system on a VM instance running under the control of a hypervisor.
* Linux Containers  [4]  An OpenStack supported Linux container. Containers can be far more efficient than a VMM.
* Memory Overcommit  [4] The ability to start new VM instances based on the actual memory usage of a host, as opposed to basing the decision on the amount of RAM each running instance thinks it has available. Also known as RAM overcommit.
* Node  [4] Hardware that supports OpenStack components (Compute, Controller, Network, Storage).
* UML  [4]  (User Mode Linux) An OpenStack-supported hypervisor.
* vCPU  [4]  (Virtual Central Processing Unit) Subdivides physical CPUs. Instances can then use those divisions.
* Virtual Machine  [4] (VM) An operating system instance that runs on top of a hypervisor. Multiple VMs can run at the same time on the same physical host. Also called a virtual server, or VM instance.
* Golden Image  [4]  A method of operating system installation where a finalized disk image is created and then used by all nodes without modification.
* Keystone  [5]  One of the OpenStack Foundation core projects that provides the Identity Service.
* API Version  [5]  The API version can be found as part of the URL.
* Authentication Token  [5] (aka API Key or API Token) The identity service (Keystone) first confirms the identity of a user, process, or client; authorized because they have provided a private key, token, password, fingerprint, or similar security mechanism. The authentication token is a string of text returned to the user that is then included with a subsequent API request.
* Credentials  [5] Passed by a user during the authentication process; password, secret key, digital certificate, and fingerprint
* Customer  [5]  Synonymous with tenant or project.
* API Key  [5]  A term sometimes used to describe an API token.
* Default Tenant  [5] If a new user gets created and no tenant is specified at the time of creation, they will be assigned a default tenant (remember, tenants are projects).
* Identity  [5]  Identity is provided by the Keystone project. Provides a centralized common authentication system that maps users to the OpenStack services they can access. Also registers endpoints for OpenStack services.
* JSON  [5]  (JavaScript Object Notation) One of the supported response formats in OpenStack.
* Project  [5] Projects represent the base unit of ownership in OpenStack, in that all resources in OpenStack should be owned by a specific project. In OpenStack Identity, a project must be owned by a specific domain. A group of users is referred to as a project, or tenant. The terms are interchangeable.
* Service Catalog  [5] Also sometimes just referred to as the catalog, or the endpoint registry. Contains a list of API endpoints that are available to a user (i.e. such as Compute, Image Service, Identity, Object Storage, Block Storage, Networking, etc.) after authentication with the Identity service.
* Tenant  [5] It refers to a group of users; used to isolate access to Compute resources. Also known as a project, these terms are interchangeable. The initial implementation of OpenStack Compute had its own authentication system and used the term project. When authentication moved into the OpenStack Identity (keystone) project, it used the term tenant to refer to a group of users. Because of this legacy, some of the OpenStack tools refer to projects and some refer to tenants. 
* User  [5] In OpenStack Identity, entities represent individual API consumers and are owned by a specific domain. In OpenStack Compute, a user can be associated with roles, projects, or both.
* Absolute Limit  [6] Ceiling (limits) for guest VMs. Controlled by defining total limits on RAM, number of vCPUs, and disk size.
* Scheduler  [6] The manager that determines which compute node will host a new instance. Types of schedulers: Chance, Fill First, or write your own filter.
* Compute Node  [6] (aka Compute, Compute Host, Compute Controller) Runs the nova-compute daemon, which is responsible for managing VM instances.
* Flavor  [6] Synonymous with VM instance type. Definable parameters include: Flavor ID, Name, VCPUs, RAM, Root Disk GB, Ephemeral Disk GB, and Swap. Simply put, it is the size of the VM instance that may be launched. Default flavors are: m1.tiny, m1.small, m1.medium, m1.large, m1.xlarge.
* Nebula  [6]  A NASA open source release that serves as the basis for Compute.
* Nova  [6]  A core OpenStack project that manages compute services.
* SDN  [7]  Software Defined Networking. The revolution that will do to networking what VoIP did to voice.
* ASIC  [7] Application Specific Integrated Circuit. An IC chip that is custom built to perform a specific function. ASICs are very expensive to develop since they are 100% hardware, but generally offer exceptional performance.
* Merchant Silicon  [7] A mass produced ASIC, generally sold to smaller manufacturers to build powerful hardware without the expense of designing and building their own ASICs.
* Middleboxes  [7] Networking equipment excluding routers and switches. Examples would be firewalls, SBC, CSCF, SGSN, GGSN, MME, etc.
* NFV  [7]  Network Function Virtualization. Simply running a network function on top of a hypervisor rather than on dedicated boxes.
* OpenFlow  [7]  A set of primitives that provides a common control language to control routing and switching functions.
* TRILL  [8] Transparent Interconnection of Lots of Links is an IETF Standard implemented by devices called RBridges (routing bridges) or TRILL Switches. TRILL combines techniques from bridging and routing and is the application of link state routing to the VLAN-aware customer-bridging problem. They are invisible to current IP routers and, like routers, RBridges terminate the bridge spanning tree protocol.
* STP  [8]  Spanning Tree Protocol.  The original layer two protocol to ensure a loop free topology. From the Jurassic era of bridging. 
* Network Namespace  [8]  Linux kernel feature that provides independent virtual networking instances on a single host with separate routing tables and interfaces. Similar to virtual routing and forwarding (VRF) services on physical network equipment.
* Network [9] In OpenStack, a fully isolated Ethernet network. 100% layer 2 (L2)
* Address Pool  [9]  A list of the fixed and/or floating IP addresses that are allocated/assigned to a project (tenant) to be used or assigned to the VM instances in a project.
* Floating IP Address  [9] IP address that a project can associate with a VM instance so that it has the same public IP address each time it boots. Create a pool of floating IP addresses, then assign them to instances (usually when they are launched) to maintain a consistent IP address for maintaining DNS assignments.
* Distributed Virtual Router  [9]  (DVR) Highly-available multi-host routing using OpenStack Networking (neutron).
* dnsmasq  [9]  A tiny DHCP and DNS service that efficiently manages local DNS and DHCP.
* Domain  [9] Domain can refer to an Identity API v3 entity where it would reference a collection of projects, groups and users that defines administrative boundaries for managing OpenStack Identity entities. When talking about the internet, it is the name space that is to the left of the TLD (.com, .gov., .edu, and so on) that must be unique.
* External Network  [9]  Usually the network that a VM instance will use to access the internet.
* Fixed IP Address  [9] Also known as a static IP address. To be associated with the same instance every time that instance boots. Used for managing that instance, and not typically accessible from the public-web.
* Flat Network  [9] The provider network is a single flat layer 2 network. IP Tables on the VM's security Group is used to isolate subnets.
* Integration Bridge  [9]  Basically acts like a VLAN switch within the compute node.  Operating at L2, it isolates tenant networks from each other, interconnecting tenant's instances with their own networking services including: dnsmasq service; virtual routers; and the provider networks.
* Provider Bridge - VXLAN [9]  Has only one outward facing interface which uses VXLAN to isolate L2 networks. Connects inward directly to the Integration Bridge.
* Provider Bridge - GRE [9]  Has only one outward facing interface which uses GRE to isolate L2 networks. Connects inward directly to the Integration Bridge.
* Provider Bridge - VLAN [9]  Has only one outward facing interface which uses VLAN to isolate L2 networks. Connects inward directly to the Integration Bridge.
* Management Network  [9] A network segment used by OpenStack core systems, (Nova, Neutron, Glance, Cinder, etc), not accessible to the public Internet.
* Network Controller  [9] Compute daemon that orchestrates the network configuration of nodes, including IP addresses, VLANs, and bridging. Also manages routing for both public and private networks. Also called Network Manager or Network Node
* Open vSwitch  [9] Open vSwitch is a production quality, multilayer virtual switch licensed under the open source Apache 2.0 license. It is designed to enable massive network automation through programmatic extension, while still supporting standard management interfaces and protocols (for example NetFlow, sFlow, SPAN, RSPAN, CLI, LACP, 802.1ag).
* SR-IOV  [9]  Intel's Single Root IO Virtualization hardware that accelerates Ethernet forwarding using a processor on the NIC which forwards directly to the VM using direct memory access.  
* Glance  [10]  One of the OpenStack Foundation core projects that provides the Image Service.
* Raw  [10]  One of the VM image disk formats supported by Image service; an unstructured disk image.
* Cache Pruner  [10] Image cache has a configurable maximum size. If glance-cache-pruner is running, and the image_cache_max_size is exceeded, it will start running and try to remove images in a stalled or invalid state due to image cache writing failing to complete, or not being written properly. It is recommended that cron is used to fire off glance-cache-pruner at a regular interval.
* Container Format  [10] Wrapper used by the Image service (glance) that contains a VM image and its associated metadata, such as machine state, OS disk size, and so on.
* Image  [10] Specifies the OS that you use to create or rebuild a server. OpenStack provides pre-built images. You can also create custom images, or snapshots, from servers that you have launched. Custom images can be used for data backups or as gold images for additional servers.
* Private Image  [10]  An image that is only available to a particular tenant.
* Golden Image  [10]  A method of operating system installation where a finalized disk image is created and then used by all nodes without modification.
* QCOW2  [10]  (QEMU Copy On Write 2) One of the VM image disk formats supported by Image service.
* Swift  [11] An OpenStack core project that provides object storage services.
* Container  [11]  Organizes and stores objects in Object Storage. Similar to the concept of a Linux directory but cannot be nested. Alternative term for an Image service container format.
* Integrity Check  [11] A period comparison between the stored file's computed MD5 value and its MD5 value stored in the metadata. When the two match, the file passes this integrity check.
* Large Object  [11]  An object within Object Storage that is larger than 5 GB.
* Object  [11]  A BLOB of data held by Object Storage; includes any format.
* Rebalance  [11]  Distributing Object Storage partitions across all drives in the ring; used during initial ring creation and after ring reconfiguration.
* Replication  [11] The process of copying data to a separate physical device for fault tolerance and performance.
* Replica Count  [11] The total count of replicas of the data in an Object Storage ring, including the origional.
* Rotted  [11] Slang used by storage administrators to describe a file whose MD5 has no longer matches the MD5 hash in the metadata, indicating that file integrity was lost, most likely due to a disk error or failure.
* Space  [11]  Computer science slang that describes any area with defined boundaries as a "space".
* Storage Node  [11] An Object Storage node that provides container services, account services, and object services; controls the account databases, container databases, and object storage.
* Ceph  [12] The OpenStack storage system of choice because it is massively scalable, and therefore well suited for big data. Ceph uses a distributed storage system that consists of an object and block store, as well as a POSIX-compatible distributed file system.
* Monitor  [12] (Mon) A Ceph component that communicates with external clients, checks data state and consistency, and performs quorum functions.
* OSD  [12]  an Object Storage Device or Object Storage Daemon is the Ceph storage daemon. An OSD is typically a single spinning disk for the actual storage, along with a bit of SSD for journaling. Many OSDs make up a Ceph storage cluster. 
* RADOS  [12] (Reliable, Autonomic Distributed Object Store) Collection of components that provides object storage within Ceph. Similar to OpenStack Object Storage.
* RADOS Block Device (RBD)  [12]  Ceph component that enables a Linux block device to be striped over multiple distributed data stores.
* Cinder  [13]  An OpenStack service that provides block storage for VM instances.
* Block Device  [13] A device that moves data in the form of blocks. These device nodes interface the devices, such as hard disks, CD-ROM drives, flash drives, and other addressable regions of memory.
* Ephemeral Volume  [13] A volume that does not save the changes made to it, therefore, it will return to the original state when the user relinquishes control.
* Fibre Channel  [13] (FC) A network technology commonly running at 2, 4, 8, and 16 Gbps primarily used to connect computers to data storage. Developed during the Jurassic period of computing, millions of web years ago (1988)
* InfiniBand  [13] (IB) A high bit rate communications link used in half of todays super computers. Can be much faster than 10Gbps Ethernet, with 2015 speeds expected to reach 300 Gps. Normally implemented with fiber, but copper links up to 30 meters are possible with IB.  
* Raw Device Mapping  [13]  (RDM) An option in the VMware server virtualization environment that enables a storage logical unit number (LUN) to be directly connected to a virtual machine (VM) from the storage area network (SAN).
* Shared Storage  [13] Block storage that is simultaneously accessible by multiple clients, for example, NFS.
* Volume  [13]  Disk-based data storage generally represented as an iSCSI target with a file system that supports extended attributes; can be persistent or ephemeral.
* Ceilometer  [14] The project name for the main component of the OpenStack Telemetry service, which is an integrated project that provides real-time metering and measuring facilities for OpenStack.
* Telemetry  [14] An integrated project that provides metering and measuring facilities for OpenStack. The project is inclusive of Ceilometer, Aodh, and Gnocchi.
* Aodh [14] Part of the telemetry wheelhouse, Aodh examines Ceilometer statistics to trigger alarms and events. An alarm can be set on a single metric, or on a combination. For example, you may want to trigger an alarm (and action) when the memory consumption reaches 70% on a given instance for 5 minutes. An Irish word for fire, the thinking is the fire will create heat (Aodh will trigger Heat), where heat makes the cloud rise. To setup an alarm, call Aodh’s API specifying the alarm conditions and action.
* Gnocchi [14] Part of the telemetry wheelhouse, Gnocchi provides Time Series Database as a Service (TSDBaas), which is the association of timestamps with data and metrics collected by Ceilometer. Using Gnocchi, admins can examine historical usage of the cloud.
* Bursting  [14]  Utilizing a secondary environment to dynamically build instances on-demand when the primary environment is resource constrained.
* AMQP [15] Advanced Message Queuing Protocol
* Fan Out Exchange  [15] Within RabbitMQ and Compute, it is the messaging interface that is used by the scheduler service to receive capability messages from the compute, volume, and network nodes.
* ZeroMQ [15] Often written "0MQ". A high performance, highly available message queuing library for OpenStack that will displace RabbitMQ at the cost of much more work to configure and deploy.
* Database Service  [16]  An integrated project that provide scalable and reliable Cloud Database-as-a-Service functionality for both relational and non-relational database engines. The project name of Database service is trove.
* NTP  [16] (Network Time Protocol) A method of keeping a clock for a host or node correct through communications with a trusted, accurate time source.
* Trove  [16]  OpenStack project that provides database services to applications.
* Git  [17] Free version control software created by Linus Torvalds in 2005 for Linux kernel development. Primarily used for software development, including OpenStack. Distributed model with complete history and version tracking without relying on client-server systems.
* GitHub  [17] A website that enhances the functionality of Git by exposing Git users to a social community. Allows users to visualize projects and branches, host repositories, share ideas, and contact information.  
* Repository  [17] The purpose of Git is to manage a project, or a set of files, as they change over time. Git stores this information in a data structure called a repository.
* Bare  [17] A repository without a clear working directory, therefore, cannot be used for development work just maintain commits. The central repository is typically a bare repository. 
* Non-bare  [17]  A repository with a working directory. Cloned repositories for development work are non-bare. 
* Git Clone  [17]  Developers will typically clone a central repository so that they can develop in parallel. 
* Git Directory  [17] The .git directory is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer. Typically exists on the central repository.
* Working Directory  [17]  A single version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.
* Staging Area  [17] You modify files in your working directory, then stage the files. Staged files are snapshots, but not permanently committed. Staged files are permanently snapshotted when they are committed.
* Git Pull [17] Step 1. Pulls in work from the central repository, bringing your working directory to the latest version.
* Git Add [17] Step 2. Adds specified files to the staging area.
* Git Commit  [17] Step 3. Takes all of the files in the staging area, and stores that snapshot permanently to your Git directory. All commits can be referenced by a UUID, and include metadata such as the author, date, contact info, notes, etc. A commit is synonymous with version.
* Git Push  [17] Step 4 Local commit is pushed to a targeted library. This can be forceful, and disrupt a current working branch, therefore, a push should only ever target the central repository (which has no working directory).
* DEVOPS  [18] Software defined infrastructure. Your data center is now defined by code, permitting continuous release of new features. Nobody turns a wrench. Read the Phoenix Project to clearly understand its impact.
* Immutable Infrastructure  [18] Stability, efficiency, and fidelity to your applications through automation and the use of successful patterns from programming. No rigorous or standardized definition of immutable infrastructure exists yet, but the basic idea is that you create and operate your infrastructure using the programming concept of immutability: once you instantiate something, you never change it. Instead, you replace it with another instance to make changes or ensure proper behavior.
* YAML  [18]  Stands for Yet Another Markup Language and is popular with many of the newest devops tools
* Chef  [18]  Devops configuration management tool supporting OpenStack deployments.
* Puppet  [18]  Devops configuration management tool supporting OpenStack deployments.
* Ansible [18] DEVOPs automation tool named after the faster-than-light communications channel described in the science fiction novel Ender's Game. Ender Wiggens called Earth, via Ansible
* Heat  [18]  One of the OpenStack Foundation core projects that orchestrates multiple cloud applications for OpenStack.
* Heat Stack  [18] A collection of  objects or resources that will be created by Heat. Objects can be instances, networks, subnets, routers, ports, router interfaces, security groups, security group rules, auto-scaling rules, etc.
* HOT  [18] (Heat Orchestration Template) Heat input in the format native to OpenStack. Formatted in YAML.  HOT is the newer of two template formats used by heat.  If you wanted to have a stack that created two instances connected by a private network, then your template would contain the definitions for two instances, a network, a subnet, and two network ports.
* CFN  [18] Short for AWS CloudFormation, this is the second template format that is supported by Heat. CFN-formatted templates are typically expressed in JSON.
* Ironic  [18] OpenStack project that provisions bare metal, as opposed to VM instances.
* High Availability  [19]  A high availability system design approach and associated service implementation ensures that a prearranged level of operational performance will be met during a contractual measurement period. High availability systems seeks to minimize system downtime and data loss.
* Active Passive Configuration  [19] In a high-availability setup with an active/passive configuration, systems are set up to bring additional resources online to replace those that have failed.
* Security Group  [20]  An IP table application to protect instances from unwanted traffic.
* Token  [20]  An alpha-numeric string of text used to access OpenStack APIs and resources.
