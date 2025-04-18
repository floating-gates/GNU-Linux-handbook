# Scheduling shell

To make a system wide repeatable job, edit the contab config file:

```sh
crontab -e
# sudo vim /etc/crontab
```

A cronjob will look somethinglike this:

```sh
0  2  *  *  * root /usr/bin/find /var/log/myservice -type f -name '*.log' -delete
```

Hence the cronjob config will look something like:

```sh
# 
SHELL=/bin/sh
PATH=/usr/bin:/bin:/usr/sbin:/sbin:/opt/slurm/bin:/usr/local/bin

# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
* * * * *  /home/user/read_scheduling.sh >> /home/user/log_read_scheduling 2>&1
```

## Jobs and Paths

When a cron job runs, it does so in a restricted environment, which means it does not automatically inherit the user’s or system’s environment variables or paths. This can lead to issues where the cron job fails because it cannot find the necessary executables or scripts due to an undefined or incorrect path.

In light of this, you can explicitly set the PATH environment variable within the crontab file to handle paths in cron jobs. This tells the cron daemon where to look for executables. For example:

```sh
PATH=/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin
```

<!--  Script to show the footer   -->
<html>
<script
    src="https://code.jquery.com/jquery-3.3.1.js"
    integrity="sha256-2Kok7MbOyxpgUVvAk/HJ2jigOSYS2auK4Pfzbm7uH60="
    crossorigin="anonymous">
</script>
<script>
$(function(){
  $("#footer").load("../../footers/footer.html");
});
</script>
<body>
<div id="footer"></div>
</body>
</html>