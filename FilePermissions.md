## Linux File Permissions

### Octal Notations Table:

| Octal| Binary| File Mode|
|----------- | -----------| -----------|
|0 | 000 | ---|
|1 | 001 | --x|
|2 | 010 | -w-|
|3 | 011 | -wx|
|4 | 100 | r--|
|5 | 101 | r-x|
|6 | 110 | rw-|
|7 | 111 | rwx|

### File Permission Letters:

|Letters|Definition|
|----------- | -----------| 
|r | "read" the file's contents.|
|w | "write", or modify, the file's contents. |
|x | "execute" the file. This permission is given only if the file is a program. |

### File Permission Operators:

|Operators|Definition|
|----------- | -----------|
|+| Add permissions |
|-| Remove permissions |
|=| Set the permissions to the specified values. |

### User, Groups, and other Options:

| Reference| Class| Description|
|----------- | -----------| -----------|
|u| user| 	The user permissions apply only to the owner of the file or directory, they will not impact the actions of other users. | 
|g|group| The group permissions apply only to the group that has been assigned to the file or directory, they will not affect the actions of other users. | 
|o|others| The other permissions apply to all other users on the system, this is the permission group that you want to watch the most. | 
|a|All three |All three (owner, groups, others) |

### Reading the Security Permissions in Linux:
>“rw-  r-x  r–“
“rw-“: the first three characters "rw-". This means that the owner of the file can “read” it (look at its contents) and “write” it (modify its contents). we cannot execute it because it is not a program but a text file. 
“r-x”: the second set of three characters “r-x”. This means that the members of the group can only read and execute the files. 
“r–“: The final three characters “r–” show the permissions allowed to other users who have a UserID on this Linux system. This means anyone in our Linux world can read but cannot modify or execute the files’ contents.  

### Examples:

```$chmod ugo+rwx {file_name}```

```$chmod 777 {file_name}```

## Research assets:

https://www.geeksforgeeks.org/permissions-in-linux/

https://www.redhat.com/sysadmin/linux-file-permissions-explained