## Set SSH key to access without password 🛂

```bash
$ ssh-keygen -t ed25519 -C "[USER] default" # generate public and private key in ~/.ssh/ directory
$ ssh-copy-id -i ~/.ssh/id_ed25519.pub [IP ADDRESS] # copy the public key to remote server in ~/.ssh/authorized_keys file
$ ssh -l [USER] [IP ADDRESS] # e.g. ssh -l root 192.168.159.35
```

> now you can disable remote password authentication

```bash
$ vi /etc/ssh/sshd_config
...
PasswordAuthentication no
...
$ systemctl restart ssh
```
  
[↩️](/Linux/remote-access.html)
