# Linux Cheat Sheet:

## File and Directory Commands

|Command|Man Page|Example|Description|
|----------- | -----------| -----------| ------------|
|ls | [[ls] man page](https://linuxcommand.org/lc3_man_pages/ls1.html) | ```$ls -al``` |List information about the FILEs (the current directory by default).  Sort entries alphabetically if none of -cftuvSUX nor --sort is specified. [Examples](https://www.geeksforgeeks.org/ls-command-in-linux/)  |
|cd | [[cd] man page](https://linuxcommand.org/lc3_man_pages/cdh.html) | ```$cd /etc/``` ,```$cd ..``` | Change the shell working directory. [Examples](https://www.geeksforgeeks.org/cd-command-in-linux-with-examples/) |
|pwd | [[pwd] man page](https://linuxcommand.org/lc3_man_pages/pwd1.html) | ```$pwd``` | Print the full filename of the current working directory. |
|mkdir | [[mkdir] man page](https://linuxcommand.org/lc3_man_pages/mkdir1.html) | ```$mkdir /home/docs``` | Create the DIRECTORY(ies), if they do not already exist. [Examples](https://www.geeksforgeeks.org/mkdir-command-in-linux-with-examples/) |
|rm | [[rm] man page](https://linuxcommand.org/lc3_man_pages/rm1.html) | ```$rm -f file``` | rm removes each specified file. This can also remove directories but must have arguments.  If the directory is not empty use ```$rm -r /directory/``` to remove the directory. [Examples](https://www.geeksforgeeks.org/rm-command-linux-examples/) |
|rmdir | [[rmdir] man page](https://linuxcommand.org/lc3_man_pages/rmdir1.html) | ```$rmdir /home/docs``` | Remove empty directories. [Examples](https://www.geeksforgeeks.org/rmdir-command-in-linux-with-examples/)|
|cp | [[cp] man page](https://linuxcommand.org/lc3_man_pages/cp1.html) | ```$cp /etc/file /home/documents/``` | Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY. [Examples](https://www.geeksforgeeks.org/cp-command-linux-examples/) |
|mv | [[mv] man page](https://linuxcommand.org/lc3_man_pages/mv1.html) | ```$mv /etc/file /home/documents``` | Rename SOURCE to DEST, or move SOURCE(s) to DIRECTORY.  This can also be accomplished with ```$cp```. [Examples](https://www.geeksforgeeks.org/mv-command-linux-examples/)|
|touch | [[touch] man page](https://linuxcommand.org/lc3_man_pages/touch1.html) | ```$touch /home/documents/file``` | Update  the access and modification times of each FILE to the current time. [Examples](https://www.geeksforgeeks.org/touch-command-in-linux-with-examples/)|
|cat | [[cat] man page](https://linuxcommand.org/lc3_man_pages/cat1.html) | ```$cat file``` | Concatenate FILE(s) to standard output. [Examples](https://www.geeksforgeeks.org/cat-command-in-linux-with-examples/) |
|head | [[head] man page](https://linux.die.net/man/1/head) | ```$head file``` | Print the first 10 lines of each FILE to standard output. With more than one FILE, precede each with a header giving the file name. With no FILE, or when FILE is -, read standard input. [Examples](https://www.geeksforgeeks.org/head-command-linux-examples/)|
|tail | [[tail] man page](https://linuxcommand.org/lc3_man_pages/tail1.html) | ```$tail /documents/file``` | Print  the  last  10  lines of each FILE to standard output.  With more than one FILE, precede each with a  header  giving the  file name. [Examples](https://www.geeksforgeeks.org/tail-command-linux-examples/) |
|ln | [[ln] man page](https://linux.die.net/man/1/ln) | ```$ln -s file file``` | Make links between files. [Examples](https://www.geeksforgeeks.org/ln-command-in-linux-with-examples/)  |
|find | [[find] man page](https://linuxcommand.org/lc3_man_pages/find1.html) | ```find cat.txt``` | Search for files in a directory hierarchy. [Examples](https://www.geeksforgeeks.org/find-command-in-linux-with-examples/) |

## File Permission Commands

|Command|Man Page|Example|Description|
|----------- | -----------| -----------| ------------|
|chmod | [[chmod] man page](https://linux.die.net/man/1/chmod) | ```$chmod a+x file``` | Change file mode bits. [Examples](https://www.geeksforgeeks.org/chmod-command-linux/) |
|chown | [[chown] man page](https://linux.die.net/man/1/chown) | chown [options] new_owner[:new_group] file(s) | Change file owner and group. [Examples](https://www.geeksforgeeks.org/chown-command-in-linux-with-examples/)  |
|chgrp | [[chgrp] man page](https://linux.die.net/man/1/chgrp) | ```$chgrp group file``` | Change the group of each FILE to GROUP. With --reference, change the group of each FILE to that of RFILE. [Examples](https://www.geeksforgeeks.org/chgrp-command-in-linux-with-examples/)  |
|umask | [[umask] man page](https://linux.die.net/man/3/umask) | ```$umask``` | Set and get the file mode creation mask. [Examples](https://www.geeksforgeeks.org/umask-command-in-linux-with-examples/)  |

## File Compression and Archiving Commands

|Command|Man Page|Example|Description|
|----------- | -----------| -----------| ------------|
|tar | [[tar] man page](https://linux.die.net/man/1/tar) | ```$tar cvf file.tar *.c```  | GNU 'tar' saves many files together into a single tape or disk archive, and can restore individual files from the archive. [Examples](https://www.geeksforgeeks.org/tar-command-linux-examples/)  |
|gzip | [[gzip] man page](https://linux.die.net/man/1/gzip) | ```$gzip myfile.txt``` | Compress or expand files. [Examples](https://www.geeksforgeeks.org/gzip-command-linux/)  |
|zip | [[zip] man page](https://linux.die.net/man/3/zip) | zip [options] [file_name.zip] [files_names] | Utility for reading and creating 'zip' archives. [Examples](https://www.geeksforgeeks.org/zip-command-in-linux-with-examples/)  |

## Process Management Commands

|Command|Man Page|Example|Description|
|----------- | -----------| -----------| ------------|
|ps | [[ps] man page](https://linux.die.net/man/1/ps) | ```$ps``` | Report a snapshot of the current processes. [Examples](https://www.geeksforgeeks.org/ps-command-in-linux-with-examples/) |
|top | [[top] man page](https://linux.die.net/man/1/top) | ```$top``` | Display Linux tasks.  |
|kill | [[kill] man page](https://linux.die.net/man/1/kill) | ```kill -15 PID``` | The command kill sends the specified signal to the specified process or process group. If no signal is specified, the TERM signal is sent. The TERM signal will kill processes which do not catch this signal. For other processes, it may be necessary to use the KILL (9) signal, since this signal cannot be caught. [Examples](https://www.geeksforgeeks.org/kill-command-in-linux-with-examples/)  |
|pkill | [[pkill] man page](https://linux.die.net/man/1/pkill) | ```$pkill -f pattern``` | Look up or signal processes based on name and other. [Examples](https://www.geeksforgeeks.org/how-to-kill-processes-by-given-partial-names-in-linux/) |
|pgrep | [[pgrep] man page](https://linux.die.net/man/1/pgrep) | ```$pgrep ssh``` | Look up or signal processes based on name and other. [Examples](https://linuxize.com/post/pgrep-command-in-linux/)  |
|grep | [[grep] man page](https://linux.die.net/man/1/grep) | ```$grep -i "text" text.text``` | Print lines matching a pattern. [Examples](https://www.geeksforgeeks.org/grep-command-in-unixlinux/) |

## System Information Commands

|Command|Man Page|Example|Description|
|----------- | -----------| -----------| ------------|
|uname | [[uname] man page](https://linux.die.net/man/1/uname) | ```$uname -a``` | Print system information. [Examples](https://www.geeksforgeeks.org/uname-command-in-linux-with-examples/)  |
|whoami | [[whoami] man page](https://linux.die.net/man/1/whoami) | ```$whoami``` | Print effective userid.  |
|df | [[df] man page](https://linux.die.net/man/1/df) | ```$df -h``` | Report file system disk space usage. [Examples](https://www.geeksforgeeks.org/df-command-linux-examples/)  |
|du | [[du] man page](https://linux.die.net/man/1/du) | ```$du /home``` | Estimate file space usage. [Examples](https://www.geeksforgeeks.org/du-command-linux-examples/)  |
|free | [[free] man page](https://linux.die.net/man/1/free) | ```$free``` | Display amount of free and used memory in the system. [Examples](https://www.geeksforgeeks.org/free-command-linux-examples/) |
|uptime | [[uptime] man page](https://linux.die.net/man/1/uptime) | ```$uptime``` |  Tell how long the system has been running.  |
|lscpu | [[lscpu] man page](https://linux.die.net/man/1/lscpu) | ```$lscpu``` | Display information about the CPU architecture. |
|lspci | [[lspci] man page](https://linux.die.net/man/8/lspci) | ```$lspci``` | List all PCI devices.  |
|lsusb | [[lsusb] man page](https://linux.die.net/man/8/lsusb) | ```$lsusb``` | List USB devices.  |

## Networking Commands

|Command|Man Page|Example|Description|
|----------- | -----------| -----------| ------------|
|ifconfig | [[ifconfig] man page](https://linux.die.net/man/8/ifconfig) | ```$ifconfig``` | Configure a network interface. [Examples](https://www.geeksforgeeks.org/ifconfig-command-in-linux-with-examples/)  |
|ping | [[ping] man page](https://linux.die.net/man/8/ping) | ```$ping host``` | Send ICMP ECHO_REQUEST to network hosts. [Examples](https://www.geeksforgeeks.org/ping-command-in-linux-with-examples/)  |
|netstat(deprecated) | [[netstat] man page](https://linux.die.net/man/8/netstat) | ```$netstat -a```  | Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships. [Examples](https://www.geeksforgeeks.org/netstat-command-linux/)  |
|ss | [[ss] man page](https://linux.die.net/man/8/ss) | ```$ss -t``` | Another utility to investigate sockets. [Examples](https://www.geeksforgeeks.org/ss-command-in-linux/) |
|ssh | [[ssh] man page](https://linux.die.net/man/1/ssh) | ```$ssh username@host``` | OpenSSH SSH client (remote login program). [Examples](https://www.geeksforgeeks.org/ssh-command-in-linux-with-examples/) |
|scp | [[scp] man page](https://linux.die.net/man/1/scp) | ```$scp file.text user@host:/home/documents``` | Secure copy (remote file copy program). [Examples](https://www.geeksforgeeks.org/scp-command-in-linux-with-examples/) |
|wget | [[wget] man page](https://linux.die.net/man/1/wget) | ```$wget -b http://www.website.com``` | The non-interactive network downloader. [Examples](https://www.geeksforgeeks.org/wget-command-in-linux-unix/)  |
|curl | [[curl] man page](https://linux.die.net/man/1/curl) | ```$curl https://www.website.com``` | Transfer a URL.[Examples](https://www.geeksforgeeks.org/curl-command-in-linux-with-examples/)  |
