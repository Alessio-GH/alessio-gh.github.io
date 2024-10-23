# Firewall
---
## - [Identify the service your OS is using as firewall 🔥](firewall-identify.html)
> [!NOTE]
> Only one of *iptables* or *firewalld* has to be *active* and *enable*.
> 
> * Use **$ systemctl start iptables/firewalld** and **$ systemctl enable iptables/firewalld**.
> 
> * Then use **$ systemctl stop iptables/firewalld** and **$ systemctl mask iptables/firewalld** on the other.

## - [Stop and disable the service you don't need 🚫](firewall-stop.html)

## - [Create SSH firewall rule 🚪](firewall-create.html)

## - [Add new service 🆕](firewall-new.html)

## - Firewall GUI 📺
```bash
$ firewall-config
```

![Firewall GUI](/assets/img/firewall_config_GUI.png)

[↩️](../Linux.html)
