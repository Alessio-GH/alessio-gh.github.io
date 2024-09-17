# Firewall
---
## - [Identify the service your OS is using as firewall 🔥](firewall-identify.html)
> [!NOTE]
> Only one of the two services has to be *active* and *enabled* eventually.
> Use **$ systemctl start firewalld** and **$ systemctl enable firewalld** for this purpose.

## - [Stop and disable the service you don't need 🚫](firewall-stop.html)
> [!WARNING]
> Remember to restart firewall service using **$ systemctl restart firewalld** or **$ systemctl restart iptables**.

## - [Check/Create SSH firewall rule 🚪](firewall-state.html)

## - [Add new service 🆕](firewall-new.html)

## - Firewall GUI 📺
```bash
$ firewall-config
```

![Firewall GUI](/assets/img/firewall_config_GUI.png)

[↩️](../Linux.html)
