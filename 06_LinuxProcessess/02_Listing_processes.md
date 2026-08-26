# Listing the processes
A common administrator task is check if a specific process is running. There are number of comands to do so:
- `ps`
- `pgrep`
- `pstree`
- `top`

Any user can see the information about running processes.
#

### Process Status (ps)
`ps` command without any option display the running process only. This display information in 4 colums. Where: `PID` is the process id which is an integer number that is automatically assigned to the processes to uniquely identify them. This is most important because, through this a user can interact with the process. `TTY` Tells the name of the controlling terminal for the process. If we see question mark on the tty column, thatprobably means the process is a sytem service or a daemon. `Time` is the cumulative CPU time shown in minutes and seconds. `CMD` is the name of the command that is used to start the process.

Some other important columns:
- UID: User id indicated the user who runs the process.
- PPID: The parent process id.
- STIME: starting time of the process.
- %CPU: Show the cpu utilization by the process.
- %MEM: Shows how much memory the process is using.
- VSZ: virtual memory size of the process. It includes all the memory that process can access.
- RSS: Is the size of the physical memory that is being used by the process. It indicates how much memory is allocated. it includesa ll the stack and heap memory.
- STAT: Indicates the process state using a code. some values for STAT:

    1. `S` for sleeping
    2. `R` for running
    3. `Z` for zombie
    4. `I` for idle kernel thread
    5. `T` for stopped
    6. `<` means high priority. `N` means low priority.


To see all the processes we can use `-e` to list the processes and `-f` to do a full listing format and display detailed information about the process. we can also use them together. another frequently used option is `-aux` can be also written `aux` which provide some extra informations. We can also sort the output based on a column with `--sort` option. Example command: `ps aux --sort=%mem` and `ps aux --sort=-%mem` for sorting reversely.

Some other useful options:
- `-u username` for specific users processes. we can also combine with `grep` command for searching a special process. even if the searche process does not exist, the grep will find one output. because when the grep was run it also created a process and and found itself. 

**[Note: when using grep for searching, the searched term must be existed in 2 lines else the process does not actually exist]**
#

### Process status grep (pgrep)
This is the combination of both ps and grep. The simple `pgrep [command]` returns the process ID only. To see the process id and name `-l` option is used. To see the user specific process we need to use -u option. Example command: `pgrep -u user1 sshd` this will look for sshd process owned by user1.

#
### pstree
`pstree` command displays the hierarchical structure of running processes. It merges identical branches by putting them inside a square brackets and prefixing them with an integer number that identifies the number of branches.

To disable the merging of identical branches `-c` option is used. The threads of a process are found under the parent process and are shown in curly braces.