# Absolute path vs relative path
The basic way to explore the linux file system is to using ```cd, pwd, and ls``` command. the ```cd``` command will take the user to a path whre the user want to go.  For example: ```cd /var/log``` command will take the user to the log directory.

The ```pwd``` command stands for print working directory will show wich directory the user currently is working on. And the ```ls``` command is used for listing contents in a directory.

running only ```ls``` will list current directory contents. But, a user can list the content of other directories by passing that directory path as argument with the ls command like ```ls /var/log```.


### Path
A path is a unique location to a file or a directory on file system of an OS. there ar two types of path
- Absolute
- Relative

#### Absolute path
Is a pth to the directory started from the root directory. They start with a ```/``` slash. For example: ```/home/kali/Desktop``` is an absolute path. 

The absolute path always remains the same. But a relative path changes based on which directory the user is working on. The absolute path is more reliable than the relative path. But relative path is used for faster and easy access of file or directory.

#### Relative path
A relative path is related with the current directory. It begins from current directory and navigated to the file system. They never start with forward slash```/```. In relative path ```.``` represents th current directory and ```..``` represents the parent directory. These two are created in all directory by default and can be seen with ```ls -a``` command.

With the single dot ```.``` and double dot ```..``` we can build a relative path. For example: If my current directory path is ```/home/kali/Videos/Linux Admin``` and i want to create a relative path to programming directory inside the Document directory, we can type ```cd ../../Document/programming``` and this will take me to the directory with the relative path. here the relative path is ```../../Document/programming```

*[Note: the tilde ```~``` represents he home directory of current user]*


### tree
tree is a handy command that can be used to visualize and understand the file system. it lists the content of a directory in tree structures which is useful to visualize the current directory structure. 

user can also pass the absolute path as argument with tree command ```tree ~/Documents/programming```
