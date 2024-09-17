## Add new service
To add a service that is not pre-defined by firewalld, create a [service].xml in /usr/lib/firewalld/services/ directory
```bash
$ cd /usr/lib/firewalld/services
$ vi [service].xml
  <?xml version="1.0" encoding="utf-8"?>
  <service>
    <short>[service name]</short>
    <description>[service description]</description>
    <port protocol="[protocol name]" port="[port number]"/>
  </service>
```
... and add a firewall rule to enable it

```bash
$ firewall-cmd --zone=public --add-service=[service] --permanent
  success
$ systemctl restart firewalld
```

[↩️](/Linux/firewall.html)
