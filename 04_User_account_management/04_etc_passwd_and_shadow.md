# Passwd file
Each line of the file represent a user account. The contents are separated by colon `:` representing different fields. 

`debian-tor:x:119:124::/var/lib/tor:/bin/false`

- first field login username. here `debian-tor`
- second field is password. It is not stored in clear text. if its blank, it does not rexuire any password to login. The password is stored in /etc/shadow file.
- third field is the user ID a positive integer number. and fourth is the goup ID.
- fith filed is the comment.
- sixth field is the users home directory. here `/var/lib/tor`
- seventh field is the shell. here `/bin/nologin` means not allowed to login.


# Shadow file
It stores the actual password of a user in encrypted format. This file is only readable by the root account. It has 9 separate fields.

- first field is user name
- second field is password in encrypted format.
- next fields are related to password expiratin. 

Full description of each field is stored in man page of shadow.
If the password filed contains `*` means login not accessible.
#
### The password field
Usually the password format is set to `$type$salt$hash`. Example password: `$y$j9T$iePjG0sGSIpixutLoEJ0i/$cBQfnQVei1r3H5DlhEkwVM.Ebq.Kijvy8eQFM1CjNh1`

Here, $y is the type of hash algorithm which is:
- `1` for  MD5
- `2a`, `2b`, or `2y` for bcrypt
- `5` for SHA-256
- `6` for SHA-512
- `y` for yescript

#
Salt, here the salt is `$j9T`. The salt is combined in the hashing process. This applies a security measure. The salt is randomly generated which mitigate password attack like the `rainbow table`

The `salt` is random but not secret like password. The same password will give different hash.

