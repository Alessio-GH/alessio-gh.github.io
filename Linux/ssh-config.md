## Check SSH configuration file ⚙️
```bash
$ vi /etc/ssh/sshd_config
```
Look for the following settings and their values:
- **Port**: Specifies the port number that SSH listens on (default is `22`).
- **ListenAddress**: Specifies the IP addresses that SSH listens on (default is `0.0.0.0`, which means all interfaces).
- **Protocol**: Specifies the SSH protocol version (default is `2`).
- **HostKey**: Specifies the location of the SSH host keys.
- **PermitRootLogin**: Specifies whether root logins are allowed (default is `yes`).
- **PasswordAuthentication**: Specifies whether password authentication is allowed (default is `yes`).
  
[↩️ back to remote access guide ✈️](/Linux/remote-access.html)

[↩️ back to hardening guide 🔐](/Linux/hardening.html)
