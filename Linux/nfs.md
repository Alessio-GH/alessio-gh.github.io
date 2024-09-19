# NFS
---
## - Config NFS server
```bash
$ yum install nfs-utils libnfsidmap rpcbind nfs-server rpc-statd nfs-idmapd
$ systemctl start rpcbind nfs-server rpc-statd nfs-idmapd
$ systemctl enable rpcbind nfs-server
$ mkdir /home/Public
$ chmod a+rwx /home/Public
$ vi /etc/exports 
...
  /home/Public 192.168.159.134(rw,sync,no_root_squash) # for only 1 client
  /home/Public *(rw,sync,no_root_squash) # for everyone
...
$ exportfs-rv # export NFS filesystem
```

## - Config NFS client
```bash
$ yum install nfs-utils rpcbind
$ systemctl rpcbind start
$ ps–ef | egrep “firewall|iptable” # make sure firewalld or iptables stopped (if running)
$ showmount-e 192.168.1.5 # IP server
$ mkdir /mnt/share # create mount directory 
$ mount 192.168.159.131:/home/Public /mnt/share
$ df –h
```

[↩️](../Linux.html)
