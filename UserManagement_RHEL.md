|Utility |Description |
|----------- | -----------|
|```id``` | Displays user and group IDs.|
|```useradd```, ```usermod```, ```userdel``` | Standard for adding, modifying, and deleting user accounts.|
|```groupadd```, ```groupmod```, ```groupdel``` | Standard for adding, modifying, and deleting groups. |
| ```gpasswd``` | Primarily used for modification of group password in the ```/etc/gshadow``` file whish is used by the ```newgrp``` command. |
|```pwck```, ```grpck``` | Can be used for verification of the password, group, and associated shadow files. |
|```pwconv```, ```pwunconv``` | Can be used for the conversion of passwords to shadow passwords, or back from shado passwords to standard passwords.
|```grpconv```, ```grpunconv``` | Like above these deal with the conversion of shadowed information for group accounts.
##

## Adding a New User:

```$useradd options {username}```

By default the useradd command creates a locked user account.  To unlock the account, run the following command to assign a password:

```$passwd {username}```

### Common useradd options:

[[useradd] man page](https://linux.die.net/man/8/useradd)

##

## Adding a New Group

To add a new group use the following command:

```$groupadd options {group_name}```

### Common groupadd options:

[[groupadd] man page](https://linux.die.net/man/8/groupadd)

##

## Adding Existing User to Existing Group

To override user's primary group, run:

```$usermod -g {group_name} {user_name}```

To override user's supplementary groups:

```$usermod -G {group_name1},{group_name2},... {user_name}```

To add one or more groups to user's supplementary groups:

```$usermod -aG {group_name1},{group_name2},... {user_name}```

or

```$usermod --append -G {group_name1},{group_name2},... {user_name}```

##

## Creating Group Directories

Create /opt/group_dir:

```$mkdir /opt/group_dir```

Add group to system:

```$groupadd my_group```

Associate contents of /opt/group_dir with my_group group:

```$chown root:mygroup /opt/group_dir```

Allow users in group to create files within the directory and set the setgid bit:

```$chmod 2775 /opt/group_dir```

Verify the permissions have been set correctly:

```$ls -ld /opt/group_dir```

Add users to my_group group:

```usermod -aG my_group {username}```


## Research assets:

https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-managing_users_and_groups#table-users-tools