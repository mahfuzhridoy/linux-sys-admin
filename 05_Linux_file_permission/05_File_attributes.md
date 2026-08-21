# File attributes
Linux file permission provides a basic level of security in access control. Linux also has advanced access control like ACLS access control and attributes. The attributes define the properties of the files. They depend on the support on the underlying file system such as extfor. Where the attribute data must be stroed along with the other control structures.

Each file attribute have the one of two states:
- set
- cleared

The attributes are considered distinct from other meta data such as file system perrmissions, owner, group, others ets. The `ls` command can not list the attributes. To list them we have to run `lsattr` command. After we run lsattr, we will see something like this. 

`--------------e------- ./Important`

Here, each letter means the attribute is set and `-` means its cleared. For example: `e` here means extended format and the file is using extend formatting on disk. There can be several other letters. To find them we can go to man page of the change attribute `man chattr`.
#

The `chattr` changes the attribute of a linux file system. The `+, -, and =` operator respectively adds the attribute, removes the attribute, and resets the attribute then provides only specified attributes. Although most of the attribute can be set or cleared by the root only.

## Most important attributes
1. `a` stands for append mode that can be only opened at append mode for writing. Appending means adding to the end of the file. Only the super user has the capability to set or clear this attribute. Example command: `sudo chattr +a user.txt`. Now no one can change the content of the file. They can only add contents at the end of the file. Not even root can do that.

2. `A` used for no access time update. If the attribute `A` is set, its access time can not be modified. It can be set and cleared by the file owner and the root.

3. `i` stands for immutable. It can not be modified. Can not delete, rename, modify, no hardlink can be created. The file is frozen. Only supr user can set or clear the attribute. This attribute is useful to prevent modification or accidental deletion of a important file.

We can set this attribute recursively as well using the command option `-R`.