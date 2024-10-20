# Remote access prerequisites
---

## - [Identify the service your OS is using as firewall 🔥](firewall-identify.html)

> [!NOTE]
> Only one of the two services has to be *active* and *enabled* eventually.
> Use **$ systemctl start firewalld** and **$ systemctl enable firewalld** for this purpose.

## - [Stop and disable the firewall service you don't need 🚫](firewall-stop.html)

> [!WARNING]
> Remember to restart firewall service using **$ systemctl restart firewalld** or **$ systemctl restart iptables**.

## - [Check/Create SSH firewall rule 🚪](firewall-state.html)

> [!TIP]
> Try to connect remotely before changing firewall rules.

## - [Check SSH configuration file ⚙️](ssh-config.html)

> [!WARNING]
> If you change file configuration, remember to restart SSH service using **$ systemctl restart sshd**.

# Execute SSH command
---

```bash
$ ssh -l [USER] 192.168.159.131
  [USER]@192.168.159.131's password:
  Last login: Sat Sep  7 18:44:07 2024
```

## - [Set SSH key to access without password 🛂](ssh-key.html)

> [!WARNING]
> If you change file configuration, remember to restart SSH service using **$ systemctl restart sshd**.

[↩️](../Linux.html)
