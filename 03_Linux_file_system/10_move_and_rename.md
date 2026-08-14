# Moving and renaming files

To move and rename files we can use a command `mv`. 

### Moving files
To move files use command `mv /path/to/file/file.txt /destination/path/`. The first argument is source and the second one is destination. `mv` can move multiple files. To do so provide multiple file names that need to be moved as arguments sepaarated by comma, and put the destination path at last.

To move a directory from one place to another simply use the directory name as argument and the destination path. 

#

##### What if a file or directory already exists in a path? In that case, the previous file will be overwritten. To solve this problem use, `-i` to get a prompt before overriting and use `-n` to ignore anything that can override a file.

Some more useful options can be
- `-u` to move file if the source file is only newer version than destination file


### Renaming files
If the source file path and destination file path is same, then the mv command will change the name of source file to destination file. For example: `mv dir1/file.txt dir1/newfile.txt`. this command will change the name of file.txt to new_file.txt 

### Renaming and moving at same time
To do so use `mv /file/path/file.txt /destination/path/new_name.txt`. Since were moving a file into a file, the source file will be renamed to new file.
 