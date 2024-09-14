# Commands

 1. For dry runs, we often use **ansible-playbook -- check**
2.  You can use the **ansible-doc** command-line tool with what you have installed to view the reference documentation and the module index mentioned previously
3. **ansible-pull** command, which can pull playbooks from a VCS repository like GitHub
4. Using the ansible-runner library, you can run an Ansible playbook from within a Python script: 

   

> #!/usr/bin/env python3 
> import ansible_runner r = ansible_runner.run(private_data_dir='./playbooks', playbook='playbook.yml') 
> print("{}: {}".format(r.status, r.rc)) 
> print("Final status:") print(r.stats)


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcwMTEzMzddfQ==
-->