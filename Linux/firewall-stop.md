## Stop and disable the firewall service you don't need 🚫
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

[↩️ back to remote access guide ✈️](/Linux/remote-access.html)

[↩️ back to firewall guide 🔥🚪](/Linux/firewall.html)
