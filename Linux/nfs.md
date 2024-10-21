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
$ firewall-cmd --permanent --new-zone=nfs-clients # make sure firewalld isn't blocking NFS port
$ firewall-cmd --permanent --zone=nfs-clients --add-source=[SERVER IP] # add server IP to authorized NFS clients
$ showmount -e [SERVER IP] # check shared folder before mounting
$ mkdir /mnt/Public # create mount directory
$ mount [SERVER IP]:/home/Public /mnt/Public # mount NFS
$ df –h # verify mounting point
$ vi /etc/fstab # add following line to mount at system boot
...
  [SERVER IP]:/home/Public /mnt/Public    nfs    defaults    0 0
...
```

[↩️](../Linux.html)
