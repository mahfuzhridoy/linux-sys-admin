# Groups
The main goal of group is to define a set of privileges to a file that can be shared between users. There are mainly two types users.

- The primary group
- Secondary group

[The primary group:]() Are assigned to the files that are created by the user. The group id of the primary group is stored in the /etc/passwd and the group name in /etc/group. When a user creates a file, the user will be owner of the file and its primary group will be the group owner of the file

In linux, the file is owned by both the owner and the group. Each user must belong exactly to one primary group.

[The secondary groups:]() A user can be member of none or more secondary groups. The secondary groups are stored in `/etc/group` file.

To see the group of a user simply run `groups username` or `id`

## Managing groups

To create a group we can use the command `sudo groupadd groupname`. This will create a group and will be added to /etc/group. 

To add or remove a user to the group we can do [this](/04_User_account_management/02_Property_changing.md#changing-and-removing-a-user). To see the groups of a user we run `groups (user_name)`.

To The name of the group use the command `sudo groupmod -n new_name old_name`

To delete the group `sudo groupdel group_name`. If the groupdel does not gives success message. but gives an error if the group does not exists.