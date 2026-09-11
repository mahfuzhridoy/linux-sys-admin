# Working with device files
Hard disks are represented in linux as special device. `dd` command can be used to read and write from special device files. dd can work directly with these device files and is used for task like backing up boot sector of a hard-drive, cloning a disk or a partition on another one, or creating a bootable usb stick.

> Note: dd has capability of erasing or destrying all the data from the disk. 

#


> ⚠️ Caution: The dd command will overwrite the existing contents of the destination drive, And if accidentally reversed the source and destination, it will overwrite the desired source file with contents of the destination file.

#

Simple command: `dd if=/etc/shadow of=/home/student/backup.img status=progress`. Here `if` stands for input file, `of` stands for output file, status shows the progress. The dd command copies the partition block by block so the copy contains:

- fiesystems
- files and directories
- permission and metadata
- free space structure
- file system uuid
- deleted but not yet overwritten data
- boot/filesystem structures contained within the partition

If the partition has free space, the dd command will also copy the available free space too.

> Note: .img files holds the exact copy of the other file.

Restoring the image file works simply by providing the image file as input and desired location where to restore as output. Example: `dd if=backup.img of=/etc/shadow status=progress`

#

With the dd command, it is possible to copy entire hard-disk to another place but the capacity of destination drive must be atleast the same size of source file.

## backup and restore master boot record
Sometimes it may need to backup the master boot record in case of something bad happens. mbr is a special type of boot sector at the very beginning of the disk. It holds the information on how the logical partition containing file systems are organized in that medium.

It also contains executable code which is usually referred to as a bootloader. The mbr represents the first section of disk with the block size of 512 bits. Example command for backingup:

```
dd if=/dev/sda of=/root/mbr.dat bs=512 count=1
```
This command will backup the partition of /dev/sda with the block size of 512 bytes specified by bs=512 option. This will copy ony one block specified by the count option.

Now to restore the mbr,
```
dd if=/root/mbr.dat of=/dev/sda bs=512 count=1
```

## Creating bootable drive
Before approaching, it is required to identify the source and the destination drive correctly, this can be done by lsblk command.

To make the usb drive bootable, it should be formatted with a specific file format. This can be done with `mkfs.[file_format] /drive/path`.

Next step is to writing the iso file with command: `dd if=/iso/file/path of=/drive/path bs=4M status=progress`