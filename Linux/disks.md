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

## - Create physical volumes (PV)
```bash
$ pvcreate /dev/sdb # create physical volume (PV)
$ pvcreate /dev/sdc # create another physical volume (PV)
$ pvdisplay # check PVs
```

## - Create volume groups (VG)
```bash
$ vgcreate vg1 /dev/sdb /dev/sdc # create a single volume group (VG) out of two PVs
$ vgdisplay # check VG
```

## - Create logical volumes (LV)
```bash
$ lvcreate –n lv1 –L 5G vg1 # create logical volume (LV)
$ lvdisplay # check LV
$ mkfs -t xfs /dev/vg1/lv1 # format LV
```

## - Format partitions
```bash
$ mkfs -t [FILE SYSTEM TYPE] [PARTITION PATH]
```

## - Mount partitions
```bash
$ mkdir /mnt/test # create a new directory
$ mount /dev/vg1/lv1 /mnt/test # mount the new file system
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
  /dev/vg1/lv1            /mnt/test               xfs     defaults        0 0
...
```

## - Extend partitions
```bash
$ pvcreate /dev/sdb # create PV
$ vgdisplay # identify VG to extend
$ vgextend /dev/cs /dev/sdb # extend VG
$ lvdisplat # identify LV to extend
$ lvresize -L +5G /dev/cs/root
$ resize2fs /dev/cs/root
```

[↩️](../Linux.html)
