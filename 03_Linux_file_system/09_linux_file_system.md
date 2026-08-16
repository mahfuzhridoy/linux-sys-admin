# Linux file systems
A file system is a logical collection of files on a partition or disk. On a linux system, everything is considered to be a file. File and directory names are case sensitive on linux system.

A file system controls How data is stored and retrived. Each group of data is called file and the structure and logic rules used to manage files and their names are called file systems.

If something that is not a file is process.

## File system hierarchy standard

- `/bin` Contains binaries or user executable files which are available to all users.
- `/sbin` Contains applications that only super users will need.
- `/boot` Contains files required for starting the system.
- `/home` is where users home directories. Under this directory, there is another directory for each user. If that particular user has a home directory.
- `/dev` contains device files.
- `/etc` contains most, if not all system-wide configuration files.
- `/lib` contains shared library files used by different applications.
- `/media` is used for external storage will be automatically mounted.
- `/mnt` is like media but it's not very often used these days.
- `/tmp` contains temporatory files. 
- `/proc` Is a virtual directory contains information about hardware, such as cpu, memory or kernel. For exaample: `cat /proc/cpuinfo` or `cat /proc/meminfo`
- `/usr` saves many command for initial users. 
- `/var` stores variable and log files.

