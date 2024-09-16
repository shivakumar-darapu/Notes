# Inventory

1.  [multi:children] --> group of groups , meaning it wont contain a list of servers but rather groups.
2.  [dev] --> grouping of servers.
3.  [multi:vars] --> variables for all the servers.
4.	Group Variables

-   vars: Define variables specific to a group of hosts.
-   vars_files: Include variables from external files.
-   children: Define sub-groups (nested groups) within a group.

5. Host Variables

-   vars: Define variables specific to an individual host.
-   ansible_host: The IP address or hostname of the host.
-   ansible_port: The SSH port for connecting to the host.
-   ansible_user: The SSH user for connecting to the host.
-   ansible_ssh_private_key_file: The SSH private key file for connecting to the host.
-   ansible_become: Whether to use privilege escalation (sudo).
-   ansible_become_user: The user to become when using privilege escalation.
-   ansible_connection: The connection type (e.g., ssh, local, docker).
-   ansible_python_interpreter: The path to the Python interpreter on the host.
-   ansible_shell_type: The shell type to use (e.g., bash, sh).

6. Host and Group Variables (Shared)

-   ansible_ssh_common_args: Additional SSH arguments.
-   ansible_ssh_extra_args: Extra SSH arguments.
-   ansible_ssh_pipelining: Whether to use SSH pipelining.
-   ansible_ssh_retries: Number of SSH connection retries.
-   ansible_ssh_timeout: SSH connection timeout.
-   ansible_ssh_extra_args: Extra SSH arguments.

7. Special Variables

-   ansible_host: Alias for the actual hostname or IP address.
-   ansible_port: The SSH port to use.
-   ansible_user: The SSH user to use.
-   ansible_password: The SSH password to use (if applicable).
-   ansible_ssh_private_key_file: The path to the private key file for SSH.

8. Dynamic Inventory

For dynamic inventories, variables can be set by the dynamic inventory script or plugin, and the structure is similar to static inventories, but may vary based on the source of the dynamic data.

9. GROUP PRIORITY 
Ansible 2.4 introduced the ansible_group_priority group variable, which can be used to set the priority of precedence for value whose key name match in vars of group variables if present in two groups. 

### Example of a Simple Inventory File with Variables

Static Inventory Example

""" yaml
`# hosts.ini`

`[webservers]`

`web1 ansible_host=192.168.1.10 ansible_user=ubuntu`

`web2 ansible_host=192.168.1.11 ansible_user=ubuntu`

`[dbservers]`

`db1 ansible_host=192.168.1.20 ansible_user=admin ansible_ssh_private_key_file=/path/to/key`

`[webservers:vars]`

`http_port=80`

`max_clients=200`

`[dbservers:vars]`

`db_port=5432`
"""

    `# hosts.ini`

`[webservers]`

`web1 ansible_host=192.168.1.10 ansible_user=ubuntu`

`web2 ansible_host=192.168.1.11 ansible_user=ubuntu`

`[dbservers]`

`db1 ansible_host=192.168.1.20 ansible_user=admin ansible_ssh_private_key_file=/path/to/key`

`[webservers:vars]`

`http_port=80`

`max_clients=200`

`[dbservers:vars]`

`db_port=5432`



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwOTMwMTkyMzFdfQ==
-->