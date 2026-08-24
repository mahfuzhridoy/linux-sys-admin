When setting the permissions recursively, it is important to distinguish between file and directories. Both file and directory should not have the similar permissions. If so then it may create some problems. 

To add a filter on types, we can take help from the find command. Example command:

`find /var/log -type f -exec chmod 640 {} \;`

This command will change all the files inside /var/log directory but exclude the directories. Similarly we can change permissions of directories by specifying the type with `d`.