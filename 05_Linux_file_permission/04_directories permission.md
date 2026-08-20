# Directory permissions
The effect of a direcctory permission has different impact than file pesmissions. 

If a user has only read permission, he can only list the contents of that dorectory but can not access their metadata.

The executute permission (x) does not mean the user can execute the directory. It means the user can traverse or search the directory. It allows to access the known object if has file permission. For example: `cat /data/file.txt` is allowed if the user has execute permission and appropriate file permission too.


#
The user with write permission can do operations like:
- Create files
- Create directories
- Delete files
- Delete directories
- Rename files/directories

Assuming no other mechanism, such as ACLs, sticky-bit restriction, mount restrictions, or MAC policy, prevents these operation. A user with appropriate group membership can potentially do these actions:
- `touch /data/file.txt`
- `mkdir /data/test`
- `rm /data/file.txt`
- `mv /data/a /data/b`

#

### Some important permission and their allowed actions:
- `r` List/read the names of files and directories inside. The `ls` command can give an error because by defaut the ls is an alias of `ls --color=auto` where the option is restricted. To avoid this error run the command with a backslash `\ls`. This disables alias.
- `w` Create, delete, and rename files/directories inside.
- `x` Enter/traverse the directory and access known files or subdirectories inside.
- `rx` List directory contents and access/traverse the entries.
- `wx` Create, delete, and rename entries without being able to list the directory contents.
- `rw` Can read directory entries, but without x cannot properly access/traverse them.
- `rwx` Full directory access: list, traverse, create, delete, and rename.
- **`wx` This means the user can create, delete, and rename entries, but normally cannot list the directory because r is missing. This is most Important combination.**