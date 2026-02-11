# LDAP

## Commands
### Search for a user

```bash
ldapsearch -x -H ldap://ldap.example.com -D "cn=admin,dc=example,dc=com" -W -b "dc=example,dc=com" "(uid=jdoe)"
```
