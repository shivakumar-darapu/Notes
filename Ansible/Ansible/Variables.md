

 1. The first major variable type is **inventory variables.** These are the variables that Ansible gets by way of the inventory. These can be defined as variables that are specific to host_vars, to individual hosts, or applicable to entire groups as group_vars. These variables can be written directly into the inventory file, delivered by the dynamic inventory plugin, or loaded from the host_vars/ or group_vars/ directories.
	 These types of variables might be used to define Ansible behavior when dealing with these hosts or site-specific data related to the applications that these hosts run. Whether a variable comes from host_vars or group_vars, it will be assigned to a host's hostvars, and it can be accessed from the playbooks and template files. Accessing a host's own variables can be done just by referencing the name, such as {{ foobar }}, and accessing another host's variables can be accomplished by accessing hostvars; for example, to access the foobar variable for examplehost: {{ hostvars['examplehost']['foobar'] }}. These variables have global scope
 2. The second major variable type is **role variables**. These are variables specific to a role and are utilized by the role tasks – however, it should be noted that once a role has been added to a playbook, its variables are generally accessible throughout the rest of the playbook, including from within other roles. In most simple playbooks, this won't matter, as the roles are typically run one at a time, but it is worth remembering this as playbook structure gets more complex—otherwise, unexpected behavior may result from variables being set within a different role!
 3. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM1NDM2ODg0OSwtMTA0OTI2ODA1NywtMT
Y5NDAwNjI0MiwtMTgzNjg3OTYzMF19
-->