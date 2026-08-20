# Understanding file permission 
The file permission specify who can access, change or execute a file on linux system. It ensures that only authorized user and processes can access files and directories. Each file and directory has an owner and a group. By default, the owner is the user who created the file and the group is the primary group of that user.

The ownership of a file or directory can be changed bythe root using `chown` and chgrp `commands`.

**For each fie, the permission are assigned tto three different categories:**
- The file owner `(o)`
- The group owner `(g)`
- Others `(o)`

**There are three file permission types:**
- The read permission `(r)`
- The write permission `(w)`
- The execute permission `(x)`

## Listing the permssions
When a user lists a file with the command `ls -l file.txt`, Tehy see somethin like this sequence `-rw-rw-r--` in beginning of the line. Here,
- The first dash indicates the file type. `-` means file, `d` means directory etc.
- Then the 3 sequences charated defines th permission of the owner. here in this example `rw-` means the owner of this file have read (r) and write (w) permission.
- Similarly next three sequenced character defines the permissions of the group that the file is associated to.
- Last three character defines permission of other users.