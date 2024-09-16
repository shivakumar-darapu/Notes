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
If you are working with IDs, simply add the ID in front of the password source, followed
by the @ character—if your ID for your Vault is prod, for example, the three preceding
examples become the following:
ansible-playbook --vault-id prod@prompt playbook.yaml
ansible-playbook --vault-id prod@/path-to/vault-password-text-file
playbook.yaml
ansible-playbook --vault-id prod@/path-to/vault-password-script.py
playbook.yaml


```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMwMjc5MDQ0NSwxMzEyODk5NzAyXX0=
-->