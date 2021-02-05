# Setup RPi System (using Mac)
## 1. Determine SD device
Insert the SD card in the slot or connect the SD card reader with the SD card inside.

```sh
$ diskutil list
/dev/disk0 (internal):
    #:                       TYPE NAME                    SIZE       IDENTIFIER
    0:                       GUID_partition_scheme        500.3 GB   disk0
    1:                       EFI EFI                      314.6 MB   disk0s1
    2:                       Apple_APFS Container disk1   500.0 GB   disk0s2

/dev/disk1 (synthesized):
    #:                       TYPE NAME                    SIZE       IDENTIFIER
    0:                       APFS Container Scheme -      +500.0 GB   disk1
                             Physical Store disk0s2
    1:                       APFS Volume Macintosh HD     89.6 GB    disk1s1
    2:                       APFS Volume Preboot          47.3 MB    disk1s2
    3:                       APFS Volume Recovery         510.4 MB   disk1s3
    4:                       APFS Volume VM               3.6 GB     disk1s4

/dev/disk2 (external, physical):
    #:                       TYPE NAME                    SIZE       IDENTIFIER
    0:                       FDisk_partition_scheme       *15.9 GB    disk2
    1:                       Windows_FAT_32 boot          268.4 MB   disk2s1
    2:                       Linux     
```

the SD card is /dev/disk2 - your disk and partition list may vary

## 2. Erase SD card (if necessary)
The basic syntax for erasing a disk from the command line in macOS is as follows:

`diskutil eraseDisk FILE_SYSTEM DISK_NAME DISK_IDENTIFIER`

Erase the disk file system to `FAT32`

## 3. Copy the image
> Note: The use of the dd tool can overwrite any partition of your machine. If you specify the wrong device in the instructions, you could overwrite your primary Mac OS partition!

### 3.1 Unmount Disk
The disk must be unmounted before copying the image

`diskutil unmountDisk DISK_IDENTIFIER`

### 3.2 Copy the image

`sudo dd bs=1m if=path_of_your_image.img of=DISK_IDENTIFIER; sync`

> Note: the rdisk ('raw disk') instead of disk, this speeds up the copying.
> This can take more than 15 minutes, depending on the image file size. Check the progress by pressing Ctrl+T.

  If the command reports dd: /dev/rdiskN: Resource busy, you need to unmount the volume first sudo diskutil unmountDisk /dev/diskN.

  If the command reports dd: bs: illegal numeric value, change the block size bs=1m to bs=1M.

  If the command reports dd: /dev/rdiskN: Operation not permitted, go to System Preferences -> Security & Privacy -> Privacy -> Files and Folders -> Give Removable Volumes access to Terminal.

  If the command reports dd: /dev/rdiskN: Permission denied, the partition table of the SD card is being protected against being overwritten by Mac OS. Erase the SD card's partition table using this command:

  sudo diskutil partitionDisk /dev/diskN 1 MBR "Free Space" "%noformat%" 100%

  That command will also set the permissions on the device to allow writing. Now issue the dd command again.

Eject

After the dd command finishes, eject the card:

sudo diskutil eject /dev/rdiskN




For the official Raspberry Pi OS, if you need to manually log in, the default user name is `pi`, with password `raspberry`. Remember the default keyboard layout is set to UK.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk1MjM3NTMzNl19
-->