# User account creation
To create a new user account we can use `useradd account_name`. When an account is create, a goroup by default is created by the username. We can see that using `groups account_name`. 

Useradd also reads the contents of /etc/login.defs. 

To set a user password `sudo passwd account_name`. Then options will arrive for choosing a password. This was a basic user creation. Home directory will not be created for this user. 

To create a home directory for a user that is already created, create a home directory for the user manually with `sudo mkdir /home/user_name` and then change the ownership to the user `sudo chown user_name:user_name /home/user_name` and lastly provide permission `sudo chmod 700 /home/user_name`. 

#

Creating a user with most common options manually we can use the command `sudo useradd -m -d /home/newUser -c "C++ developer" -s /bin/zsh -G sudo,adm,mail user_name`. Then set the password using previous command. Here:-
- `-m` Creates a home directory .
- `-d` Specify the home directory at `/home/newUser`.
- `-c` Full name/comment field. Stores as the users description.
- `-s` Gives login shell. Here `/bin/zsh` is the shell path.
- `-G` Supplemantary groups. Here this user is added to the `sudo`,`adm` and `mail`
- `user_name` is the actual user name that is created.

## Temporary user
To make a user temporary, set an expiary date of the user. The specified date the user will expire. We can use the command like `sudo useradd -e 2027-12-31 user_name` this will create a temporary user that will expire at 31 december 2027


#### Change or list the password policy of a user
`sudo chage -l user1` Will list the account information. 

#
Sometimes we need a system account that is used for only running a specific service such as a web server. In linux every daemon or process should be run as a user and it is recommneded to not run as a root. 

To create such account that never log in, set the shell of the user to `false` or `nologin`. Then the user will never be able to login on that account.nologin It will say the user is currently not available, and false is a binary immediately says false.


# Create Admin User
To give a user ability to run root commands the user must be added to `sudo` group or `wheel` on RedHat or CentOS. If the goup does not exist, create that group and add the users to the group.