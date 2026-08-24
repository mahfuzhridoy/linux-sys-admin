# Set Group ID (SGID)
SGID is set mainly to directories. If SGID is set on a directory, all files and sub-directories will be owned by the same group owner of the directory where SGID was configured. It is useful in creating shared directories, which are directories that are writable at the group level.

SGID is set on a directory so that newly created files inherit the directory’s group ownership.
For example, a directory named `shared` can be owned by the `developers` group and have SGID enabled.
When Alice creates `report.txt` inside it, the file is automatically assigned to the `developers` group.
The ability to delete or rename `report.txt` is determined by the permissions of the `shared` directory.
If the sticky bit is also enabled, deletion or renaming is restricted to the file owner, directory owner, or root.
Therefore, SGID controls group inheritance, while directory permissions and the sticky bit control deletion and renaming.


### Setting SGID
#
#### Absolute mode
It can also be set using the numeric permission value by adding 2000, such as `chmod 2775 directory`.

#### Relative mode
SGID can be set on a directory using the symbolic command `chmod g+s directory`. 

#### verification
The SGID status can be verified using `ls -ld directory`.
A lowercase s in the group permission position indicates that SGID is enabled.
For example, `drwxrwsr-x` shows that the SGID bit has been successfully set. If we see an uppercase `S`, that means execution permission is not set to that group.

### Why do we need this?
#
For a Linux administrator, understanding SGID is important because shared directories are common in real-world environments.

SGID allows files and directories created inside a shared directory to inherit its group ownership automatically.

This is especially useful when multiple users are working on the same project, application, or set of shared resources.

Without proper group inheritance, files can end up with inconsistent group ownership, causing unexpected permission issues.

With SGID, access can be managed more consistently through Linux group permissions.

It also reduces the need for administrators to repeatedly correct group ownership manually.

Understanding SGID therefore helps administrators design cleaner, more predictable permission structures.

It becomes particularly valuable when managing development environments, shared application directories, and collaborative server resources.

In short, SGID is a small Linux permission feature that can make shared-resource management significantly easier.

That’s why it is worth understanding—not just for an exam, but for managing Linux systems in the real world.
