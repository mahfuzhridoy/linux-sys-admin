# Timestamp 
Every file system on linux ha three timestamps. These are:

1. The access time or `atime` is the last time file was read. `ls -lu` 
2. The modified timestamp or `mtime` is the last time the contents of the file was modified. `ls -l, ls -lt`
3. The changed timestamp or `ctime` is the last time when some metadata related to the file was changed. `ls -lc`

Also `stat` command show these times.
Use `ls -l --full-time` to show the entire timestamp. 

With the `touch` command with argument that already exists, the timestamp will be updated to current time. To assign the update time to a specific time we can use `touch -m -t 201812301530.34 linux.txt` to change the modify time. the time format here is Year, month, date hour, min,second.

with `-d` option changes both access and modification time together. For example: `touch -d "2010-10-31 15:45:30" file.txt`

### There is no option to change the modify time. To do it, change your device time then modify the time.

Use the `date` command to see and change the time.