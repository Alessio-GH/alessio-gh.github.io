# Prerequisites

## 1. [Identify the service your OS is using as Firewall 🔥](firewall-identify.md)
> [!NOTE]
> Only one of the two services has to be *active* and *enabled* eventually.
> Use **$ systemctl start firewalld** and **$ systemctl enable firewalld** for this purpose.

## 2. [Stop and disable the service you don't need 🚫](firewall-stop.md)
> [!WARNING]
> Remember to restart firewall service using **$ systemctl restart firewalld** or **$ systemctl restart iptables**.

## 3. [Check/Create SSH firewall rule 🚪](firewall-state.md)
> [!TIP]
> Try to connect remotely before changing firewall rules.
