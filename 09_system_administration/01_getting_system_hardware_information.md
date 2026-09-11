# Getting system hardware information
For many reasons getting hardware information is needed. For example, upgrading the system, finding any issues in the hardware etc. There are plenty of commands to do this.
> These command should be run as root users else they will not provide full details

## Whole system information

To extract detailed information about the system: `lshw` command is used. This is by default pre installed in the ubuntu. The output is huge so redirecting it to a file will help. To get the output in other format like json or html, `-json` `-html` can be used. To get only the summary of hardware system `-short` option can be used.

These informations can also be found using `dmidecode` command. This displays the hardware informations from the dmi/SMBIOS tables provided by the system firmware. The output can be filtered by type with the option `-t`. For example: `dmidecode -t bios`

## CPU informations

Another useful command to get hardware information is `inxi`. this is not by default available on all linux distros. Some options for inxi is: `-F` for full overview, `-C` for cpu, `-m` for memory, `-D` for disks, `-N` for network interfaces, `-s` for sensors and temperatures.

Another useful command is `lscpu`. `-J` can be used to get the informations in json format. This display detailed information about the processor and its architecture. These informations can be also seen by `lshw -C cpu`. This will display same informations in different format. This can be further filtered with the help of grep. 

## Memory informations
with the help of `dmidecode -t memoy` command, the information about the memory RAM can be found. It does not display disk space or memory usage. To get the memory usage details, there are other commands like `top` or `free -m`. The dmicode output can be filtered by grep command too.

## PCI buses information
PCI stands for peripheral Component Interconnect. It is a communication pathway that allows computers CPU/memory subsystem to communicate with hardware devices. The informations about them `lspci` command can be used. 

## USB controller information
To list the details about usb controller and the devices conected to them, `lsusb` command can be used. `-v` option can be used to print detailed information about each usb port. 

## Disk information
With the help of `lshw -C disk` disk information can be displayed and further filtering can be done with the grep command. or to get shorter version of output by using option `-short`.

There is another command `lsblk` which also display the disk information. This displays information about disks in a thee like structure.

To get even more details `fdisk -l` command can be used. The output can be filtered for specific disks by providing its name as argument with `-l` command. Example: `fdisk -l /dev/sda`. With the help of `fdisk` command, a user can view, create, resize, delete, change, copy, and move partitions on a hard drive using text based menu.

Another useful command is `hdparm`. This is used to set or get sata drive parameters. To get details about a specific stata drive parameters, `hdparm -i /dev/sds` command can be used. To request identification information directly from the drive with more details `-I` option is used rather than lowercase i.

hdparm can also be used to benchmark or test the hardware performance. Example command `hdparm -t --direct /dev/sda` this does a timing test and the disk read speed test.

## Wireless information
To see information about the wireless device `iw list` command is used.

## Power and temperature status
acpi command can be used to get details about battery, ac-adapter, temperature etc with options `-b, -a, -t` respectively.

#

Mosthe of the comments shows information from the file on the directory `/proc/`. Specific informations about the hardwares can be found from there by reading the files on the /proc directory. For example: `cpuinfo` will display the informations about cpu, `meminfo` will show memory info, `version` will show the running kernel version. Also `uname -r` command can be used to get running kernel version and `-a` to see more informations.

