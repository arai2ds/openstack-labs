---
date: "2016-10-10"
draft: false
weight: 10001
title: "Instructors & Students: Quick Fixes & Lab Tips"
---

### Fixes

#### Quick Lab Fixes

0. Reset aliceanderson password example:
   `keystone user-password-update aliceanderson --pass fa5tpa55w0rd`

0. How to "unsource" your bash session  
   `source /home/student/unset.rc`
   
   >
   or
   
   `.bashrc`

#### A fix to avoid slow yum mirror in anisble lab when a mirror is down and yum slows to a craw or completely fails.

0. Why are YUM updates taking so long!!
  - Here is the YUM mirror status: http://mirror-status.centos.org/
  - Here is yum.conf file info: https://docs.fedoraproject.org/en-US/Fedora/15/html/Deployment_Guide/sec-Configuring_Yum_and_Yum_Repositories.html
  - The default retries before YUM advances to the next mirror is **10 (TEN!!!)** retries, let's make that 1:
Copy this text into the files directory and name the file "yum.conf"

0. In your home directory, make a new directory called "files"

0. copy /etc/yum.conf to /~/files

0. Edit your new yum.conf file by adding **retries=1** to the bottom of the config as shown below. 

<pre>
[main]
cachedir=/var/cache/yum/$basearch/$releasever
keepcache=0
debuglevel=2
logfile=/var/log/yum.log
exactarch=1
obsoletes=1
gpgcheck=1
plugins=1
installonly_limit=5
bugtracker_url=http://bugs.centos.org/set_project.php?project_id=23&ref=http://bugs.centos.org/bug_report_page.php?category=yum
distroverpkg=centos-release
retries=1
</pre>

5. Save the file

6. After you have downloaded sl.yml file, modify it to look like this:

<pre> 
- hosts: openstack
  remote_user: root
  tasks:
  - name: Look at me adding my first line of devops code! The next line of code updates yum.conf on all my hosts, this is really cool.
    copy: src=/home/centos/files/yum.conf dest=/etc/yum.conf owner=root group=root mode=0644
  - name: Install sl even though I have no idea what sl does... yet.
    yum: name=sl state=installed
</pre>

Now run the sl.yml playbook and it should go a lot faster.


#### Add Interface example

  `source keystonerc_chestercopperpot`
  
  `neutron net-list`
 
  `nova   interface-attach    --net-id  a0a1ac28-e581-4937-9667-632bc6a1470a`

  `neutron   port-create    --security-group http-ssh        a0a1ac28-e581-4937-9667-632bc6a1470a`
  
  `nova interface-attach    --port-id 6c65150b-4b8a-4e3d-84eb-bebce64b228a    vt2`
