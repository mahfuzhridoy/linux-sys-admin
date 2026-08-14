# Removing files and directories
To remove file we use `rm` command. If a file is removed from the terminal, it will be removed permanently. So the user must use `rm` command with caution. However, some professionals can still may restore the data from the disk. 

To make important files totally unreadable even after being recovered, user may use `shred` command. This command will rewrite the file before deleting. Basic command: `shred -vu -n 100 /file/path/file.txt`. This command will rewrite the file 100 times before deleting it.

To get prompted before deleting a file and asking to confirm, use `-i` option and, to get verbose message use `-v` option.

Users use

### Removing a directory
Normal `rm` command can not remove a directory. To remove a directory `-r`. Or we can use another useful command `rmdir`. Although `rmdir` can not remove if there are contents inside a directory. 

### Remove multiple directories
To remove multiple directories, just give the directory names as arguments separated by comma. To remove forcefully use `-f` option.

#

### Caution: While removing a file, please give extra attention at what file you are removing. If by mistake you mistype a removing directory, It can cause a catastrophe.

For example: `sudo rm -rf /home/ studen/a.txt` This command siply looks harmless but there is a extra white space after home directory. If this command is executed, It will remove entire home directory. Because, the command will receive the home directory as argument.

To avoid this situation, try to use `TAB` key for auto completion. This key will not complete the directory name because there is a mistake.

#


