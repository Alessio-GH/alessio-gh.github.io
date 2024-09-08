# Prerequisites

## 1. [Identify the service your OS is using as firewall 🔥](firewall-identify.md)
> [!NOTE]
> Only one of the two services has to be *active* and *enabled* eventually.
> Use **$ systemctl start firewalld** and **$ systemctl enable firewalld** for this purpose.

## 2. [Stop and disable the service you don't need 🚫](firewall-stop.md)
> [!WARNING]
> Remember to restart firewall service using **$ systemctl restart firewalld** or **$ systemctl restart iptables**.

## 3. [Check/Create SSH firewall rule 🚪](firewall-state.md)
> [!TIP]
> Try to connect remotely before changing firewall rules.

## 4. [Check SSH configuration file ℹ️](ssh-config.md)
> [!WARNING]
> If you change file configuration, remember to restart SSH service using **$ systemctl restart ssh** or **$ systemctl restart ssh**.

# Execute
```bash
$ shh -l mele 192.168.159.131
  mele@192.168.159.131's password:
  Last login: Sat Sep  7 18:44:07 2024
```
[↩️](../Linux.md)
