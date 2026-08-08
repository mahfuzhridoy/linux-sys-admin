# Linux terminal keyboard shortcut

## Required commands for sys-admin

#### Clear terminal
Press ```ctrl + L``` to clear the terminal

#### Close the terminal
Press ```ctrl + D``` to close the bash shell. It is similar to execute the ```exit``` command

#### Move cursor to beginning
Press ```ctrl + A``` to move the cursor to the beginning

#### Traverse the previous commands
Press ```arrow up``` to access the previous command or ```arrow down``` to go to next one. it keeps moving through previous history

#### Move cursor to end
press ```ctrl + E``` to move the cursor to the end of the command

#### Clear the current command
press ```ctrl + U``` will clear the current command you are typing. This is useful for typing password. just pressing it will clear the password field. 

#### Cancel the running command
press ```ctrl + C``` to cancel the command that is currently running

#### Pause the current command
press ```ctrl + Z``` will pause the executing command and can be resumed later by ```bg %[paused command job id]``` will resume the process

## TAB key
Tab key is used for auto completion of commands or directories. to do so type few characters that can uniquely identify your command and hit TAB, it will search in the bash history and find the command for you and auto complete this.

after typing the command Press tab twice and it will show all the commands that start with the command you typed