# Prepare
### Identify existing users 🆔
```bash
$ getent passwd | cut -d: -f1 | sort
```
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

> [!NOTE]
> A prompt will be visualized if you try to create a user that already exists.

# Execute
### Create user 🪪
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

# Check
### User created with default settings 👌
```bash
$ id alessio
  uid=1001(alessio) gid=1001(alessio) groups=1001(alessio)
$ cat /etc/passwd | grep alessio
  alessio:x:1001:1001::/home/alessio:/bin/bash
```
> When a new user is created, it’s entry is automatically added to the "/etc/passwd" file.
> | alessio | x      | 1001 | 1001 |         | /home/alessio | /bin/bash |
> |---------|--------|------|------|---------|---------------|-----------|
> |Username |Password|UID   |GID   |User Info|Home Directory |Shell      |
> 
> Username: User login name used to login into system. It should be between 1 to 32 charcters long.
> Password: User password (or x character) stored in /etc/shadow file in encrypted format.
> User ID (UID): Every user must have a User ID (UID) User Identification Number. By default UID 0 is reserved for root user and UID’s ranging from 1-99 are reserved for other predefined accounts. Further
> UID’s ranging from 100-999 are reserved for system accounts and groups.
> Group ID (GID): The primary Group ID (GID) Group Identification Number stored in /etc/group file.
> User Info: This field is optional and allow you to define extra information about the user. For example, user full name. This field is filled by ‘finger’ command.
> Home Directory: The absolute location of user’s home directory.
> Shell: The absolute location of a user’s shell i.e. /bin/bash.

[↩️](../Linux.md)
