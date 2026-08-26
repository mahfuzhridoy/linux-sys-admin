# Job controlling
When a background process starts, Two integer number is shown. First one is called the jobID and the second one is PID or process ID. Once the process finished, it will display the job id and done including the command that ended.

If more processes have been started from the same terminal, they can be listed using `jobs` command. to list the jobs with jobID along with the PID `-l` option is used.

#### To take a process from background to foreground, `fg %[jobid]` command is used.

### Suspend and resume a process
To suspend a process running in the terminal `ctrl + z` is pressed. The process is temporarily stopped not discarded. The process can still be found in the processes list. to resume the process in background `bg %[jobid]` and in foreground `fg %[jobid]`
#
### nohup
If a process is running and in the mean time the terminal is closed or logged out or gets disconnected from remote host, The process will be killed. Closing the terminal, the running processes receives `SIGHUP` signal is sent to all the running processe and the process will be terminated.

This can be painful while working ona  remote host, So, to solve this problem `nohup` command can be used. The syntax of nohup is `nohup [command that should be executed]`. Example command: `nohup sleep 10` and now even if we close terminal or lose connection, the command keeps running.
#
When nohup command is run and terminal is closed, the command output will be saved at the `nohup.out` in the directory where the command is executed from. If the user who executed the program does not have write permission to the same directory, the file will be created at that users home directory.

when a process is started with `nohup`, and bash shell gets terminated th process gets adopted by the `systemd` or `init` which is first process created when 
#

### Nohup alternatives

Some popular nohup alternatives are `screen` and `tmux`

#### Tmux
`tmux` (Terminal Multiplexer) is used to create and manage persistent terminal sessions. A program can be started inside a tmux session and can be kept running even when the SSH connection is disconnected or the terminal is closed. The session can later be reattached after reconnecting to the server. It is commonly used for long-running processes, remote development, monitoring, and server-side tasks.

example commands:

- tmux                         # A new session is started
- tmux new -s mysession        # A named session is created
- tmux ls                      # Running sessions are listed
- tmux attach -t mysession     # A session is reattached
- tmux detach                  # The current session is detached
- tmux kill-session -t mysession # A session is terminated

#### screen

screen is also similar to tmux. The do almost same things. Common usage commands:

- screen                       # A new session is started
- screen -S mysession          # A named session is created
- screen -ls                   # Running sessions are listed
- screen -r mysession          # A session is reattached
- screen -S mysession -X quit  # A session is terminated