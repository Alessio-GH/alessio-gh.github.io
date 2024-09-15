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
  ANSI_COLOR="0;31"
  LOGO="fedora-logo-icon"
  CPE_NAME="cpe:/o:centos:centos:9"
  HOME_URL="https://centos.org/"
  BUG_REPORT_URL="https://issues.redhat.com/"
  REDHAT_SUPPORT_PRODUCT="Red Hat Enterprise Linux 9"
  REDHAT_SUPPORT_PRODUCT_VERSION="CentOS Stream"
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
  
  Riepilogo della transazione
  ========================================================================================================================
  Installati  3 pacchetti
  
  Dimensione totale dello scaricamento: 103 M
  Dimensione installata: 149 M
  Procedere [s/N]: s
  Scaricamento dei pacchetti:
  (1/3): kernel-ml-6.10.10-1.el9.elrepo.x86_64.rpm                                        100 kB/s |  49 kB     00:00
  (2/3): kernel-ml-core-6.10.10-1.el9.elrepo.x86_64.rpm                                   1.3 MB/s |  53 MB     00:41
  (3/3): kernel-ml-modules-6.10.10-1.el9.elrepo.x86_64.rpm                                1.0 MB/s |  50 MB     00:48
  ------------------------------------------------------------------------------------------------------------------------
  Totale                                                                                  2.1 MB/s | 103 MB     00:48
  Esecuzione del controllo di transazione
  Controllo di transazione eseguito con successo.
  Test di transazione in corso
  Test di transazione eseguito con successo
  Transazione in corso
    Preparazione in corso        :                                                                                    1/1
    Installing                   : kernel-ml-core-6.10.10-1.el9.elrepo.x86_64                                         1/3
    Esecuzione scriptlet in corso: kernel-ml-core-6.10.10-1.el9.elrepo.x86_64                                         1/3
    Installing                   : kernel-ml-modules-6.10.10-1.el9.elrepo.x86_64                                      2/3
    Esecuzione scriptlet in corso: kernel-ml-modules-6.10.10-1.el9.elrepo.x86_64                                      2/3
    Installing                   : kernel-ml-6.10.10-1.el9.elrepo.x86_64                                              3/3
    Esecuzione scriptlet in corso: kernel-ml-core-6.10.10-1.el9.elrepo.x86_64                                         3/3
  
  
  
    Esecuzione scriptlet in corso: kernel-ml-6.10.10-1.el9.elrepo.x86_64                                              3/3
    Verifica in corso            : kernel-ml-6.10.10-1.el9.elrepo.x86_64                                              1/3
    Verifica in corso            : kernel-ml-core-6.10.10-1.el9.elrepo.x86_64                                         2/3
    Verifica in corso            : kernel-ml-modules-6.10.10-1.el9.elrepo.x86_64                                      3/3
  Prodotti installati aggiornati.
  
  Installati:
    kernel-ml-6.10.10-1.el9.elrepo.x86_64                        kernel-ml-core-6.10.10-1.el9.elrepo.x86_64
    kernel-ml-modules-6.10.10-1.el9.elrepo.x86_64
  
  Fatto!
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
