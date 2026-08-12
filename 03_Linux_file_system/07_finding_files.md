# Finding files and directories
Finding file is an everyday job for a linux system administrator. To find files and directories we use mainly 2 commands ```find``` and ```locate```. locate is faster because it doesn't search for the file in realtime. It searched in the previously built database. find command searches in the real system to all the directories.

On the other hand, ```find``` command has more options available. the locate command searches by name and returns list of path containing that name.

To use locate command we must continuously update the database with the command ```sudo updatedb```. THe detabase will now be updated. Now to search ```locate passwords``` and itwill return all the fies with name password with absolute path name.

#### Some Useful options with locate

- `-b` search file with its base name
- `-b '\files'` search for absolute file named file exact
- `-e` Check if the file really exist if the db is not updated
- `-i` Ignoring the case
- `-r` Regex search

### which command
which command is used to find the location of a command and return its absolute path. For example: `which ls` It will return the absolute file path of the ls command

Find all the locations `which -a find` finds all the location of find command. Also multiple file name can be passed as arguments.

### Find command
Locate command is fast but has drawbacks too, it can find only on its daabas and database should be updated regularly.

Find searches for files in the directory and recursively onto its sub directory. It can search with name, permission, owner, time and many more properties. 

Basic use `find . -name file.txt` search file with name file.txt. `-iname` option is used for searchi case insensitively. 
It searches with absolute name. to search wildcard `find ./path -iname "file*"`. 

#### Some other options
- `-delete` we can also delete a file with  option
- `-ls` option runs ls command on all the files found by search.
- `type d` search for directory
- `-maxdepth 2` maximum level of depth with argument 2
- `-perm 755` files with 755 permission
- `size 100k` files with 100k size
- `size +100M` files with  greater than 100M size
- `-mtime 0` modified files in last 24 Hours. counted in days
- `-atime 0` accessed atleast 1 days ago
- `-cmin 3` created within 3 minutes atleast
- `-user username` files belongs to the user