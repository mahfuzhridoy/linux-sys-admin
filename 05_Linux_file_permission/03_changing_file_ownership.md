# Changing file ownership
In linux operating system, every file is associated with an owner and assigned with permission for owner, group, and others. Only root can change the file ownership.

A normal user can change the group of a file only if the user owns that file and only to a group which they are member of. 
To see athe ownership or group of a file we can run `ls -l [file]` command

## chown command
To change the ownership of a file or directory we have to run `chown` command follwed by the `username` of the new owner and the target file or directory as an argument. We can pass more than one files as an argument to change their ownership.

We can also use the numeric user id istead of the user name to change ownership. We can find the user id on `/etc/passwd` file. To chenge the ownership we have to run command as `sudo chown +[user_id] [arguments]`. To also change the group we can simply add the groupname with the  username separated by colon like this `[user_name]:[group_name]`

To change the group of the file only we can use `sudo chgrp [group_name] [file_name]`. To change the group with chown command we can use the group name appended with colon `chown :[group_name] [file]` 

To change all the files permission recursively, we have to use `-R` option whith the chown command.