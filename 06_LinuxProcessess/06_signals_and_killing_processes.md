# Killing processes
Sometimes an applications becomes unresponsive or consumes lots of resources. There are few options to stop the processes. one of them is `kill` command which sends a signal to the process. When the signal is not specified, its default to 15 or `SIGTERM`

Multiple commands can be used to kill or send signal to a process. For example:
- kill
- killall
- pkill

### kill
Used to send signals from signal lists by the signals associated number or the full name of the signal.

### killall
kills all the instances of a process. example command: `killall -[signal name] [process name or pid]`

### pkill
both kill and killall commands requires either full name of the process or their pid, but pklill command can use partial name to send signals to the specified process. Example command: `pkill -SIGINT slee`. Here, slee is partial name of sleep process.

# Signals
A signal is an asynchronous notification sent to a process that the term is how a process should behave when the signal is delivered. If a process gets the term signal then thats an invitation for the process to enter into terminate state.

Processes can decide to ingnore some of the signals.

## Listing all the signals
To list all the signal, the `kill` command is used with the `-l` option. This will display a list of signals and an associated number with them.

## Sending a signal
First to send a signal to a process, the process needs to be found first, This can be done with `pgrep -l [process name]`. Then the `SIGTERM` SINGNAL can be sent by `kill -[singnal number] [process id]`. example command: `kill -INT 144040` or `kill -2 144040`. Multiple space separated process ID can be sent as argument too. **[Note: all signal name must be written in all caps]**

Instead of copy pasting the PID of processes, A commnad substitution can also be used. For example: `kill -2 $(pidof sleep)`

Non privileged users can send signal to their own processes and the root user can send signal to anyones process.

### Important signals
Some important signals include:
- `SIGHUP` sends reload signal to the processes.
- `SIGINT` sends an interrupt signal.
- `SIGTERM` process can ignore, response immediately, or wait some time before terminating to collect resource.
- `SIGKILL` sends kill signal and the process stops immediately. this is also called hardkill

