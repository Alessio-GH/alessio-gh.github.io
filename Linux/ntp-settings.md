# NTP settings

## - Check *chrony deamon* status
```bash
$ systemctl status chronyd
  ● chronyd.service - NTP client/server
       Loaded: loaded (/usr/lib/systemd/system/chronyd.service; enabled; preset: enabled)
       Active: active (running) since Mon 2024-09-09 16:05:22 CEST; 1 day 5h ago
         Docs: man:chronyd(8)
               man:chrony.conf(5)
      Process: 772 ExecStart=/usr/sbin/chronyd $OPTIONS (code=exited, status=0/SUCCESS)
     Main PID: 796 (chronyd)
        Tasks: 1 (limit: 4312)
       Memory: 1.3M
          CPU: 684ms
       CGroup: /system.slice/chronyd.service
               └─796 /usr/sbin/chronyd -F 2
```

## - Check NTP server list
```bash
$ chronyc sources
  MS Name/IP address         Stratum Poll Reach LastRx Last sample
  ===============================================================================
  ^* time.cloudflare.com           3   7   377    41  -2310us[-1370us] +/-   38ms
  ^- host93-133-14-31.serverd>     3   7   377    44    -24ms[  -23ms] +/-   71ms
  ^- kraken2.bilink.net            3   7   377   428    -18ms[  -17ms] +/-  106ms
  ^- 129.152.16.145                3   7    56   302    -29ms[  -28ms] +/-   93ms
```

## - Change NTP server list 
```bash
$ vi /etc/chrony.conf
  # Use public servers from the pool.ntp.org project.
  # Please consider joining the pool (https://www.pool.ntp.org/join.html).
  pool 2.centos.pool.ntp.org iburst
... 
```
> add/modify pool list adding new server names or IP

```bash
$ vi /etc/chrony.conf
  # Use public servers from the pool.ntp.org project.
  # Please consider joining the pool (https://www.pool.ntp.org/join.html).
  # pool 2.centos.pool.ntp.org iburst
  server pool.ntp.org iburst
  server 0.pool.ntp.org iburst
  server 1.pool.ntp.org iburst
  server <IP_address> iburst
...
```
> restart service using $ systemctl restart chronyd

[↩️](../Linux.html)
