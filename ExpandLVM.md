## Expand LVM with added storage:

1. First check for the added disks to make sure they are seen by the system:

    ```$lsblk```

    Output:
    sda,sdb, and sdc are the three hard drives I added to the system.

    ```
    NAME  MAJ:MIN RM  SIZE RO  TYPE MOUNTPOINTS
    sda     8:0    0  3.6T  0  disk
    sdb     8:16   0  3.6T  0  disk
    sdc     8:32   0  3.6T  0  disk
    ```
2. Create a physical volume.  We will use /dev/sda for this:

    ```$sudo pvcreat /dev/sda```

3. Identify the volume group:

    ```$sudo vgs```

    Output:

    ```
    VG             #PV #LV #SN Attr   VSize VFree
    rhel_desktop     2   3   0 wz--n- <4.55t   0
    ```

4.  Extend the volume group:

    ```
    $sudo vgextend rhel_desktop /dev/sda
    ```
    Check the volum group again:

    ```$sudo vgs```

5. Identify the logical volume you want to extend:

    ```$sudo lvs```

6. Extend the logical volume you want to add more space to:
     
    We will extend the /root lv:

    ```$sudo lvextend -l +100%FREE /dev/rhel_desktop/root```

7. Extend the filesystem:

    ```$sudo xfs_growfs /dev/rhel_desktop/root```

8. Verify the changes:

    ```$df -h```

    This should show the extended space of the root / FS.