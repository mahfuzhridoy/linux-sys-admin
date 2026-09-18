# Bash command history

System administrators frequently execute many commands while configuring servers, managing services, troubleshooting problems, and performing routine maintenance. Some commands can also be long or complicated, making it impractical to remember and retype them.

Bash command history helps an administrator **recall previously executed commands, repeat commands, search for previous work, and review what commands were executed during troubleshooting**.

For example, if an administrator configured Apache yesterday but cannot remember the exact commands used, the history can be searched instead of repeating the entire process from memory.

However, command history should not be considered a complete security audit log because it can be modified or cleared and does not record everything that happens on a system. For proper auditing, mechanisms such as `auditd` and centralized system logging are more appropriate.

The `history` command is therefore mainly a **convenience and troubleshooting tool**, while also providing some useful administrative context.

#### Bash history files

Bash normally saves command history in the `.bash_history` file in the user's home directory.

Other shells may use different files. For example, Zsh normally uses `.zsh_history`.

The environment variable `HISTFILE` specifies the file used to save the history:

```bash
echo $HISTFILE
```

The number of commands Bash keeps in the current shell's memory is controlled by `HISTSIZE`:

```bash
echo $HISTSIZE
```

The number of commands saved to the history file is controlled by `HISTFILESIZE`:

```bash
echo $HISTFILESIZE
```

So, `HISTSIZE` and `HISTFILESIZE` are different:

* `HISTSIZE` → number of commands kept in the current shell's history list.
* `HISTFILESIZE` → maximum number of commands stored in the history file.

To display the command history:

```bash
history
```

#### Run a command from history

Every command displayed by `history` has a number:

```text
421  sudo systemctl restart apache2
422  sudo systemctl status apache2
423  sudo tail /var/log/apache2/error.log
```

To execute a command using its history number:

```bash
!421
```

This runs command number `421`.

To run the immediately previous command:

```bash
!!
```

To run the most recent command beginning with a particular string:

```bash
!ls
```

This runs the most recent command that starts with `ls`.

For example, if the previous matching command was:

```bash
ls -lah /var/log
```

then:

```bash
!ls
```

will execute:

```bash
ls -lah /var/log
```

> **Caution: Repeating commands directly from history can be dangerous, especially when working as root or using `sudo`. You may not remember the exact arguments or options used previously. To display the command without executing it, use `:p`**

```bash
!ls:p
```

This prints the matching command without executing it. After verifying the command, it can be run normally.

**#### Searching in bash history**

There are several ways to search the command history.

One common method is:

```bash
history | grep ssh
```

This displays previous history entries containing `ssh`.

For example:

```bash
history | grep systemctl
```

can help find previously used `systemctl` commands.

Another useful method is reverse history search:

```text
Ctrl + R
```

After pressing `Ctrl + R`, Bash enters reverse-i-search mode. Start typing part of a previous command and Bash will search backward through the history.

For example:

```text
(reverse-i-search)`apache': sudo systemctl restart apache2
```

Press `Ctrl + R` again to move through older matching commands.

Press `Esc` or `Ctrl + G` to leave the search without executing the command.

**[Caution: Reverse search does not automatically execute a command merely because it finds it. The command is executed only after you accept it, usually by pressing Enter. Always inspect a command carefully before executing it, particularly when it contains `sudo`, file deletion, permission changes, or other potentially destructive operations.]**

**#### Removing a command from the history**

To remove a single command from the current shell's history:

```bash
history -d [line number]
```

For example:

```bash
history -d 421
```

To clear the current shell's history list:

```bash
history -c
```

**[Note: Clearing the shell's history does not necessarily mean that every historical record has disappeared from the system. Other logging mechanisms may contain information about commands or related system activity.]**

**### Date time record**

For troubleshooting and administrative review, it can be useful to know **when** a command was executed.

By default, the `history` command normally displays the history number and command, but not the timestamp.

Bash can display timestamps using the `HISTTIMEFORMAT` environment variable:

```bash
HISTTIMEFORMAT="%d/%m/%y %T "
```

The format specifiers mean:

* `%d` → day
* `%m` → month
* `%y` → two-digit year
* `%T` → time in `HH:MM:SS` format

After setting it:

```bash
history
```

may display something like:

```text
421  18/09/26 21:30:15 sudo systemctl restart apache2
422  18/09/26 21:31:02 sudo systemctl status apache2
```

The format can be changed according to your preference.

To make the setting permanent for Bash, add it to `~/.bashrc`:

```bash
echo 'HISTTIMEFORMAT="%d/%m/%y %T "' >> ~/.bashrc
```

Then reload the configuration:

```bash
source ~/.bashrc
```

**[Important: Timestamps are useful for reviewing shell history, but Bash history is still not a reliable security audit mechanism. For security auditing, use dedicated logging and auditing tools.]**

**## How to run a command and not leave any trace?**

Bash provides several ways to prevent commands from being added to the shell history. However, deliberately hiding administrative activity should not be treated as a security or auditing method. Administrators should understand these mechanisms mainly so they know the limitations of Bash history.

One commonly encountered method is placing a whitespace character before the command:

```bash
 ls
```

Whether this command is ignored depends on the value of the `HISTCONTROL` variable.

Check it with:

```bash
echo $HISTCONTROL
```

Common values include:

* `ignorespace` → commands beginning with whitespace are not saved.
* `ignoredups` → consecutive duplicate commands are not saved.
* `ignoreboth` → both `ignorespace` and `ignoredups` behavior are enabled.

For example:

```bash
HISTCONTROL=ignorespace
```

After this setting, a command beginning with a space can be excluded from Bash history.

**[Note: This behavior is shell configuration dependent and should not be assumed to work identically across all shells or configurations.]**

To inspect the current configuration:

```bash
echo $HISTCONTROL
```

The important point for a system administrator is that **Bash history is not a tamper-proof record of user activity**. A user may be able to delete or avoid history entries, so administrators should not rely on `.bash_history` alone when investigating security incidents or auditing privileged activity.
