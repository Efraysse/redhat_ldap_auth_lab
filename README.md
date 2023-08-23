# Set a lab openldap infrastructure for Unix users authentication

The idea is to have a set of ansible roles to quickly deploy an openldap with TLS enbled, register users and groups and configure clients for ldap auth.
We have three roles :

**[ldap-server](ldap-server/README.md):** Provide a containerized openldap environement ready for Unix user management. This role will also create the server certificate signed with your own CA auth. The sudo schema will be installed and a sudo rule is set to allow users from "ldapuser" group to sudo.

**[ldap-manager](ldap-server/README.md):** This role will install a containerized WebApp that will be used to register Unix groups and users in the Ldap.

**[ldap-client](ldap-server/README.md):** Customize a server for users ldap authentication. This role will enable the mk-homedir feature so homedirs for users will be automaticaly created. Users defined in the "ldapuser" group will be able to sudo root as we saw.

