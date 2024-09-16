 1. **Module blacklisting** - The location for the module blacklist is defined by the plugin_filters_cfg parameter found in the defaults section of the Ansible configuration file. By default, it is disabled, and the suggested default value is set to /etc/ansible/plugin_filters.yml.
 

> For example, one of the currently deprecated modules to be completely removed in Ansible 2.11 is sf_account_manager (see https://docs.ansible.com/ansible/latest/porting_ guides/porting_guide_2.7.html#deprecation-notices). Thus, to prevent anyone from using this internally, the plugin_filters.yml file would look like this: --- filter_version:'1.0' 
module_blacklist: 
\# Deprecated – to be removed in 2.11
	\- sf_account_manager

2. **Task performance** - The first is an SSH feature, **ControlPersist**, which provides a mechanism to create persistent sockets when first connecting to a remote host that can be reused in subsequent connections to bypass some of the handshaking required when creating a connection. This can drastically reduce the amount of time Ansible spends on opening new connections. Ansible automatically utilizes this feature if the host platform where Ansible is run from supports it. To check whether your platform supports this feature, check the SSH man page for ControlPersist.
3.  **Task performance** - The second performance enhancement that can be utilized is an Ansible feature called **pipelining**. Pipelining is available to SSH-based connection methods and is configured in the Ansible configuration file within the ssh_connection section: [ssh_connection] pipelining=true This setting changes how modules are transported. Instead of opening an SSH connection to create a directory, another to write out the composed module, and a third to execute and clean up, Ansible will instead open an SSH connection on the remote host. Then, over that live connection, Ansible will pipe in the zipped composed module code and script for execution. This reduces the connections from three to one, which can really add up. By default, pipelining is disabled.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYyNTAxNDU3NSwxNzk2MzM3NDAxLC0xND
UzMDM4MzM2XX0=
-->