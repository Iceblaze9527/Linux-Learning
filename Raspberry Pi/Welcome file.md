# Setup RPi System
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

## 2. Erase the SD card (if necessary)
The basic syntax for erasing a disk from the command line in macOS is as follows:

`diskutil eraseDisk FILE_SYSTEM DISK_NAME DISK_IDENTIFIER`

Erase the disk file system to 

For the official Raspberry Pi OS, if you need to manually log in, the default user name is `pi`, with password `raspberry`. Remember the default keyboard layout is set to UK.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM5Nzc3MzI0Nl19
-->