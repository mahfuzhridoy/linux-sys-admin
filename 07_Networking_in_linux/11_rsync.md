# Local synchronizing with rsync
rsunc ia a fast and versatile utility that synchronizes between two file or directories That can be local or remote. `rsync` is widely used for backup and mirroring. Its like an improved copy command. This is pre-installed on all major linux distros and macOS. The user that runs the rsync command, must have read permission on the source location and write permission on the destination.

**Basic example:** `rsync -av /etc/ ~/etc-backup/` 

Here, 

- `-a` is to run in archive mode. This copies files recursively, preserve owner, group, and permissions.
- `v` for verbose
- `/etc/` is the source directory
- `~/etc-backup/` destination directory

> *Note:* If trailing slash **'/'** is added in the source location, only contents of the file will be copied but, if its not added then the souce directory itself will be copied.

If the destination directory does not exist, it will create that directory. When the rsync run again with same options and arguments, it will only copy the files that has been changed. If nothing changed then it will copy nothing.

rsync not only copy files, it also removes file if a file is deleted from the source. To do so, `--delete` option is required. This done when the source and the destination must stay exact same.

## Excluding some files
There are 2 ways to do that. 

### --exclude-files option:
***
When using this, a file will be passed as argument which contains the name of files that should be excluded in each lines. Example command: `rsync -av --exclude-iles='exclude.txt' /etc/ ~/etc-backup/`

Here, exclude.txt conatin file names in each line. It is best practice to add the absolute file paths inside exclude.txt file. Example content inside exclude.txt:
```txt
/etc/shadow
/etc/passwd
~/documents/secret
*.png
```
### --exclude option
***
This is quick exclude option. This takes a single argument inside quotes. Also patterns or regex are allowed here. Example command: `rsync -av --exclude-iles='*.png' /etc/ ~/etc-backup/`
This will exclude all png files.

> This can be used multiple times in a single command.

# Synchronizing with remote location

This can also be used To synchronize local directories with the remote server. First thing to check is ssh connection working. This uses ssh to syncronize them.

To synchronize, user on local system should have read permission to the file and the user on remote location should have write permission. 

**Basic Example:**`rsync -av -e ssh /etc/ user@Server_IP:~/etc-backup`

**Here,** `-e ssh` tells to use ssh as transport. This option allows to use the options of ssh too. To do so, the options including the ssh needs to be passed inside quotes. Example: `-e 'ssh -p 2222'`, which will use the port 2222.

Once the command is run, it will ask for confirmation and password of the server user. If `sudo` command is used then sudo password is required. `--delete` option can also be used here. If not used then the file will not be deleted which no longer exist in the source location. All oher options for local sync is also available here.


### Transfering from server to local using rsync
To transfer from server to local, everything is same only need to swithch the source address and destination address. Example: `rsync -av -e ssh user@Server_IP:~/etc-backup /etc/`. Now etc-backup directory content will be copied to local /etc directory.
