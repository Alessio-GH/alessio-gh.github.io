# Prerequisites
## Identify the service your OS is using as Firewall;

```bash
$ rpm -qa | grep firewalld
  firewalld-filesystem-1.3.4-1.el9.noarch
  firewalld--1.3.4-1.el9.noarch

```
or

```bash
$ rpm -qa | grep iptables
  iptables-libs-1.8.10-4.el9.x86_64
  iptables-nft-1.8.10-4.el9.x86_64
```
and check their status:

```bash
$ systemctl status firewalld
● firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; preset: enabled)
   Active: active (running) since Fri 2024-09-06 20:21:19 CEST; 14min ago
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
   Loaded: loaded (/usr/lib/systemd/system/iptables.service; disabled; preset: disabled)
   Active: inactive (dead)
```
      
> [!WARNING]
> Only one of the two services has to be *active* and *enabled* eventually.
> Use **$ systemctl start firewalld** and **$ systemctl enable firewalld** for this purpose.

>## Stop and block the service you don't need.

```bash
$ systemctl stop firewalld
$ systemctl disable firewalld
  Removed "/etc/systemd/system/multi-user.target.wants/firewalld.service".
  Removed "/etc/systemd/system/dbus-org.fedoraproject.FirewallD1.service".
$ systemctl mask firewalld
  Created symlink /etc/systemd/system/firewalld.service → /dev/null.
```
or

```bash
$ systemctl stop iptables
$ systemctl disable iptables
$ systemctl mask iptables
```

> [!WARNING]
> Remember to restart firewall service.
> Use **$ systemctl restart firewalld** or **$ systemctl restart iptables** for this purpose.

## Check SSH firewall rule;

```bash
$ firewall-cmd --list-all
  public (active)
  target: default
  icmp-block-inversion: no
  interfaces: ens33
  sources:
  services: cockpit dhcpv6-client ssh
  ports:
  protocols:
  forward: yes
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```
or

```bash
$ iptables –L --line-numbers

```
and open port 22

```bash
$ firewall-cmd --permanent --zone=public --add-port=22/tcp
  success
```
or

```bash
$ iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```
