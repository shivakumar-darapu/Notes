 1. **Module blacklisting** - The location for the module blacklist is defined by the plugin_filters_cfg parameter found in the defaults section of the Ansible configuration file. By default, it is disabled, and the suggested default value is set to /etc/ansible/plugin_filters.yml.
 

> For example, one of the currently deprecated modules to be completely removed in Ansible 2.11 is sf_account_manager (see https://docs.ansible.com/ansible/latest/porting_ guides/porting_guide_2.7.html#deprecation-notices). Thus, to prevent anyone from using this internally, the plugin_filters.yml file would look like this: --- filter_version:'1.0' 
module_blacklist: 
\# Deprecated – to be removed in 2.11
	\- sf_account_manager

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc5NjMzNzQwMSwtMTQ1MzAzODMzNl19
-->