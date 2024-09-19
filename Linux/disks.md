# Disks
---
## - Create partition
```bash
$ fdisk /dev/sdb
$ n <new partition>
$ p <print partition table>
$ [Enter for first sector]
$ [Enter for last sector]
$ t <change a partition system ID>
$ L <type L to list all codes>
$ 8E <change partition type from Linux to Linux LVM>
$ w <write changes and quit>
```

## - Manage partition
```bash
$ pvcreate /dev/sdb1 <create physical volume (PV)>
$ pvdisplay <verify PV>
$ vgcreate test_vg /dev/sdb1 <create volume group (VG)>
$ vgdisplay test_vg <verify VG>
$ lvcreate –n test_lv –size 1.5G test_vg <create logical volume (LV)>
$ lvdisplay <verify LV>
$ mkfs.xfs /dev/test_vg/test_lv <format LV>
```

## - Mount partition
```bash
$ mkdir /test <create a new directory> 
$ mount /dev/test_vg/test_lv /test <mount the new file system> 
$ df –h
```

[↩️](../Linux.html)
