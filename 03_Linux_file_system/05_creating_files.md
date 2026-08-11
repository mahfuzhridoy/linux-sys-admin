# Creating files and directories

## Creating files
To create a file We can use the ```touch``` command along with the file name for example ```touch example.txt```. This will create a file named after it. Multiple files can be created at once using this command too.

If the command is run again with same arguments, It will update the timestamp.

To create a file with a space in it's name, The file name argument should be passed inside double quotes. For example: ```touch ~/Desktop/"learning linux.txt"```. this file name will contain space now.

### Creating multiple files
To create multiple files at once we can use the touch command too. to create multiple files with different name ```touch index.html style.css readme.md```. this will create 3 different files with the specified name

To ceate file with sequential name we can use ```touch file{1..5}.txt```. This will create files with names in the range provided inside curly braces like ```file1.txt```,```file2.txt```...```file5.txt```. Here the range is between 1 to 5 so there will be total 5 files created. We can also specify it like this ```touch script.{sh,py,js}```. Now script file with different extensions will-be created.

## Creating a directory
To create a directory we use ```mkdir``` command. for example: ```mkdir dir1```. This will create a directory named dir1. We can create multiple directories in single command too like this ```mkdir dir1 dir2 dir3```. 

We can also create a complete directory structures like ```mkdir -p first/second/third``` when none of them exists. But if we try to do it without -p option it will give an error. Because, the directories will be created from right to left, when they try to create the right most directory, it sees that the second also does not exists. This problem is solved by the -p option.



# File types
In linux everything is considered a file. And file can exist even without a file extension. For example: if we create a file without an extension with the command ```touch file```, the file is created. 

All the executables does not have any extension. The extension is required to identify them visually. for example: log file ends with log, .conf extension means it is a configuration file. if we change a file extension with command ```mv file.txt file.png``` the file will change visually but the content will remain same.
