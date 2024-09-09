## Change user profile directory 🪧
- ### Modify default *useradd* command settings:
```bash
$ vi /etc/default/useradd
  # useradd defaults file
  GROUP=100
  HOME=/home
  INACTIVE=-1
  EXPIRE=
  SHELL=/bin/bash
  SKEL=/etc/skel
  CREATE_MAIL_SPOOL=yes
```
> Modify HOME directory.
- ### Modify single user settings:
```bash
$ vi /etc/passwd
...
  alessio:x:1001:1001::/home/alessio:/bin/bash
```
> Find user typing "/" into vi editor and modify its directory.
