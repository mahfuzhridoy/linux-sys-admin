# ANACRON

Anacron is a Linux task scheduler used to run commands or scripts periodically.

Unlike cron, Anacron does not require the system to be running at the exact scheduled time.

For example:

If a task is scheduled to run daily at 6:00 AM using cron, but the computer is turned off at 6:00 AM, cron will miss that execution.

With Anacron, the task can run when the system becomes available again.



## CRON vs ANACRON

**Cron:**

* Runs tasks at a specific time.
* If the system is powered off at the scheduled time, the task is missed.
* Suitable for systems that are continuously running.

**Anacron:**

* Runs tasks based on a period rather than an exact time.
* If the system was unavailable, Anacron can run the missed task after the system becomes available.
* Useful for laptops, desktops, and systems that are not always running.

---

### ANACRON CONFIGURATION FILE

The main configuration file is:

/etc/anacrontab

A typical anacrontab looks like:

period   delay   job-identifier   command

Example:

1    5    daily-backup    /home/user/backup.sh

Here:

1
= Run the job every 1 day.

5
= Wait 5 minutes after Anacron starts before running the job.

daily-backup
= A unique name used to identify the job.

/home/user/backup.sh
= The command or script to execute.

---

ANACRONTAB FIELDS

1. PERIOD

Specifies how often the job should run.

Common values:

1   = daily
7   = weekly
@monthly = monthly

Example:

1    5    backup    /home/user/backup.sh

This means the job should run once every day.

---

2. DELAY

Specifies how many minutes Anacron should wait before executing the job.

Example:

1    10    backup    /home/user/backup.sh

The job will run 10 minutes after Anacron determines that it is due.

---

3. JOB IDENTIFIER

A name used to identify the job.

Example:

1    5    backup    /home/user/backup.sh

Here, "backup" is the job identifier.

---

4. COMMAND

The command or script that Anacron executes.

Example:

1    5    backup    /home/user/backup.sh

Here:

/home/user/backup.sh

is the command being executed.

---

HOW ANACRON WORKS

Suppose we have:

1    5    backup    /home/user/backup.sh

Anacron checks whether the backup job has been executed within the required period.

If the job is due, Anacron waits for the specified delay and then executes it.

For example:

Computer is turned off for several days.

Computer is started today.

Anacron detects that the daily backup job is due and executes it after the configured delay.

---

IMPORTANT DIFFERENCE

Cron asks:

"Is it the scheduled time?"

Anacron asks:

"Has this periodic task been performed within its required period?"

This is the main conceptual difference between cron and Anacron.

---

IMPORTANT LIMITATION

Anacron is not designed for tasks that must run at an exact time.

For example:

"Run this script every day exactly at 06:00."

Cron is more appropriate for this.

Anacron is better for:

"Run this task once every day, even if the computer was not running at the expected time."


#### DEFAULT ANACRONTAB

The system-wide Anacron configuration is usually located at:

/etc/anacrontab

You can view it with:

cat /etc/anacrontab

---

### SIMPLE EXAMPLE

Suppose we want to run a backup script once every day.

Script:

/home/user/backup.sh

Anacrontab entry:

1    5    daily-backup    /home/user/backup.sh

Meaning:

1
→ Check/run every day

5
→ Wait 5 minutes before execution

daily-backup
→ Job identifier

/home/user/backup.sh
→ Script to execute

---

REMEMBER

Cron:
Exact time-based scheduling.

Anacron:
Periodic scheduling that can compensate for missed executions when the system was unavailable.

Anacron is especially useful on systems such as laptops and desktops that may not be running continuously.
 