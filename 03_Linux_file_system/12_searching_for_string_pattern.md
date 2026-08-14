# Searching for string pattern

The most used tool for pattern search is `grep` command. Basic usage `grep string /file/path/file.txt` will search for the term string in the file.txt and to search for a string that contains space, send the argument inside a single or double quotes like this `grep "command line" /etc/ssh/ssh_config`. Now it will search for "command line" in ssh_config file.

To ignore case use `-i` option. To print the line number it found on `-n` works.

The `-w` option will search for whole word. Only return if the string specified is a whole word not a name containing similar pattern.

The `-v` Does reverse searching. Returns result that do not contains the search term.


The `-R` searched in the directory and also its sub directories recursively. For example: `grep -R 127.0.0.1 /etc/` . This command does not have all the permissions, to give permission, run with sudo.

To count number of matches use `-c` option . Also can use `wc -l` to count number of matched lines


## Kernel ring buffer
using `dmesg` we can see kernel ring buffer. We can combine this command with grep to find error messages in kernel ring buffer

Kernel ring buffer is the messages in ram mostly produced by device drivers. 

to search `dmesg | grep error`

## Searching context
To search for a match along with its before and after context `dmesg | grep -A 3 -B 4 error`. Here -A will print 3 lines after the matched line and -B will prin 4 lines before the matched lines. We can also use `-C` to see the context. It will print same number of lines before and after. For example: `dmesg | grep -C 4 error`.


#


## Searching in binary files
The `strings` command extracts printable characters from binary files. It prins out character sequences that are at least 4 characters long. 

For example: First find ls command `which ls` then `strings /path/to/binary/binary`

Printing all ascii files use `-a` option with strings command

## Searching into physical device

Searching in the memory `sudo strings /dev/mem | less`
