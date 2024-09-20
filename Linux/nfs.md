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
  /home/Public [CLIENT IP](rw,sync,no_root_squash) # for only 1 client
  /home/Public *(rw,sync,no_root_squash) # for every client
...
$ exportfs -rv # export NFS filesystem
```

## - Config NFS client
```bash
$ yum install nfs-utils rpcbind
$ systemctl rpcbind start
$ systemctl status firewalld # make sure firewalld is stopped (if enabled)
$ systemctl status iptables # make sure iptables is stopped (if enabled)
$ showmount -e [SERVER IP]
$ mkdir /mnt/share # create mount directory 
$ mount [SERVER IP]:/home/Public /mnt/share
$ df –h
```

[↩️](../Linux.html)
