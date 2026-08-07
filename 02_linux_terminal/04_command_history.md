# Bash command history

The command history are stored in a file .bash_history or       .zsh_history on the home directory by default. Number of commands that will be stored is controlled by an environment variable ```HISTFILESIZE```. 

To access the file ```echo $HISTSIZE``` and it will show the number of commands it can store on the memory.  

### Run a command form history
To run a command from history type ```![command number]```. And to run the last command type !!.

We can run them fro reverse direction too by ```!-3``` now this will star from reverse direction and run the third last command in the history. 

To run a last specified command(e.g. ls) we can type ```!ls```. Now it will run the last ls command or cd command

*[Caution: Running the command like this is dangerous as you dont know with which options did you run it. To stay safe you can type a :p at the end like ```!ls:p``` and it will print the command not run it. After being sure the command is currect then you may run it ]*

#### Searching in bash history
To search for a command in bash history press ```ctrl + r``` and it will enable reverse i search. Then start typing and search result will arrive. Press ```ctrl + g``` to leave history search

*[Caution: This method is not recommended. It can create some problems. sometimes it auto runs the command]*


#### Removing a command from the history
- clear entier history: ```history -c```
- remove single one: ```history -d [line number]```


### How to run a command and not leave any trace?
