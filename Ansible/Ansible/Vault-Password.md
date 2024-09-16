 1. Vault password:
``` yaml
ansible-playbook --vault-id @prompt playbook.yaml
- If you want to obtain the Vault password from a text file, you would run the following
command:
ansible-playbook --vault-id /path-to/vault-password-text-file playbook.yaml
- Finally, if you are using an executable script, you would run the following command:
ansible-playbook --vault-id /path-to/vault-password-script.py playbook.yaml
2. Vault password:
``` yaml
ansible-playbook --vault-id @prompt playbook.yaml
If you want to obtain the Vault password from a text file, you would run the following
command:
ansible-playbook --vault-id /path-to/vault-password-text-file playbook.yaml
Finally, if you are using an executable script, you would run the following command:
ansible-playbook --vault-id /path-to/vault-password-script.py playbook.yaml
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNzI1Njg1NjcsMTMxMjg5OTcwMl19
-->