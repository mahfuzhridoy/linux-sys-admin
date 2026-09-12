# Task automation with Cron

Cron is one of the most useful utility for a linux system administrator. It allows to schedule tasks or commands also known as cronjobs at a specific time. Cron runs as a daemon and is used to automate repetativ etasks such as:

- Backups
- Monitoring
- Disk usage
- Updating the system
- sending emails
- logging etc

The text file that contains the cron jobs for a user is called users crontab. There is such file for each user stored on `/var/spool/cron/crontabs`. Only root can access the directory.

There is a command to manage crontab files. The command is  `crontab`. There is also a configurtion file for the system wide cronjobs located in `/etc/crontab`. There are 2 types of cron jobs:
1. System-wide
2. Users individual

## User individual

Each user has a crontab file which is short for cron table. Where all schedule for cron jobs of thea user are specified. These files are located in sub-directory /var/spool/cron. The exact location can vary depending on linux distros. 

The files can be edited by hand using text editors but is not recommended. The recommended way is to using `crontab` command. 

To display the contents of the crontab file of the current user, `crontab -l command is used`. By default there are no cronjobs for a user initially. 

To edit current user crontab file `crontab -e` command used and the user will be prompted for selecting a text editor. Lines that starts with # inside the crontab file are comments.

Each task to be run has to be defined by a single line that consist of 6 fields separated by space. The first five fields define when the task will be run and the last field represents the command or script to be run.

The first five fields respectively:

1. `m` for minute
2. `h` hour
3. `dom` day of the month
4. `mon` month
5. `dow` day of the weeks

If a field contains *, it means any value is allowed for that field. This is different from regex * where it means everything. For example, an * in the day filed means everyday. Minimum time unit used by the cron is minute. if a task is needed to run in every second, It cannot be run using cron. 

To run a task in seconds, A bash script can be created.

#

Practice cronjob: A backup script should be run everyday at exact 6 AM.

```text
    0 6 * * * /root/backup.sh
```

Practice cronjob: A backup script should be run 1, 5, and 15th day of the month at exact 6 AM.

```text
    0 6 1,5,15 * * /root/backup.sh
```

#

