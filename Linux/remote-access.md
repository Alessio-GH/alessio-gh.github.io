# Prerequisites
1. Identify the service your OS is using as **Firewall** with the following commands:
  ```bash
  $ rpm -qa | grep iptables
  `iptables`-libs-1.8.10-4.el9.x86_64
  `iptables`-nft-1.8.10-4.el9.x86_64
  ```
  or
  ```bash
  $ rpm -qa | grep firewalld
  `firewalld`-filesystem-1.3.4-1.el9.noarch
  `firewalld`--1.3.4-1.el9.noarch
  ```
  > [!WARNING]
  > Only one of the two service has to be *active* and *enabled* eventually.
  ```bash
  $ systemctl status firewalld
  ● firewalld.service - firewalld - dynamic firewall daemon
       Loaded: loaded (/usr/lib/systemd/system/firewalld.service; `enabled`; preset: `enabled`)
       Active: `active (running)` since Fri 2024-09-06 20:21:19 CEST; 14min ago
         Docs: man:firewalld(1)
     Main PID: 846 (firewalld)
        Tasks: 2 (limit: 4299)
       Memory: 2.5M
          CPU: 608ms
       CGroup: /system.slice/firewalld.service
               └─846 /usr/bin/python3 -s /usr/sbin/firewalld --nofork --nopid
  ```
  or
  ```bash
  $ systemctl status iptables
  ○ iptables.service - IPv4 firewall with iptables
       Loaded: loaded (/usr/lib/systemd/system/iptables.service; `disabled`; preset: `disabled`)
       Active: inactive (dead)
  ```
2. 
