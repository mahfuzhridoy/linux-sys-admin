# Umask in Linux

## 1. What is Umask?

Umask (user file-creation mask) is a Linux setting by which the **default permissions of newly created files and directories are controlled**.

Permissions are not directly assigned by umask. Instead, specific permissions are **removed from the default permissions** when a new file or directory is created.

The default permissions are:

* **Files:** `666` (`rw-rw-rw-`)
* **Directories:** `777` (`rwxrwxrwx`)

The umask value is used to determine which permissions should be removed.

For example, when the umask is set to `022`:

* New file → `666 - 022 = 644` → `rw-r--r--`
* New directory → `777 - 022 = 755` → `rwxr-xr-x`

By using umask, newly created files and directories can be prevented from being given excessive permissions.

## 2. Methods of Checking and Setting Umask

The current umask can be checked by using:

umask

For example:

umask
0022

The symbolic form can also be displayed by using:

umask -S

Example output:

u=rwx,g=rx,o=rx

The umask can be temporarily changed for the current shell session by using:

umask 027

When `027` is used:

* New file → `640` → `rw-r-----`
* New directory → `750` → `rwxr-x---`

For permanent configuration, the umask can be added to appropriate shell configuration files such as `/etc/profile`, `/etc/bashrc`, or the user's shell startup files, depending on the Linux distribution and shell.

**[Note: to make permanent change on umask command, the umask must be saved to the bashrc file, else the change is umask is limited to current shell session]**

## 3. Example of Umask

Suppose the following umask has been set:

umask 022

A file and a directory can then be created:

touch example.txt
mkdir example_dir

Their permissions can be checked by using:

ls -l example.txt
ls -ld example_dir

The following permissions will typically be displayed:

-rw-r--r-- example.txt
drwxr-xr-x example_dir

For the file, the permissions are calculated as:

666

* 022
  = 644

For the directory, the permissions are calculated as:

777

* 022
  = 755

Therefore, read and write permissions are provided to the file owner, while only read permission is provided to the group and others.

For the directory, full permissions are provided to the owner, while read and execute permissions are provided to the group and others.

## 4. Why Does a Linux Administrator Need to Know This?

Umask is considered important because default permissions for newly created files and directories can be controlled through it.

Unnecessary access can be reduced, and system security can be improved by using an appropriate umask value.

For example, by using:

umask 027

newly created files and directories can be prevented from being accessible to everyone.

Umask is particularly useful when the following are being managed:

* Multi-user Linux systems
* Shared directories
* Application-generated files
* Security-sensitive environments
* User accounts and shell configurations

In short, **access permissions are defined by file and directory permissions, while unwanted default permissions are removed by umask.**

## 5. Important Point to Remember

Umask is applied only when new files and directories are created. The permissions of existing files are not changed by umask.

Regular files are normally created with a default permission of `666`, rather than `777`, because execute permission is not normally included.

Quick example:

umask 022

New file → `644` → `rw-r--r--`

New directory → `755` → `rwxr-xr-x`

Therefore, umask can be remembered as:

**Umask = permissions that are removed from the default permissions.**
