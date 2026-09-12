# Mounting and unmounting file systems
In linux, file system are hierarchical like an upside down tree where `/` is the main trunk of the tree. Under this, there are many childs. 

if user wants to acces a file system thats on another partition, the user needs to mount it or logically attach it to an existing directory on an existing file system which is called mount point. 

To mount or to attach a file system in the directory tree `mount` command is used. If run without any argument, it will diaplay all currently attached file systems. 

To display an specific type of file system `-t ext4` option is used. it will show ext4 file types.

## Mounting a file system
on ubuntu, Inserting an usb device automatically will mount it on /media directory.If its not mounted automatically then, To mount it manually Basic command : `sudo mount [device file name] [mount point path]`.Example command: `sudo mount /dev/sdb /home/student/desktop` To get the device file name, `lsblk, fdisk -l` commands can be used. 

A single physical device can be mounted on multiple places.

The mount command will auto-detect file system format. Some file system are automatically not recognized, in that case and needs to be explicitely specified. To specify `-t [type]` option is used. Example command: `mount -t vfat -l`

Some other important options, `-o`. This gives power to mount the files in specified mode. Example command: `mount -o ro /dev/sdb [mount point]`. This will mount the drive with read only mode.

The device can also remounted if mistakenly mounted with wrong permission with commands, `mount -o rw,remount /dev/sdb [mount point]`

If the device is already mounted somewhere in another mode then this command will fail. To mount it with this option, first the device needs to unmounted, only then thei will work.

## Unmounting a device.
Simply running `sudo umount [mount point]` will unmount a partition. But if any files on that partition is open it will not work. 

Alternativelavy lazy unmount can be used with including `-l` option. It will unmount the partition uwen the partition is not being used.

## Mounting As .iso file
To mount an iso file, `sudo mount /path/to/iso/file /home/studen/iso -o -loop`. If the iso file is mounted, it will act like a file system tree. 

## Disk partitioning
For graphically managing partition `gparted` command can be used. Installation ` sudo apt install gparted` ant then opening `sudo gparted`.

There is also a cli tool for partitioning called `fdisk`.



