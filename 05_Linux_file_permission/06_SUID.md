# SUID
Besides the traditional r, w, and x for the owner, group, and others there are 3 extra special permissions for each file or directory.
- SUID or set user ID
- SGID or set group ID
- Sticky Bit.

These special permissions are for a file or directory overall, not just for a user category. 
#
By default linux commands run with the same executive permission that the user who ececutes them. For example: If the user who executes the `cat` command have permission to read the file, the cat command will also have the access to the file. It doesnt matter that the owner of the cat executable binary is root. But the program will run with the privilages of the user who executes it.

Sometimes it is required to temporarily treat a user as root or as another user. This is wher SUID comes into play. When executable file with SUID is executed, the resulting process will have the permission of the owner of the command, not with the prmission of the user who executed it.

For example: If the `cat` command has the suid bit set then the cat command will only run with root privileges, no matter who runs it. Thats because the root is the owner of the cat binary.

#
## Setting SUID to the cat
#### numerical method:
To set a suid we can use the chmod with numerical values. In this case we have to use 4 digit octal number. The first digit represents the special permission. Example command: `sudo chmod 4755 /file`. Here the 4 is the special permission digit. The 4 stand for SUID bit. We can verify the permissions with `ls -l /file` command and we will see an `s` in the permission field.

Sometimes we may see a capital `S` instead of small `s`. This means the file does not have the execution permission. We can also see the suid by running the `stat [file]` command.
#

#### Symbolic method
We can simply run `sudo chmod u+s /usr/bin/cat`. Now the cat command has the special permission.

**[Note: It is important to remove the SUID permission if not necessary, Otherwise It can cause a security vulnerability]**

We can remove the permissions in the similar way. For example `sudo chmod u-s /file` or `sudo chmod 0755 /file`

# 
### Why do we need this?
In linux, The password is saved on a file that can be only accessed by someone with root privileges. Tf this is the case then how can someone change their own password? To solve this problem we can use suid. Thats why the command `passwd` comes with the SUID bit by default. 

To find all the commands with SUID bit we can use the `find /usr/bin/ -perm -4000`. the -4000 means searching for the file that atleast have this permissions.

#### Programs that run with elevated privileges or has suid bit can oppose a security risks if they are not created with a security by design mindset. An intruder finds an executable file that belongs to root user and has SUID bit set, he can use that to exlpoit the system. It is necessary to ensure that insecure programs with SUID bit set are not installed to the system.