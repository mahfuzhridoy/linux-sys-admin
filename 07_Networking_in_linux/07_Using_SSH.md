# Using SSH(Secure Shell)
Also know as secure shell is a network protocol used by sytem administrators to securely configure a remote system over an insecure network connection. It infact most useful network protocol for remotely managing servers, routers, switches or other networking devices. 

The ssh involves a client and a server. An ssh client creates a secure connection to the ssh server on a remote machine, then the connection will be used to execute command on a remote server. 

### Installing SSH
To install ssh server and client:- `sudo apt install openssh-server openssh-client`. Verifying the installation `systemctl status ssh`. This can be also verified from the processes list `ps -ef | grep ssh`

To check if ssh is enabled `systemctl is-enabled ssh`. If its enabled then it will start when the system starts. 


## Connecting to ssh server from ssh client
To confirm the server is online first, `ping [server ip]`. If it does not work, network troubleshooting is required. If it works then:

connection command: `ssh [server username]@[server ip]`. example command: `ssh serverUser@10.2.2.4`. Then the user will be prompted to confirm the connection if connecting to it first time. Because the client uses cryptographic fingerprint to prevent man in the middle attack. The fingerprint verifies the server.

> The fingerprint for the server is stored on the .ssh directory of the users home directory.

Once typed yes, then the user need to type the password to connect. To disconnect from the ssh connection, `exit` command is used or `ctrl + d` is pressed.

another form of connecting command `ssh -l [server username] [server ip]`. To connect to another port rather than default port 22 `-p` optin can be used. Example command: `ssh -l serverUser 10.2.2.2 -p 44`. This will connect using SSH to port 44, provided that the port is open and an SSH server is configured to listen on that port.

The configuration file for openssh is located at `/etc/ssh/ssh_config` and can be configured for the users. Here the admin can specify a default port, specify encryption algorithm, default username etc.


## Connecting from windows

Modern windows os also includes built in openSSH client. SO, a user can connect to the server similarly like from linux. But there is another widely used GUI application to connect from windows called [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html?utm_source=chatgpt.com).

To connect using PuTTY, the IP address and port should be specified, and a name to the session should be provided. The session will then be saved and can be connected anytime using that session.
