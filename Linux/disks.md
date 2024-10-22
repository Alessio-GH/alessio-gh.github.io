# Disks
---
## - Create partitions
```bash
$ fdisk /dev/sdb
$ n # new partition
$ p # print partition table
$ [specify first sector]
$ [specify last sector]
$ t # change the partition system ID
$ L # list all codes
$ 8E # change partition type from Linux to Linux LVM
$ w # write changes and quit
```

## - Create logical volumes (LV)
```bash
$ pvcreate /dev/sdb1 # create physical volume (PV)
$ pvdisplay # verify PV
$ vgcreate test_vg /dev/sdb1 # create volume group (VG)
$ vgdisplay test_vg # verify VG
$ lvcreate –n test_lv –size 1.5G test_vg # create logical volume (LV)
$ lvdisplay # verify LV
$ mkfs -t xfs /dev/test_vg/test_lv # format LV
```

## - Format partitions
```bash
$ mkfs -t [FYLE SYSTEM TIPE] [PARTITION PATH]
```

## - Mount partitions
```bash
$ mkdir /mnt/test # create a new directory
$ mount /dev/test_vg/test_lv /mnt/test # mount the new file system
$ df –h
```

## - Mount partitions on system boot
```bash
$ vi /etc/fstab
...
  # Created by anaconda on Mon Aug 26 09:19:21 2024
  #
  # Accessible filesystems, by reference, are maintained under '/dev/disk/'.
  # See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info.
  #
  # After editing this file, run 'systemctl daemon-reload' to update systemd
  # units generated from this file.
  #
  /dev/mapper/cs-root     /                       xfs     defaults        0 0
  /dev/mapper/cs-swap     none                    swap    defaults        0 0
  /dev/test_vg/test_lv    /mnt/test               xfs     defaults        0 0
...
```

[↩️](../Linux.html)
