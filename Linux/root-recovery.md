# Root recovery
---
## - Press *shift* or *esc* during the boot process to enter the GRUB command line
![grub_boot](/assets/img/grub_boot.png)

## - Press *e* to edit GRUB
![grub_boot](/assets/img/grub_edit.png)
- remove *ro* (read-only) before crashkernel;
- replace *ro* with *rw init=/sysroot/bin/sh* before crashkernel	(on CentOS / Red Hat 9);
- add *rd.break* after *rhgb quiet* (on other distros);
- press [ctrl+x];
  
```bash
$ chroot /sysroot
$ passwd root
$ [enter new password]
$ touch /.autorelabel
$ exit
$ reboot
```

[↩️](../Linux.html)
