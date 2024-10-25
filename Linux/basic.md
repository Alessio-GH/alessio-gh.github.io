# Commands
---

| Command | Role |
| - | - |
| **$ uname -a** | linux kernel and hostname |
| **$ id** | user ID (UID) and group ID (GID) |
| **$ pwd** | absolute path name of the current working directory |
| **$ rsync -azuv [ORIGIN] [DESTINATION]** | backup folders |
| **$ rsync -azuve ssh [ORIGIN] [USER]@[IP]:[DESTINATION]** | tranfer files |
| **$ rsync -azuve ssh [USER]@[IP]:[DESTINATION] [ORIGIN]** | retrieve files |
| **$ tar -xf [.tar FILE]** | extract .tar file |
| **$ tar -xzf [.tar.gz FILE]** | extract .tar.gz file |
| **$ tar -xjf [.tar.bz2 FILE]** | extract .tar.bz2 file |
| **$ tar -xJf [.tar.xz FILE]** | extract .tar.xz file |

# Directories
---

| Path | Role |
| ---- | ---- |
| **/etc/anacrontab** | set automatic tasks on workstations |
| **/etc/fstab** | mount partitions on boot |
| **/etc/sudoers** | permissions of users to execute commands with superuser privileges |
| **/etc/ssh/sshd_config** | configuration file for the Secure Shell (SSH) |
| **/dev/null** | black hole |
| **/usr/local/bin** | $PATH env variable usefull for containing scripts |
| **/var/log** | log files directory |

[↩️](../Linux.html)
