

 1. The first major variable type is **inventory variables.** These are the variables that Ansible gets by way of the inventory. These can be defined as variables that are specific to host_vars, to individual hosts, or applicable to entire groups as group_vars. These variables can be written directly into the inventory file, delivered by the dynamic inventory plugin, or loaded from the host_vars/ or group_vars/ directories.
	 These types of variables might be used to define Ansible behavior when dealing with these hosts or site-specific data related to the applications that these hosts run. Whether a variable comes from host_vars or group_vars, it will be assigned to a host's hostvars, and it can be accessed from the playbooks and template files. Accessing a host's own variables can be done just by referencing the name, such as {{ foobar }}, and accessing another host's variables can be accomplished by accessing hostvars; for example, to access the foobar variable for examplehost: {{ hostvars['examplehost']['foobar'] }}. These variables have global scope
 2. The second major variable type is **role variables**. These are variables specific to a role and are utilized by the role tasks – however, it should be noted that once a role has been added to a playbook, its variables are generally accessible throughout the rest of the playbook, including from within other roles. In most simple playbooks, this won't matter, as the roles are typically run one at a time, but it is worth remembering this as playbook structure gets more complex—otherwise, unexpected behavior may result from variables being set within a different role!
 3. The third major variable type is **play variable**s. These variables are defined in the control keys of a play, either directly by the vars key or sourced from external files via the vars_files key. Additionally, the play can interactively prompt the user for variable data using vars_prompt. These variables are to be used within the scope of the play and in any tasks or included tasks of the play. The variables apply to all hosts within the play and can be referenced as if they are hostvars.
 4. The fourth variable type is task variables. Task variables are made from data discovered while executing tasks or in the fact-gathering phase of a play. These variables are hostspecific and are added to the host's hostvars and can be used as such, which also means they have global scope after the point in which they were discovered or defined. Variables of this type can be discovered via gather_facts and fact modules (modules that do not alter state but rather return data), populated from task return data via the register task key or defined directly by a task making use of the set_fact or add_host modules. Data can also be interactively obtained from the operator using the prompt argument to the pause module and registering the result: 
 

> - name: get the operators name     
> pause: 
>   ..prompt: "Please enter your name" 
> register: opname

5.The extra variables, or extra-vars type, are variables supplied on the command line when executing ansible-playbook via --extra-vars. Variable data can be supplied as a list of key=value pairs, a quoted piece of JSON data, or a reference to a YAML-formatted file with variable data defined within: 

> --extra-vars "foo=bar owner=fred" 
> --extra-vars '{"services":["nova-api","nova-conductor"]}' 
> --extra-vars @/path/to/data.yaml

6. In addition to the previously listed variable types, Ansible offers a set of variables that deserve their own special mention – magic variables. These are variables that are always set when a playbook is run without them having to be explicitly created. Their names are always reserved and should not be used for other variables. Magic variables are used to provide information about the current playbook run to the playbooks themselves and are extremely useful as Ansible environments become larger and more complex. For example, if one of your plays needs information about which groups the current host is in, the group_names magic variable returns a list of these. Similarly, if you need to configure the hostname for a service using Ansible, the inventory_hostname magic variable will return the current hostname as it is defined in the inventory. A simple example of this would be as follows:

```YAML
--- 
-   name: demonstrate magic variables 
	hosts: all 
	gather_facts: false 
	tasks: 
		- name: tell us which host we are on 
		  debug: 
			  var: inventory_hostname 
		- name: tell us which groups we are in 
		  debug: 
			  var: group_names
```

> https://docs.ansible. com/ansible/latest/reference_appendices/special_variables.html.
7. Accessing external data Data for role variables, play variables, and task variables can also come from external sources. Ansible provides a mechanism to access and evaluate data from the control machine (the machine running ansible-playbook). The mechanism is called a lookup plugin, and a number of them come with Ansible. These plugins can be used to look up or access data by reading files, generate and locally store passwords on the Ansible host for later reuse, evaluate environment variables, pipe data in from executables, access data in the Redis or etcd systems, render data from template files, query dnstxt records, and more. The syntax is as follows: lookup('', 'plugin_argument') For example, to use the mastery value from etcd in a debug task, execute the following command: 
- name: show data from etcd 
  debug: 
	  msg: "{{ lookup('etcd', 'mastery') }}"
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTkwMjUxNDcsMTE5MjI1MDg5NCw5Mj
E4ODA4MzgsLTEwNDkyNjgwNTcsLTE2OTQwMDYyNDIsLTE4MzY4
Nzk2MzBdfQ==
-->