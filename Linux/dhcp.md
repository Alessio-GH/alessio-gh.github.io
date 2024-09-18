# DHCP
---

## - Assign a static IP to DHCP server
```bash
$ nmtui
...
```
![nmtui](/assets/img/nmtui.png)

## - Install DHCP server service
```bash
$ yum install dhcp-server
...
  ========================================================================================================================
   Package                      Architecture            Version                             Repository               Size
  ========================================================================================================================
  Installing:
   dhcp-server                  x86_64                  12:4.4.2-19.b1.el9                  baseos                  1.2 M
  Installazione dipendenze:
   dhcp-common                  noarch                  12:4.4.2-19.b1.el9                  baseos                  129 k
  
  Riepilogo della transazione
  ========================================================================================================================
  Installati  2 pacchetti
  
  Dimensione totale dello scaricamento: 1.3 M
  Dimensione installata: 4.2 M
  Procedere [s/N]: s
  Scaricamento dei pacchetti:
  (1/2): dhcp-common-4.4.2-19.b1.el9.noarch.rpm                                           310 kB/s | 129 kB     00:00
  (2/2): dhcp-server-4.4.2-19.b1.el9.x86_64.rpm                                           1.0 MB/s | 1.2 MB     00:01
...
```

## - Config DHCP
```bash
$ vi /etc/dhcp/dhcpd.conf
...
  default-lease-time 600;
  max-lease-time 7200;
  authoritative;
  
  subnet 192.168.10.0 netmask 255.255.255.0 {
      range 192.168.10.100 192.168.10.200;
      option routers 192.168.10.1;
      option subnet-mask 255.255.255.0;
      option domain-name-server 8.8.8.8 8.8.4.4;
  }
```

## - Config *firewalld*
```bash
$ firewall-cmd --permanent --zone=public --add-port=67/udp --add-port=68/udp
  success
```

## - Start/Enable *dhcpd*
```bash
$ systemctl start dhcpd
$ systemctl enable dhcpd
```

[↩️](/Linux/example.html)
