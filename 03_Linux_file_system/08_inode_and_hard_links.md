# Inodes and Hard links
### Inode
Each file on the disk has a data structure called `index node` or `inode` associated with it. Each node is uniquely identified by an integer number called inode number. 

The inode structure stores metadata abut the file such as the type, files permission, file's owner, timestamp etc. except the file contents.

To see the inode number `-i` option with `ls` command is used. With the number the kernel can find the file. The file name doesnt belong to the file structure. 

### Hardlink
The hardlink is the link between a file and the inode structure. It is also the connection between a single file with two names. 

A single file can have many different names that will be linked to the inode data structure with single inode number. A hardlink can be created using `ln` command. For example `ln [existing-file] [new-file name]`.  The second file is not a copy, they point to the same data and changing one will change content of other file.

Removing one file with rm does not make the file inaccessable. The file is still accessable with other name. 

#### Finding the files with same hardlink we can use the command `find ./directory/name -inum [inode-number]`

The hardlink can not be used for directory and can not cross disk partition.