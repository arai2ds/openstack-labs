---
date: "2016-10-09"
draft: true
weight: 210
title: "Lab 21 - Introduction to OpenStack API Endpoints"
---
[Click here to find out more about Alta3 Research's Openstack Training](https://alta3.com/courses/openstack)

### TUESDAY - &#x2B50;REQUIRED&#x2B50;

### Lab Objective

The objective of this lab is learn abou tthe metadata service utilized by compute. Compute uses a metadata service for virtual machine instances to retrieve instance-specific data. Instances access the metadata service at http://169.254.169.254. The metadata service supports two sets of APIs: an OpenStack metadata API and an EC2-compatible API. Both APIs are versioned by date.

### Procedure

0. Now let's set some metadata about our instance. Here I am using mtag1, but you can use anything. Try starting with the following:

	`ender@controller admin >` `nova meta $VAR_UUID set mtag1='vault_tek box'`
	
9. Look to see that your first metadata tag has been set.

	`[root@controller ~(keystone_admin)]#` `nova show $VAR_UUID`
	
10. Now let's set a second metadata tag concerning our instance.

	`[root@controller ~(keystone_admin)]#` `nova meta $VAR_UUID set mtag2='uh oh I set this tag incorrectly'`
	
11. Look to see that your second metadata tag has been set.

	`[root@controller ~(keystone_admin)]#` `nova show $VAR_UUID`

12. Now remove the second metadata tag.

    `[root@controller ~(keystone_admin)]#` `nova meta $VAR_UUID delete mtag2`
	
13. Confirm the second metadata tag has been deleted.

	`[root@controller ~(keystone_admin)]#` `nova show $VAR_UUID`
	
#### Additional Learning / References

The following are a list of pages we thought might be helpful for our students to know about:

* [Overview of OpenStack Metadata Types](http://www.madorn.com/openstack-metadata-types.html#.V8RmppgrJpg)

* [OpenStack Nova Compute MetaData Service](http://docs.openstack.org/admin-guide/compute-networking-nova.html#metadata-service)
