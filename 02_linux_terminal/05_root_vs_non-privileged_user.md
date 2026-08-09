# Root users vs Non-Privileged users

On each linux systems there are two types of users.

1. Non-privileged users
2. root users

## Root user
Root users exists in all linux system. Root user has the super-power on the system. He can do anything from installing a software, managing other users, changing ownership of file, change network system etc. They can run anu command or access any file.

Because of that power, it is not recommended to login as user because a sigle mistype of command can damage the entier system. thats why it is always recommended to use a normal user to log in to the system.

However a normal user can also access the root user power using ```sudo``` command or become a temporary root user by typing ```sudo su``` command. After typing the command hit enter, then it will ask for the currently logged in users password. 
To logout from the root user type ```exit```. then to activate root user again type ```sudo su -```

To identify whoich user you are type ```id``` command is used. It will show which group or user you are.



## Non-Privileged users
A non- privileged user is a normal server account that does not have full administrative power. They are created so people or application can:

- Run programs and services safely
- Access only the files/resources they need
- Perform regular tasks without changing critical system settings
- Reduce the damage if the account is compromised

They are mainly created for security and least privileges.

### sudo command
sudo command provides temporary root power only for a single command. a non-privileged user canexecute a command that usually required admin root privilege. To do this  ```sudo``` prefix is added to the command and the it will ask for the password. 

*[Note: once a password is given, it will be cached for five minutes. The user can run sudo commands without password for that time being]*

By running ```sudo -v``` a user can update cached credentials. ```sudo -k``` will remove the privilege.

## Unlocking root user

By default root account is locked in the linux distros. To unlock root account, a password needs to be set for the root account using command ```sudo passwd root``` then enter current user password firsh. After that gige password by typing twice.

A user can change his password using the ```passwd``` command and root user can change any users password with this command
```passwd [username]``` and type password for it.