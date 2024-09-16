# OpenLDAP (CentOS) 📂
---
## 1. Enable EPEL repository
```bash
$ dnf install epel-release
```

## 2. Install OpenLDAP
```bash
$ dnf -y install openldap openldap-servers openldap-clients
```

## 3. Start/Enable service
```bash
$ systemctl start slapd.service
$ systemctl enable slapd.service
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

## 7. Configure olcRootDN administrator
- Create root password
```bash
$ slappasswd
  New password:
  Re-enter new password:
  {SSHA}VLZAQjBjBxw9VmZc6V2EnMjhUmlNXI5X
```
- Create rootpwd.ldif file in user directory
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

```

>[!NOTE]
>Credit to [www.ibm.com](https://www.ibm.com/docs/en/rpa/23.0?topic=ldap-installing-configuring-openldap)

>[!NOTE]
>Config OpenLDAP client [www.ibm.com](https://www.ibm.com/support/pages/how-configure-client-machine-running-centos-authenticate-openldap)
