# Project Title

We have three roles

**ldap-server:** Provide a containerized openldap environement ready for Unix user management. This role will also create the server certificate signed with your own CA auth. The sudo schema will be installed and a sudo rule is set to allow users from "ldapuser" group to sudo.

**ldap-manager:** This role will install a containerized WebApp that will be used to register Unix groups and users in the Ldap.

**ldap-client:** Customize a server for users ldap authentication. This role will enable the mk-homedir feature so homedirs for users will be automaticaly created. Users defined in the "ldapuser" group will be able to sudo root as we saw.

[Contribution guidelines for this project](ldap-server/README.md)
