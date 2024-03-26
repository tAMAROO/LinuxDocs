
# System Installation:


### Note:

I did not have internet access before installing the dkms wifi packages.  I had to use a tethered usb connection since I have no ethernet port.  I had to use this to get the packages in pacstrap.
```

====================
Partition Creation ==
====================

cgdisk /dev/sda

Create four partitions:

|  Device Name  |      Type    |  Size  | Selection Code |  Name    |
| ------------- |--------------|--------|----------------|----------|
|   /dev/sda1   |      EFI     | 100MiB |      ef00      |  efi     |
|   /dev/sda2   |      Boot    | 250MiB |      8300      |  boot    |
|   /dev/sda3   |      SWAP    | 2GiB   |      8200      |  swap    |
|   /dev/sda4   |      Root    | 100%   |      8300      |  Arch(/) |


===========================
Format Created Partitions ==
===========================

mkfs.vfat -F32 /dev/sda1
mkfs.ext2 /dev/sda2
mkfs.ext4 /dev/sda4

============
Setup Swap ==
============

mkswap /dev/sda3
swapon /dev/sda3


==================
Mount Partitions ==
==================

mount /dev/sda4 /mnt
mkdir /mnt/boot
mount /dev/sda2 /mnt/boot
mkdir /mnt/boot/efi
mount /dev/sda1 /mnt/boot/efi


=====================
Install Arch System ==
=====================

pacstrap /mnt base base-devel grub-efi-x86_64 efibootmgr wpa_supplicant syslinux nano linux-zen linux-zen-headers linux-firmware mkinitcpio networkmanager network-manager-applet acpi acpi_call acpid lm_sensors intel-ucode


================
Generate fstab ==
================

genfstab -pU /mnt >> /mnt/etc/fstab


==================================
Chroot into the installed system ==
==================================

arch-chroot /mnt /bin/bash

====================
Change root password ==
====================

passwd

==============
Set Hostname ==
==============

echo #hostname > /etc/hostname


============
Set Locale ==
============

echo LANG=en_US.UTF-8 >> /etc/locale.conf
echo LANGUAGE=en_US >> /etc/locale.conf
echo LC_ALL=C >> /etc/locale.conf


===================
Locale generation ==
===================

Nano /etc/locale.gen
uncomment en_US.UTF-8
locale-gen


===============
Create a user ==
===============

useradd -m -g users -G wheel,storage,power -s /bin/bash USERNAME
passwd USERNAME

nano /etc/sudoers
Uncomment #%wheel ALL=(ALL) ALL


=========================
Regenerate initrd image ==
=========================

mkinitcpio -P


============
Grub Setup ==
============

grub-install
grub-mkconfig -o /boot/grub/grub.cfg


=================
Done.  Clean up ==
=================

exit
umount -R /mnt
reboot
```
