# Real time view of running processes
Most common tool for viewing the live pdates of running process is `top` command. This tool refresh in every second and display the updates dynamically. This tool display information in two section. 
#

## Summary area (top section)
1. ##### First line of summary section display information about system time, up time, number of user, and load average for past 1, 5, and 15 minutes. If the load average is below 1, that means the system load is perfect

2. ##### The second line displays information about tasks. They display total task, running, sleeping, stopped, zombie process count.

3. ##### Third line shows information about cpu state percentages based on the interval since the last refresh. Where,

- **us**: time running un-niced(high priority) user processes
- **sy**: time running kernel processes 
- **ni**: time running niced(low priority) user processes
- **id**: spent in the kernel idle handler
- **wa**: waiting time for I/O completion
- **hi**: spent servicing hardware interrupts
- **si**: spent servicing software interrupts
- **st**: stolen from this vm by the hypervisor

4. ##### Foruth line shows information about physical memory (RAM). They are displayed in megabytes. Meanings of them:
- **total** → Total installed RAM
- **free** → Completely unused RAM
- **used** → RAM currently being used
- **buff/cache** → Memory Linux uses for caching files and data

5. ##### last line display information about Swap memory in megabytes. Swap memory is space on disk that the OS can use as extra virtual memory. this is much slower than RAM. Informations include:

- **total** → Total installed RAM
- **free** → Completely unused RAM
- **used** → RAM currently being used
#

## Process list section

This section displays processes in a list format along with their `PID, USER, PR, NI, VIRT, RES, SHR, S, %CPU, %MEM, TIME+, COMMAND` by default. Detailed Information about them can be found on `man top` page. In the man page, searching for `/columns` takes to the details of the meaning of each column section.

### Interactive commands
There are some interactive commands in top command. when the special keys are pressed they take some actions. Most important interactive keys are:
- `h` shows a help summary and `q` to exit from it
- `1` change the display and see individual statistics for each cpu.
- `t` change the cpu display to simple ascii graph, press multiple times to change the view.
- `m` to change the memory and swap to differen display options
- `d` reset the refresh time
- `space key` refresh the stats manually when pressed
- `y` highlight running processes in the process list
- `x` to highlight the column used to sort the process list
- `b` to bold and highlight the column and the running process
- `<` or `>` to change the columns that will used to sort the list.
- capital `R` reverse the sorting order of the selected column.
- `e` to change the size unit. press multiple times to keep changing
- capital `P` to sort the process by cpu and capita `M` to sort by memory.
- `u` to see the processes of a selective user.
#

To display or change the fields that will be showed, pressing `f` will take to the fields management page. Fields that have `*` beside them are currently displaying. to select or disselect a field firt navigate to that field by pressing up or down key and then press `space`. 

To change the field order first the right key is pressed when on the selected field, then pressing up or down key will change the position of the selected field. after going to desired position, left key is pressed. 

The changes that are made is temporary, when restarted `top` everything will be reset to default. Pressing capital `W` will save the configuration. 

## Useful options 
Some useful otions for top command are:
- `top -b -n 1` batch mode outputs a single snapshot of top to plain text. perfect for logging/cron jobs.
- `top -u [username]` launches top pre filtered for a specific user
- `top -p [PID]` monitors only a specific process ID or comma separated PIDs.
- `top -d 1` sets the initial screen refresh delay exactly 1 second.