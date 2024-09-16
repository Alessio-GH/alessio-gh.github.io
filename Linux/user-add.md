# Add new user
---
## Identify existing users 🆔
```bash
$ getent passwd | cut -d: -f1 | sort
```
> [!NOTE]
> A prompt will be visualized if you try to create a user that already exists.

<details>
<summary>output</summary>
  adm
  avahi
  bin
  chrony
  clevis
  cockpit-wsinstance
  colord
  daemon
  dbus
  dnsmasq
  flatpak
  ftp
  games
  gdm
  geoclue
  gnome-initial-setup
  halt
  libstoragemgmt
  lp
  mail
  mailnull
  mele
  nobody
  operator
  pipewire
  polkitd
  root
  rtkit
  saslauth
  setroubleshoot
  shutdown
  smmsp
  sshd
  sssd
  sync
  systemd-coredump
  tcpdump
  tss
</details>

---
## Create user 🪪
```bash
$ useradd alessio
  passwd alessio
  Cambio password per l'utente alessio.
  Nuova password:
  Password scadente: La password non supera il controllo del dizionario - Si basa su un termine di dizionario
  Reimmettere la nuova password:
  passwd: tutti token di autenticazione sono stati aggiornati con successo.
```
> [!WARNING]
> A prompt will be visualized if you choose a password that doesn't satisfy security checks.

---
## Check user configs 👌
```bash
$ id alessio
  uid=1001(alessio) gid=1001(alessio) groups=1001(alessio)
$ cat /etc/passwd | grep alessio
  alessio:x:1001:1001::/home/alessio:/bin/bash
```
| alessio  |     x    |  1001 |  1001 |           | /home/alessio  | /bin/bash  |
| -------- | -------- | ----- | ----- | --------- | -------------- | ---------- |
| Username | Password | UID   | GID   | User Info | Home Directory | Shell      |

> [!NOTE]
> When a new user is created, it’s entry is automatically added to the "/etc/passwd" file.

> [!TIP]
> If you want to delete users you can just use *userdel* command.

[↩️](../Linux.html)
