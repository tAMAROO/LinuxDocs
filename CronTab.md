## CronTab

### What is crontab?

> The crontab is a list of commands that you want to run on a regular schedule, and also the name of the command used to manage that list.  Crontab stands for "cron table," because it use the job scheduler cron to execute tasks.

### Crontab Syntax:

```MIN HOUR DOM MON DOW CMD```

|Field|Description|Allowed Value|
|----------- | -----------| -----------|
|MIN (Minute) | Specifies the minute when the command will run | Range: 0 to 59 |
|HOUR | Denotes the hour of the day when the command is scheduled to execute. | Range 0 to 23 |
|DOM (Day of Month) | Specifies the day of the month for the task. | Range: 1 to 31 |
|DOW (Day of Week) | Specifies the day of the week for the task. | It is represented by numbers from 0 to 6, wher both 0 and 6 correspond to Sunday. |
|CMD (Command) | Represents the actual command or script that whil run at the scheduled time. | NA |

##

## View Crontab entries:

```$crontab -l```

### View Root Crontab entries:

Login as root user and use

```$crontab -l```

### View others Crontab entries:

Login to root and use

```$crontab -u {username} -l```

##

## Basic Usage:

```$30 08 10 06 * /home/script.sh```

This would run script.sh at 8:30 AM on June 6th *-Everyday of the week.

### Schedule for every minute:

```$* * * * * /home/script.sh```

### Schedule twice a day:

```$00 11, 16 * * * /home/script.sh```

##

### To edit Crontab entries:

This edits the current users entries:

```$crontab -e```

## Research assets:

https://www.geeksforgeeks.org/crontab-in-linux-with-examples/


https://askubuntu.com/questions/2368/how-do-i-set-up-a-cron-job/2371#2371

