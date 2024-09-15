## Keep your OS up to date (CentOS)

### - Check current Kernel version
```bash
$ uname -msr
  Linux 5.14.0-505.el9.x86_64 x86_64
```

### - Check current OS version
```bash
$ cat /etc/os-release
  NAME="CentOS Stream"
  VERSION="9"
  ID="centos"
  ID_LIKE="rhel fedora"
  VERSION_ID="9"
  PLATFORM_ID="platform:el9"
  PRETTY_NAME="CentOS Stream 9"
...
```

### - Update packages
```bash
$ sudo yum -y update
...
```

### - Add third-party repository ElRepo
Check last repository on *www.elrepo.org*
```bash
$ rpm -Uvh https://www.elrepo.org/elrepo-release-9.el9.elrepo.noarch.rpm
  Ripristino di https://www.elrepo.org/elrepo-release-9.el9.elrepo.noarch.rpm
  Verifying...                          ################################# [100%]
  Preparazione in corso...              ################################# [100%]
  Aggiornamento / installazinone...
     1:elrepo-release-9.1-1.el9.elrepo  ################################# [100%]
```

### - Install last mainline kernel
```bash
$ yum --enablerepo=elrepo-kernel install kernel-ml
  Aggiornamento repository di Subscription Management.
  Impossibile leggere l'identità dell'utente
  
  This system is not registered with an entitlement server. You can use "rhc" or "subscription-manager" to register.
  
  ELRepo.org Community Enterprise Linux Repository - el9                                  192 kB/s | 265 kB     00:01
  ELRepo.org Community Enterprise Linux Kernel Repository - el9                           1.2 MB/s | 3.1 MB     00:02
  Dipendenze risolte.
  ========================================================================================================================
   Package                        Architecture        Version                            Repository                  Size
  ========================================================================================================================
  Installing:
   kernel-ml                      x86_64              6.10.10-1.el9.elrepo               elrepo-kernel               49 k
  Installazione dipendenze:
   kernel-ml-core                 x86_64              6.10.10-1.el9.elrepo               elrepo-kernel               53 M
   kernel-ml-modules              x86_64              6.10.10-1.el9.elrepo               elrepo-kernel               50 M
...
```
>[!NOTE]
> ... or install last long-term support release using $ yum --enablerepo=elrepo-kernel install kernel-lt

### - Set new kernel as default and upgrade grub configuration
```bash
$ reboot
$ vi /etc/default/grub
...
  GRUB_DEFAULT=0
...
$ grub2-mkconfig -o /boot/grub2/grub.cfg
$ reboot
```

[↩️](/Linux/hardening.html)
