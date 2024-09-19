# System info
---
## - Show CPU info
```bash
$ cat /proc/cpuinfo
  processor       : 0
  vendor_id       : AuthenticAMD
  cpu family      : 23
  model           : 113
  model name      : AMD Ryzen 5 3600XT 6-Core Processor
  stepping        : 0
  microcode       : 0xffffffff
  cpu MHz         : 3792.890
  cache size      : 512 KB
...
```

## - Show disk usage
```bash
$ df -h
  File system          Dim. Usati Dispon. Uso% Montato su
  devtmpfs             4,0M     0    4,0M   0% /dev
  tmpfs                368M     0    368M   0% /dev/shm
  tmpfs                148M  4,4M    143M   3% /run
  /dev/mapper/cs-root   17G  4,6G     13G  28% /
  /dev/sda1            960M  455M    506M  48% /boot
  tmpfs                 74M   52K     74M   1% /run/user/42
  tmpfs                 74M   36K     74M   1% /run/user/1000
```

## - Show memory usage
```bash
$ free -h
                 total        used        free      shared  buff/cache   available
  Mem:           735Mi       567Mi        74Mi       1,0Mi       212Mi       167Mi
  Swap:          2,0Gi       161Mi       1,8Gi
```

## - Show routing table
```bash
$ netstat -r
  Kernel IP routing table
  Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
  default         _gateway        0.0.0.0         UG        0 0          0 ens33
  192.168.159.0   0.0.0.0         255.255.255.0   U         0 0          0 ens33
```

## - Show TCP internet connection
```bash
$ netstat -t
  Active Internet connections (w/o servers)
  Proto Recv-Q Send-Q Local Address           Foreign Address         State
  tcp        0     52 CentOSvm:ssh            192.168.159.1:52996     ESTABLISHED
  tcp        0      0 CentOSvm:ssh            192.168.159.1:62180     ESTABLISHED
  tcp        0      0 CentOSvm:ssh            192.168.159.1:64103     ESTABLISHED
```

## - Show UDP internet connection
```bash
$ netstat -u
  Active Internet connections (w/o servers)
  Proto Recv-Q Send-Q Local Address           Foreign Address         State
  udp        0      0 CentOSvm:bootpc         192.168.159.254:bootps  ESTABLISHED
```

[↩️](../Linux.html)
