# Securing the open ssh server
Default settings of openSSH server is not most secure. To meake it secure, some settings needs to be change. the server configuration file is located in `/etc/ssh` and the name of the file is `ssh_config` and `sshd_config` is the configuration file for ssh daemon. To change any settings, user needs to change this file content. 

> Before changing any settings, backing up the main file is best practice.

Inside the configuration file, each line each line that starts with hash is interpreted as comment. ach line can consist of a configuration option. Example: `#Port 22`. here, `#` defines that the line is commented, `Port` is option, then white space and lastly the value for that option `22`. 

In the file, default the file is configured with default options and are commented out. If a user wants to change that default settings, he must uncomment the line and change the value. For example:

*  `#Port 22` this is the default port for ssh to listen on. Which is also commented inside the configuration file. To change the default value, user must uncomment and change the value of it.

#### Detailed discussion
To find out about all the options that are listed in the configureation file, user have to open the man page for the `sshd_config` file with the command `man sshd_config` and then [search](/02_linux_terminal/06_man_page.md#searching) for that option.

##
## Few important settings

To secure the server few things can be done.
* **Security through obsecurity:**  Changing the default listening port to something others rather than port 22. This is called security through obsecurity. Although this does not help if a hacker scans all the ports but still gives a little security against targated attack on ssh.

* **Disable direct root login:** No matter how strong the password is, There is always a possibility for the hacker to find the password. To perform an action that requires root permit, user can use sudo command for that. This reduces attack surface and the password authentication can be restricted for users. configuration line: `PermitRootLogin no`

* **Disable password authentication:** Only public key authentication can make the ssh connection more secure. If its not possible to disable the password login then users must use strong passwords and avoid dictionary words. 

* **Limiting user ssh access:** Only few administrator users really need to access the server using ssh remotely. This settings will limit the impact of a ordinary user having a weak password. This is not available by default. To add this settings, folling line must be written to the file: `AllowUsers user1 user2 user3`

* **Filtering ssh access at firewall level:** iptables rules can be used to do this. If only few admin users there who need access to the server remotely thei ip can be configured using iptables.

* **Using ssh protocol version 2:** Always updated versions should be used

* **ClientAliveInterval:** this option automatically logs out a user if no packets of data is sent or received from the user. It will send a message to user and then automatically log out. Command configuration line: `ClientAliveInterval 300` the time is counted in seconds. and set `ClientAliveCountMax 0` this immediately disconnects the user after one message.

* **Setting max auth tries rule:** this specifies maximum number of authentication tries per each connection. 

* **Max startups rule:** this specifies number of concurrent un authenticated connections to the ssh daemon. 

* **Login grace time:** disconnects the user after specified time if the user fails to login within given time.