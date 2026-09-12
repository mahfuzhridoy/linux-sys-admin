# Root users vs Non-Privileged users

On each Linux system, there are two types of users.

1. Non-privileged users

2. Root users

## Root user

Root users exist in all Linux systems. The root user has the super-power on the system. He can do anything from installing software, managing other users, changing ownership of files, changing network systems, etc. They can run any command or access any file.

Because of that power, it is not recommended to log in as a root user because a single mistype of a command can damage the entire system. That's why it is always recommended to use a normal user to log in to the system.

However, a normal user can also access the root user's power using the `sudo` command or become a temporary root user by typing the `sudo su` command. After typing the command, hit enter, then it will ask for the currently logged-in user's password.

To log out from the root user, type `exit`. Then, to activate the root user again, type `sudo su -`.

To identify which user you are, the `id` command is used. It will show which group or user you are.

## Non-Privileged users

A non-privileged user is a normal server account that does not have full administrative power. They are created so people or applications can:

- Run programs and services safely

- Access only the files/resources they need

- Perform regular tasks without changing critical system settings

- Reduce the damage if the account is compromised

They are mainly created for security and least privilege.

### sudo command

The sudo command provides temporary root power only for a single command. A non-privileged user can execute a command that usually requires admin/root privileges. To do this, the `sudo` prefix is added to the command, and then it will ask for the password.

**[Note: once a password is given, it will be cached for five minutes. The user can run sudo commands without a password for that time being]**

By running `sudo -v`, a user can update cached credentials. `sudo -k` will remove the privilege.

## Unlocking root user

By default, the root account is locked in Linux distros. To unlock the root user, a password needs to be set for the root account using the command `sudo passwd root`. Then, enter the current user's password first. After that, give a password by typing it twice.

A user can change his password using the `passwd` command, and the root user can change any user's password with this command:

```
passwd [username]
```

and type the password for it.


| User        | Privileges           | Typical use           |
| ----------- | -------------------- | --------------------- |
| Normal user | Limited              | Everyday work         |
| Root        | Unrestricted         | System administration |
| `sudo` user | Controlled elevation | Administrative tasks  |
