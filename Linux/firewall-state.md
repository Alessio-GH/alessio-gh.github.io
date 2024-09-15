## Check/Create SSH firewall rule 🚪

### List firewall rules
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
  Chain INPUT (policy ACCEPT)
  num  target     prot opt source               destination
  1    ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
  2    ACCEPT     icmp --  anywhere             anywhere
  3    ACCEPT     all  --  anywhere             anywhere
  4    ACCEPT     tcp  --  anywhere             anywhere             state NEW tcp dpt:ssh
  5    REJECT     all  --  anywhere             anywhere             reject-with icmp-host-prohibited
  6    ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
  
  Chain FORWARD (policy ACCEPT)
  num  target     prot opt source               destination
  1    REJECT     all  --  anywhere             anywhere             reject-with icmp-host-prohibited
  
  Chain OUTPUT (policy ACCEPT)
  num  target     prot opt source               destination
```

### Open port 22 for SSH

```bash
$ firewall-cmd --permanent --zone=public --add-port=22/tcp
  success
```
or

```bash
$ iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

[↩️ back to remote access guide ✈️](/Linux/remote-access.html)

[↩️ back to firewall guide 🔥🚪](/Linux/firewall.html)
