# Disk

## Restore SD card image
```
diskutil list                         // show the SD card disk path
diskutil unmountDisk /dev/diskx       // unmount SD card
sudo newfs_msdos -F 16 /dev/diskx     // format SD card
sudo dd if={/path/of/image/xxx.dmg} of=/dev/diskx bs=1m   // restore image file to SD card
```

## Backup SD card image
```
diskutil list
sudo dd if=/dev/diskx of=~{/path/of/image/xxxx.dmg}
```

## Manage Partitions
https://elinux.org/RPi_Easy_SD_Card_Setup#Adding_a_data_partition_.28Optional.29

https://www.thegeekstuff.com/2011/09/parted-command-examples/

```
sudo su -
apt-get install parted
parted /dev/mmcblk0
unit chs
print
```
    BIOS cylinder,head,sector geometry: 60906,64,32.  Each cylinder is 1049kB.
    Number  Start    End         Type     File system  Flags
    1      4,0,0    259,63,31   primary  fat32        lba
    2      260,0,0  3838,63,31  primary  ext4

### Resize partition
```
resizepart 2
7676,63,31
```

### Add partition
```
mkpart primary 7677,0,0 60905,63,31
print
```
    Number  Start     End          Type     File system  Flags
    1      4,0,0     259,63,31    primary  fat32        lba
    2      260,0,0   7676,63,31   primary  ext4
    3      7677,0,0  60905,63,31  primary               lba
```
quit
mkfs.ext4 /dev/mmcblk0p3
e2label /dev/mmcblk0p3 data
sudo pico /etc/fstab
```
    # Add below line to end of /etc/fstab
    /dev/mmcblk0p3  /data           ext4    defaults        1       2
```
mkdir /data
mount /data
cd /data
ls