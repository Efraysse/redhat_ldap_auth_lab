## ldap-client role


Deploy this role where you want to enable ldap auth for users.


## Role Variables

Variables defined in vars/main.yml

| Variable |  value |
| --------|-------|
| ca_cert_file | the location of your CA cert file  |
| ldap_uri | the uri of the ldap server |

Set these variables with your own settings e.g.

ca_cert_file: //home/student/ca_cert/EFTrust.ca.pem
ldap_uri: ldap://serverc:1389





## Example Playbook


``` sh
---
- name: Install Ldap client
  hosts: serverc
  roles:
    - ldap-client
```



