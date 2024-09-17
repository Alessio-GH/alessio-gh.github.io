# OpenLDAP (CentOS)
---
## 1. Enable EPEL repository
```bash
$ dnf install epel-release
```

## 2. Install OpenLDAP
```bash
$ dnf -y install openldap openldap-servers openldap-clients
```

## 3. Enable/Start service
```bash
$ systemctl enable slapd.service
$ systemctl start slapd.service
```

## 4. Add firewall exeption
```bash
$ firewall-cmd --permanent --add-port=389/tcp --add-port=389/udp
$ firewall-cmd --reload
```

## 5. SELinux configuration
```bash
$ setsebool -P allow_ypbind=1 authlogin_nsswitch_use_ldap=1
$ setsebool -P httpd_can_connect_ldap on
```

## 6. Edit OpenLDAP config files
```bash
$ vi /etc/openldap/ldap.conf
  BASE     dc=example,dc=com
  URI      ldap://ldap.example.com ldap://ldap-master.example.com:666
```
> change default settings with your OpenLDAP server name and IP:
```bash
$ vi /etc/openldap/ldap.conf
  BASE    dc=LDAP,dc=com
  URI     ldap://192.168.159.131
```

## 7. Import LDAP schemas
```bash
$ ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/openldap/schema/cosine.ldif
$ ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/openldap/schema/nis.ldif
$ ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/openldap/schema/inetorgperson.ldif
$ ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/openldap/schema/openldap.ldif
$ ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/openldap/schema/dyngroup.ldif
```

## 8. Configure olcRootDN administrator
- Create root password:
```bash
$ slappasswd
  New password:
  Re-enter new password:
  {SSHA}VLZAQjBjBxw9VmZc6V2EnMjhUmlNXI5X
```

- Create rootpwd.ldif file in user directory:
```bash
$ cd /home/mele/Public
$ vi rootpwd.ldif
...
  dn: olcDatabase={0}config,cn=config
  changetype: modify
  add: olcRootPW
  olcRootPW: {SSHA}VLZAQjBjBxw9VmZc6V2EnMjhUmlNXI5X
...
$ ldapadd -Y EXTERNAL -H ldapi:/// -f rootpwd.ldif
  SASL/EXTERNAL authentication started
  SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
  SASL SSF: 0
  modifying entry "olcDatabase={0}config,cn=config"
```

## 9. Configure manager user
- Create manager.ldif file in user directory:
```bash
$ cd /home/mele/Public
$ vi manager.ldif
...
  dn: olcDatabase={2}mdb,cn=config
  changetype: modify
  replace: olcSuffix
  olcSuffix: dc=LDAP,dc=com
  
  dn: olcDatabase={2}mdb,cn=config
  changetype: modify
  replace: olcRootDN
  olcRootDN: cn=manager,dc=LDAP,dc=com
  
  dn: olcDatabase={2}mdb,cn=config
  changetype: modify
  add: olcRootPW
  olcRootPW: {SSHA}VLZAQjBjBxw9VmZc6V2EnMjhUmlNXI5X
...
$ ldapmodify -Y EXTERNAL -H ldapi:/// -f manager.ldif
  SASL/EXTERNAL authentication started
  SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
  SASL SSF: 0
  modifying entry "olcDatabase={2}mdb,cn=config"
  
  modifying entry "olcDatabase={2}mdb,cn=config"
  
  modifying entry "olcDatabase={2}mdb,cn=config"
```

## 10. Configure groups
- Create org.ldif file in user directory:
```bash
$ cd /home/mele/Public
$ vi org.ldif
...
  dn: dc=LDAP,dc=com
  objectClass: top
  objectClass: dcObject
  objectclass: organization
  o: LDAP Server
  dc: LDAP
  
  dn: cn=manager,dc=LDAP,dc=com
  objectClass: organizationalRole
  cn: manager
  description: LDAP manager
  
  dn: ou=LDAPusers,dc=LDAP,dc=com
  objectClass: organizationalUnit
  ou: LDAPusers
...
$ ldapadd -x -D cn=manager,dc=LDAP,dc=com -W -f org.ldif
  Enter LDAP Password:
  adding new entry "dc=LDAP,dc=com"
  
  adding new entry "cn=manager,dc=LDAP,dc=com"
  
  adding new entry "ou=LDAPusers,dc=LDAP,dc=com"
```

## 11. Configure new users
- Create [username].ldif file in user directory **REPLACING [username]** with the name of the user that you want to add:
```bash
$ cd /home/mele/Public
$ vi [username].ldif
...
  dn: cn=display_name,dc=LDAP,dc=com
  changetype: add
  objectClass: inetOrgPerson
  objectClass: organizationalPerson
  objectClass: person
  objectClass: top
  uid: [username]
  cn: display_name
  sn: surname
  displayName: display_name
  mail: [username]@example.com
  userPassword: {SSHA}VLZAQjBjBxw9VmZc6V2EnMjhUmlNXI5X
...
$ ldapadd -D "cn=manager,dc=LDAP,dc=com" -W -f [username].ldif
  Enter LDAP Password:
  adding new entry "cn=display name,dc=LDAP,dc=com"
```

>[!NOTE]
>Credit to [www.ibm.com](https://www.ibm.com/docs/en/rpa/23.0?topic=ldap-installing-configuring-openldap)

>[!NOTE]
>Config OpenLDAP client [www.ibm.com](https://www.ibm.com/support/pages/how-configure-client-machine-running-centos-authenticate-openldap)

[↩️](../Linux.html)
