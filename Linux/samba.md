# Samba sharing
---
## - Prerequisites
```bash
$ yum install samba samba-client samba-common # install packages
$ firewall-cmd --permanent --zone=public --add-service=samba # add firewall rule
$ firewall-cmd –-reload # restart firewall
$ useradd alessio # create a new user
$ groupadd smbgrp # create a new group
$ usermod -a -G smbgrp alessio # add new user to new group
$ smbpasswd -a alessio # set password
  New SMB password: <password>
  Retype new SMB password: <password> 
  Added user alessio 
```

## - Shared folder config
```bash
$ mkdir -p /home/samba # create directory to share
$ chown -R alessio:smbgrp /home/samba # change owner
$ chmod -R 770 /home/samba # change permissions
$ chcon -t samba_share_t /home/samba # set SELinux policy
$ vi /etc/samba/smb.conf # add the following lines
...
  [global] 
  workgroup = WORKGROUP 
  netbios name = CentOS 
  security = user 
  map to guest = bad user 
  dns proxy = no
  
  [Share] # shared folder name
  path = /home/samba 
  valid users = @smbgrp 
  guest ok = no 
  writable = yes 
  browsable = yes
...
$ systemctl enable smb 
$ systemctl enable nmb 
$ systemctl start smb 
$ systemctl start nmb 
```

## - Mount on Linux client
```bash
$ yum -y install cifs-utils samba-client 
$ mkdir /mnt/samba 
$ mount -t cifs //[SERVER IP]/[SHARED FOLDER NAME] /mnt/samba -o username=[USERNAME],password=[PASSWORD]
```

## - Mount on Windows client
![Samba shared folder](/assets/img/samba_share.png)

[↩️](/Linux/example.html)
