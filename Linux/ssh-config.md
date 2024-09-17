## Check SSH configuration file ⚙️
```bash
$ vi /etc/ssh/sshd_config
```
Look for the following settings and their values:
- **Port**: specifies the port number SSH listens on (default is `22`);
- **ListenAddress**: specifies IP addresses SSH listens on (default is `0.0.0.0`, which means all interfaces);
- **Protocol**: specifies the SSH protocol version (default is `2`);
- **HostKey**: specifies the location of the SSH host keys;
- **ClientAliveInterval**: specifies idle timeout interval after which you will be automatically logged out (600 seconds = 10 minutes);
- **ClientAliveCountMax**: specifies the number of chances the client has to respond before the server drops the connection;
- **PermitRootLogin**: specifies if root logins are allowed (default is `yes`);
- **PasswordAuthentication**: specifies if password authentication is allowed (default is `yes`).

> [!NOTE]
> Remember to restart the service after having made changes using $ systemctl restart sshd.
  
[↩️ back to remote access guide ✈️](/Linux/remote-access.html)

[↩️ back to hardening guide 🔐](/Linux/hardening.html)
