# Monitoring an user account
In linux a user can login as a user and then switch to another user with su` command. Thats why there are two concepts.
- Real User ID or `RUID`
- Effective user id or `EUID`

The real user id is of the user who initally logged in and euid is for the user who is currently executing commands in the terminal. For example: suppose a user is logged in as user_one and then logs in to user_two with the command `su user_two`. The user_one will contain RUID and user_two will contain EUID. This also implies to the remotely logged in user.

## Logged in user
Normally to see user informations we run `who`, `who am i`, `whoami`, `id` commands. The who command parse and show the content of `/var/run/utmp` file. This file logs current users. To dispaly more information we can use `-aH` option with who command.


To see which users are currently logged in and and some basic information, we can simply run `w` command on terminal. This will show least information about that. The header will show curent time, How long the system is up, The load average in last 1, 5, and, 15 minutes. We can see the same informations with the `uptime` command.

*[Note: The load average should be below 1 or there will be a problem ]*

#
### Investigating security breach
Each time a user logs in, a record for that user is created. To see a historical list of recently logged in user we can run`last` command. It works by reading data from `/var/log/wtmp`.This is useful when we are investigating a possible securitybreach.

To print a specific user from this output we have to pass the username as argument with the last command like this `last [user_name]`
