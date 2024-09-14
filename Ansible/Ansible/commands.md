# Commands

 1. For dry runs, we often use **ansible-playbook -- check**
2.  You can use the **ansible-doc** command-line tool with what you have installed to view the reference documentation and the module index mentioned previously
3. **ansible-pull** command, which can pull playbooks from a VCS repository like GitHub
4. Using the ansible-runner library, you can run an Ansible playbook from within a Python script: 

   

    #!/usr/bin/env python3  import ansible_runner r = ansible_runner.run(private_data_dir='./playbooks', playbook='playbook.yml')  print("{}: {}".format(r.status, r.rc))  print("Final status:") print(r.stats)

5. add the **-vvvv** flag to see more details about the error
6. 

> **WHERE SHOULD I PUT MY ANSIBLE.CFG FILE** ? Ansible looks for an ansible.cfg file in the following places, in this order: File specified by the ANSIBLE_CONFIG environment variable ./ansible.cfg (ansible.cfg in the current directory) ~/.ansible.cfg (.ansible.cfg in your home directory) /etc/ansible/ansible.cfg (Linux) or /usr/local/etc/ansible/ansible.cfg


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMDY3MDk0MzIsLTUxNjEwNDEwNiwxNz
E0NzU2NDkzXX0=
-->