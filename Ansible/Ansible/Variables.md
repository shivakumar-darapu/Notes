

 1. The first major variable type is **inventory variables.** These are the variables that Ansible gets by way of the inventory. These can be defined as variables that are specific to host_vars, to individual hosts, or applicable to entire groups as group_vars. These variables can be written directly into the inventory file, delivered by the dynamic inventory plugin, or loaded from the host_vars/ or group_vars/ directories.
	 These types of variables might be used to define Ansible behavior when dealing with these hosts or site-specific data related to the applications that these hosts run. Whether a variable comes from host_vars or group_vars, it will be assigned to a host's hostvars, and it can be accessed from the playbooks and template files. Accessing a host's own variables can be done just by referencing the name, such as {{ foobar }}, and accessing another host's variables can be accomplished by accessing hostvars; for example, to access the foobar variable for examplehost: {{ hostvars['examplehost']['foobar'] }}. These variables have global scope
 3. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2OTQwMDYyNDIsLTE4MzY4Nzk2MzBdfQ
==
-->