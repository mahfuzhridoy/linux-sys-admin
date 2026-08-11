# Copying files and directories

### Copy file content

Copying file with ```cp``` command type ```cp /file/destination/file.txt ./new_file.txt```. Here the content of the firs file content will be copied to new_file.txt. If ne_file.txt does not exist, it will create the file first. 

If the file already contains some content, it will be overwritten. To avoid this situation use ```-i``` option with cp command. It will prompt the user before overwriting

### Copy file to a destination

To copy a file to a destination type ```cp learning_linux.txt logs.txt ./files/``` here the destination is a directory, so all the files that are specified will be copied to the files directory with its original content

### Copying directory

To copy a directory, we must use ```-r``` option with the cp command. For example: ```cp -r /etc/ ~/Desktop/```. this command will copy the etc directory to the desktop directory.

### Preserving ownership
The user who copies the file becomes the owner of the file. To avoid this we have to use ```-p``` stands for preserve. With this option, the ownership of file will be preserved.