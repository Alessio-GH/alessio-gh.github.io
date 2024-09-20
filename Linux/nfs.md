# NFS
---
## - Config NFS server
```bash
$ yum install nfs-utils libnfsidmap rpcbind nfs-server rpc-statd nfs-idmapd
$ systemctl start rpcbind nfs-server rpc-statd nfs-idmapd
$ systemctl enable rpcbind nfs-server
$ mkdir /home/Public # shared directory
$ chmod a+rwx /home/Public # shared permissions
$ vi /etc/exports 
...
  /home/Public 192.168.159.134(rw,sync,no_root_squash) # for only 1 client
  /home/Public *(rw,sync,no_root_squash) # for everyone
...
$ exportfs -rv # export NFS filesystem
```

## - Config NFS client
```bash
$ yum install nfs-utils rpcbind
$ systemctl rpcbind start
$ systemctl status firewalld # make sure firewalld is stopped (if enabled)
$ systemctl status iptables # make sure iptables is stopped (if enabled)
$ showmount -e 192.168.59.131 # server IP
$ mkdir /mnt/share # create mount directory 
$ mount 192.168.159.131:/home/Public /mnt/share
$ df –h
```

[↩️](../Linux.html)