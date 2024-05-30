### Issue:
When trying to install RedHat 9.4 onto my worstation I ran into a problem where the installer(Anaconda) would not see the NVME SSD drive.

### Fix:
From research I found that the drive must be set to AHCI mode instead of RAID mode which windows will set a drive to.  This is the steps I took to resolve.

 1. Boot computer into BIOS.
 2. Find option labeled "Sata Operation", could be different per manufacturer.
 3. Select AHCI mode.
 4. Reboot.



### Research assets:

>You've got a single SSD set up in RAID mode, and the Ubuntu installer won't recognize your SSD until you switch your disk setting in the BIOS from RAID to AHCI.
>Making that switch comes with some problems though, as Windows will no longer boot.
>You don't need to reinstall Windows...
>Below, you'll find two different ways to solve this problem. Some users found Choice #2 to be easier.

URL: https://askubuntu.com/questions/1127505/ssd-not-detected-during-ubuntu-installation#:%7E:text=Restart%20the%20computer%20and%20enter,automatically%20boot%20to%20Safe%20Mode.
