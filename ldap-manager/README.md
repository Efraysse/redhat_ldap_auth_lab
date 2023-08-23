## ldap-manager role


Install and configure a web based LDAP manager container.
This role is intented to be added to the server owning the ldap-server role.
It will provide a webapp to manage unix users and groups.

## Requirements

On the master Ansible server install the following packages:

\# For container management
```
ansible-galaxy collection install containers.podman
```




## Role Variables

Default variables defined in defaults/main.yml:

| Variable | Default value |
| --------|-------|
| lam_pwd | master password and lam profile password is set to "lam"  |
| lam_port | port redirection of the webapp is set 8080 |



It is recommended to overwrite the password value with your own using an ansible-vault file:

``` sh
  ansible-vault create secret.yml
```

And import the secret file in the play:

``` sh
- name: Install LAM server
  hosts: serverc
  vars_files: secret.yml
  roles:
    - ldap-manager
```



## References

See LDAPAccountManager/lam reference on Github [LDAPAccountManager/lam](https://github.com/LDAPAccountManager/lam)



## Example Playbook


``` sh
- name: Install LAM server
  hosts: serverc
  vars_files: secret.yml
  vars:
    lam_port: 8081
  roles:
    - ldap-manager
```

Run and prompt for the secret password defined for secret.yml
``` sh
ansible-playbook -K --vault-id @prompt lam.yml
```


