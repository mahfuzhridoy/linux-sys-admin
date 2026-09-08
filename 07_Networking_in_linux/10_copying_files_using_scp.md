# Copying files over the network using SCP
SCP is very useful when need to transfer a file over the network. This tool uses ssh for transferring files. scp is part of openSSH client package. This can be used in three different ways:

- Copy files from users computer to the server
- Copy files from server to the users computer
- Copy files from one server to another server

Before copying files, First thing that needs to verify that the user has ssh access to the remote ssh server in case of copying the file to or from. 

## copying the files
Once verified that the user has ssh access, Copy process can now be started. To do that, simple command:

     scp -rp -P 22 [file] username@ip_address_of_server:copy_location

Here, 

* `-P` specifies the port. If the port is at default 22 then this option is not necessary
* `[file]` here the file to be copied is used.
* `username` is the user who is authenticated to the server.
* `ip_address_of_server` here server ip address should be placed. The username and address are connected with `@` between them. No space are allowed
* `copy_location` Is the file path on the server where the file will be copied to. this is connected with the ip address with colon `:` between them. no space is allowed.
* `-r` to cpy a directory. here r stands for recursive which copies the whole directory recursively.
* `p` is lowercase p which preserves the access and modification time.

Once run the command, it will ask for the password of the user on the server whose account is being used.

To copy the file with a different name on the server, the file name should be specified. For example: `scp -P 22 pc_file.txt student@10.10.20.34:~/server_file.txt`. now the client file will be saved to the server with name `server_file.txt`.
#

> Note: To be able to cpy files, the user who runs the command must have the read permission to the file being copied and the user that authenticates on the server must have the write permission on the destination path.

#

### Remote server to users computer
To copy files from the remote server to users computer, the server address and file path should be provided as source and users computer directory, where the file will be copied should use as destination address. For example: `scp student@10.10.20.34:~/server_file.txt /users/destination/directory`. And to copy a directory, `-r` option can be used.

> **Caution:** when copying a file, if the destination already has a file with same name, that file will be replaced with the copied file.

The colon `:` symbol distinguish between local address and remote address.

### Remote server to another server
To copy files from remote to remote server, the user must have access to both system from the machine the command will be run. To copy, user need to run the command: `scp user1@serverIP:source_file_path user2@serverIP:destination_directory`. Here, first address is source and second address is destination.


## SCP vs SFTP
SFTP is a file transfer protocol which also uses ssh but there are few differences between scp and sftp. The sftp has extra features like resuming interrupted transfers, directory listings, or remote file removal. 

> **SFTP is more complex and featureful than scp but, scp is faster than SFTP.** 

There are some GUI applications for file transfer using scp and sftp protocols. Popular two:

- `WinSCP` for windows only
- `FileZilla` the cross platform application. supports drag and drop.