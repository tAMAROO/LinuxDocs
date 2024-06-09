## Linux Logfiles

There are two ways to manipulate log files:

1. rsyslog
2. systemd-journald

### Using rsyslog:
##

>The rsyslog service keeps various log files in the /var/log directory. You can open these files using native commands such as tail, head, more, less, cat, and so forth, depending on what you are looking for.

Examples:

Display boot and other kernel messages, view /var/log/messages:

```$cat /var/log/messages```

You can use grep and other filtering tools to gather more specific events from a file.  You can also use tail to view files as they are updated:

```$tail -f /var/log/messages```

The -f option updates the output when new log file entries are added.

View /var/log/secure to see users and their activites:

```$tail -f /var/log/secure```

### Using systemd-journald:

The difference between systemd-journald and rsyslog is systemd-journald does not keep separate files like rsyslog does.  This avoids checking different files for issues.

Examples:

Show all event messages:

```$journalctl```

View last 10 event messages:

```$journalctl -n```

You can see the last X amount of entries by using:

```$journalctl -n {number}```

Output entries as they are written:

```$journalctl -f```

Display kernel message log from last boot:

```$journalctl -k```

Display different events:

```$journalctl -p {what to find}```

Display messages related to a user:

1. Find user info:
   
   ```$id {user}```
2. Search with journalctl for that user:

    ```$journalctl _UID={UID}```

View entries for today:

```$journalctl --since today```

View entires for a specific service:

```$journalctl -u {service}```

More specific search using httpd service:

```$journalctl -u httpd --since "1 hour ago"```


## Research assets:

https://www.redhat.com/sysadmin/rsyslog-systemd-journald-linux-logs