
## Mount the USB drive

Run
```
sudo fdisk -l
```
 and you will get something like this
 ```
 Disk /dev/sdc: 7.4 GiB, 7948206080 bytes, 15523840 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     8192 15523839 15515648  7.4G  b W95 FAT32
```

Choose the device (in this case `/dev/sdc1` ) and make a directory for mounting this
```
sudo mkdir /media/usb-drive
sudo mount /dev/sdc1 /media/usb-drive/
```

## Copy the data
Now copy the data from the drive using `rsync`
```
sudo rsync -r --info=progress2 --info=name0 '/data_gathering/<folder to copy>'  '/media/usb/data_gathering/'
```

This will give us the progress bar and estimated time remaining.

## Unmount the drive 
Once that is complete we can unmount the drive.
```
sudo umount /media/usb-drive
```
