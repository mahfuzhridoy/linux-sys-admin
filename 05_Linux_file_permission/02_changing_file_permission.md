# Changing file permissions
To change file permissions (e.g. read, write, execute) We use chmod command. Only root and the file owner can change the file permissions. 

## Command structure
`chmod [who][operation][permission] file` 
Here, 
1. `who` signifies the user category whose permission will be changed. 
    - `u` the user 
    - `g` the group
    - `o` others

2. The `operation` flags define whether the permissions are to be removed, added, or set.
 - `-` hyphen to remove the specified permission
 - `+` to add the permission
 - `=` to set permissions

 **[Note: set permission will reset the previously given permissions an only add the currenlt specified permissions in the command]**

3. The `permissions` are specified by `r, w, x` respectively to read, write, execute.

Example commands:
- `chmod u-x file`
- `chmod u+x file`
- `chmod u=rwx file`
- `chmod u-x,g+x,o+x file`
- `chmod ug+x file`
- `chmod a+x,a-wr file` Here, a stands for all users.

To display a message we can use `-v` option with the command. And to recursively work on all files in a directory we can use `-R` option.
#
We can also use a file as a reference to assign its permission type to another file with the oftion `--reference=[referencefile]`.

## Numeric method for changing permission
Another method for representing permission is to use octal or 8 based number. The number that represent the permission can be a 3 digit number from 0 to 7. 

The first digit represents the permission for `owner`, second digit for `group`, and the last digit for `others` class. The r,w,x permissions have their own fixed number values.
- Read = 4
- Write = 2
- Execute = 1
- No permission = 0

The permissions that will be given to the file is calculated by the sum of permission fixed numbers. For example: 7 stands for all permission which is sum of 4, 2, and 1. 6 is for read and write which is sum of 4 and 2.

**Example commands:**
- `chmod 744 file`
- `chmod 644 file`