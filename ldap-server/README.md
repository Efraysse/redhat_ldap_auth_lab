## ldap-server


Install and configure then bitnami/openLdap container with TLS enabled and ready for system's user auth.

## Requirements

On the master Ansible server install the following packages:

\# For certificate management
```
ansible-galaxy collection install community.crypto
```
\# For container management
```
ansible-galaxy collection install containers.podman
```
\# For ldap management
```
ansible-galaxy collection install community.general
```




## Role Variables

Default variables defined in defaults/main.yml:

| Variable | Default value |
| --------|-------|
| ldap_user_password | is set to "ldap" with sha-512 method |
| ldap_admin_password | adminpassword |
| ldap_config_password | configpassword |



It is recommended to overwrite these values with your own using an ansible-vault file:

``` sh
  ansible-vault create secret.yml
```

And import the secret file in the play:

``` sh
- name: Install Ldap server
  hosts: serverb
  vars_files: secret.yml
  roles:
    - ldap-server
```

Use this command to create the hash for ldap_user_password:

``` sh
mkpasswd --method=sha-512
```


> [!NOTE]
> ldap_admin_password and ldap_config_password will be used only at the Binami OpenLdap container first creation. If you change these variables,
        the podman module will recreate the container but wil not change the initial persisted values in the ldap. If so you will need to change them
        manualy.



## References

See bitnami/openldap reference on dockerhub [bitnami/openldap](https://hub.docker.com/r/bitnami/openldap/)

## Dependencies


A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook


Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: Install Ldap server
      hosts: serverb
      vars_files: secret.yml
      roles:
        - ldap-server

## License


BSD



