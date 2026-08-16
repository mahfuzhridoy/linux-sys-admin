# Reading files
There are many graphical text viewers like gedit editor like windows notepad. But in the serever there are no GUI so we can use `cat` command to read the file in the terminal. It is most used command. For example: `cat /etc/passwd`, we can use multiple file as arguments to read them together. 

cat is used for viewing small files only most of the time. we can also use this command to concatenate files: `cat file1 file2 > file3`


## Less and More command
For viewing large files we use less command or more command. For example: `less file1` this will show one window. The navigation here is similar to the [man](/02_linux_terminal/01_man_page.md#important-navigation) page naviation

## Tail, Head, and Watch
To show the last lines of a file `tail file1` will show the last 10 lines of the file. we can use options like `-n 20` to specify the number of lines we want to use. 

If we use `-n +20` option, it will show the last lines of the file starting from line 20.

#### Viewing files realtime
`tail -f /file/pat/file` will show live updates. If the file is updated, it will show them in realtime. When we want to exit, press `ctrl + c`

The head command shows the first 10 lines of the file while used like `head -n 10 file`. 


## watch command
Another useful command is watch command that allows to see program output in realtime. it refresh every 2 second. Two interesting options are `-d` to highlite the update and `-n 3` to update interval. 
