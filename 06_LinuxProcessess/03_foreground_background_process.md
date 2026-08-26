# Foreground and background processes
### Foreground processes
Foreground processes are started by the user and while they are running, user can not start another process in the same terminal. By default every process a user starts run on the foreground. It gets input from the keyboard and sends output to the terminal.

### Background processes
There are many executive or processes that are start by the os or the user running on background. While they are running, a user can start new process. In the same terminal. 

To start a background process an `&` is added in the end of command. Example: `sleep 10 &`. Even if the processes are background, they show their final output to the terminal once the process finishes.

If the user do not want to see the output at all they can redirect the output to a file to save it or redirect to `/dev/null` which is called a black hole. `/dev/null` does not save any output, it immediately discards evrything sent to it.