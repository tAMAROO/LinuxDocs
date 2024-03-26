# System Installation:

### Note:

I did not have internet access before installing the dkms wifi packages.  I had to use a tethered usb connection since I have no ethernet port.  I had to use this to get the packages in pacstrap.

Partition Creation -
----

+ Run
```cgdisk /dev/sda```

+ Create four partitions:

| Device Name   | Type           | Size   | Selection Code | Name  |
| ------------- |:-------------:| -------:|:--------------:|:-----:|
| /dev/sda1     | EFI            | 100MiB |  ef00          | efi   |
| /dev/sda2     | Boot           | 250MiB |   8300         | boot  |
| /dev/sda3     | SWAP           | 2GiB   |  8200          |swap   |
| /dev/sda4     | Root           | 100%   |   8300         |Arch(/)|


##### *There are different ways of setting up a swap and this way is only one of them by partition.  I am using this because it works for me.  See [Swap - Arch Wiki](https://wiki.archlinux.org/title/Swap#Swap_file)

----
Format Created Partitions -
----

+ Run
```
mkfs.vfat -F32 /dev/sda1
mkfs.ext2 /dev/sda2
makf.ext4 /dev/sda4
```

----
Setup Swap -
----

+ Run
```
mkswap /dev/sda3
swapon /dev/sda3
```

----
Mount Partitions -
----

+ Run
```
mount /dev/sda4 /mnt
mkdir /mnt/boot
mount /dev/sda2 /mnt/boot
mkdir /mnt/boot/efi
mount /dev/sda1 /mnt/boot/efi
```

----
Install Arch System -
----

+ Run
```
pacstrap /mnt base base-devel grub-efi-x86_64 efibootmgr wpa_supplicant syslinux nano linux-zen linux-zen-headers linux-firmware mkinitcpio networkmanager network-manager-applet acpi acpi_call acpid lm_sensors intel-ucode
```
##### *Note: I am using the linux zen kernel.  There are four officially supported kernels for Arch. see [Kernel - Arch Wiki](https://wiki.archlinux.org/title/kernel#Officially_supported_kernels)

##### *Note: Also during this first install make sure to install some sort of command line text editor of your flavor(nano, vim, emacs) as one is not installed when you need it.

----
Generate fstab -
----

+ Run
```
genfstab -pU /mnt >> /mnt/etc/fstab
```

----
Chroot into the installed system -
----

+ Run
```
arch-chroot /mnt /bin bash
```

##### *Note:  You can also use chroot after system installation to troubleshoot and fix issues that may arise.  If needed follow below:
```
1. Use installation media as you would install a new system.
2. Mount your root directory in this case it would be /dev/sda4
   mount /dev/sda4 /mnt
3. At command prompt run arch-chroot /mnt
4. From here you can browse your files and edit and make changes as needed.
```
##### You can read more about chroot at [Chroot - Arch Wiki](https://wiki.archlinux.org/title/Chroot)

----
Change root password -
----

+ Run
```
passwd
```

----
Set Hostname -
----

+ Run
```
echo #hostname > /etc/hostname
```

----
Set Locale -
----

+ Run
```
echo LANG=en_US.UTF-8 >> /etc/locale.conf
echo LANGUAGE =en_US >> /etc/locale.conf
echo LC_ALL=C >> /etc/locale.conf
```

----
Locale generation -
----

+ Run
```Nano /etc/locale.gen```
+ In editor uncomment en_US.UTF-8
+ Run
```locale-gen```


----
Create a user -
----

+ Run
```
useradd -m -g users -G wheel,storage,power -s /bin/bash USERNAME
```
+ Run
```
passwd USERNAME
```
+Make user a sudoer. Run
```
nano /etc/sudoers
Uncomment #%wheel ALL=(ALL) ALL
```


----
Regenerate initrd image -
----

+ Run
```
mkinitcpio -P
```

----
Grub Setup -
----

+ Run
```
grub-install
grub-mkconfig -o /boot/grub/grub.cfg
```

##### Note:  If any changes are made to grub you will always need to run ```grub-mkconfig -o /boot/grub/grub.cfg```


----
Done.  Clean up -
----

+ Run
```
exit
umount -R /mnt
reboot
```
