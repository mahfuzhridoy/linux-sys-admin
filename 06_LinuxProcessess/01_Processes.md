# Processes and Linux security model
## Process
A process is a running instance of a program. It runs on its own memory space. Each time a command is executed, a new process starts. A process is an active entity as opposed to a program, which is considered to be a passive entity. Processes are sometimes called tasks. one CPU core can run a single process at a time.

A new process is created only when running an executable file, not when running shell built in commands e.g. type, cd umask.

The operating system maintain a table that associates every process to the data necessary for its functioning. When a process terminates its execution, the operating system releases most of the resources and informations related to that process.

### Process properties:
- PID (Process ID) - A unique positive integer
- User
- Group
- Priority / Nice

If an executable file that represents the process does not have SUID bit set, then the process will have the permission of the user who executes it. It is very important and related to the whole system security.

### Types of processes
There are many types of processes. In linux, all the processes are created with another process which executes the `fork system call`. There is an exception which is the first process that executes when the system is booting. It is init or `systemd` and has the process ID 1. Some types of processes:

- Parent: The process that calls the system fork is the parent process. In other words, the parent process is the process who has created one or more child processes. For example: When we execute the command like `who` this process is created by the parent process `bash`. So the parent process is bash and child process is who.

- Child: The process that is created after system call is child process. A child process has only one parent process.

- Zombie: The terminated process whose data has not been collected is called zombie or defunc process. Normally zombie processe are removed quickly from the memory and does not use system resources.

- Orphan: If parent process terminate before child processes, it is called an orphan. By default all those processes will receive hangup signal. There is also possibility to get adopted by another process such as init or `systemd`. It is the situation when the terminal is closed when a process is running.

- Daemon: A process that runs on the background and does not interact. They have no controlling terminal. The name of daemon ends with d. This is commonly a server application that provides a service. Some popular daemons are `sshd`, `httpd`,`named`,`mysqld`.

### Thread
Multiple threads can exist within the same process and they share resources such as memory. while different processes do not share resources. For example: A text editor execution creates a process, and automatic spell checker, automatic saving is the threads. Threads are basically sub processes that run in the same memory context of a single process and make the application responsive. Threads may share the same data while executing.

### Security insight
Normally if a user installs a malware or a virus and runs it. The malware will have the permissions of the user who executed it. and by default linux does not allows login as root user. So, unless a user runs the virs or maware with `sudo` command, it is mostly safe because unprivileged user is not capable of running important commands.