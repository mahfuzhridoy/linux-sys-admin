# Changing properties of a user
All the informations about the user is stored in few files which are, `/etc/etcpasswd`, `/etc/shadow`, `/etc/group`, and `/etc/gshadow`. There is also `/etc/login.defs` which containd the default options for a new user if they are not specified while created.

## Changing and removing a user
`usermod` command is used for this actions. Options of `adduser` commands are available for this command too. Instead of creatign a new uset, this command modifies the properties.

For example: `sudo usermod -c "Not a test user" user_name` Will change the comment of the user to "Not a test user"

- `-g` to add the user to a primary group
- `-G` to add the user to a secondary group.

when used this option, if the user is currently on a group that is not specified by the -G option while executing, the user will be removed from that group. The user will be members of the specified groups only.

This situation can be avoided by using `-a` option.


## Deleting a user
To delete a user we can use `sudo deluser user_name`. This will only delete the user, not its home directory. To delete all these use `-r` option with it.

