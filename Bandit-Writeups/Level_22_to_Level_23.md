## Level_22_to_Level_23

--------------------------------------



Level Goal
A program is running automatically at regular intervals from
cron, the time-based job scheduler. Look in /etc/cron.d/ for
the configuration and see what command is being executed.
NOTE: Looking at shell scripts written by other people is a
very useful skill. The script for this level is intentionally made
easy to read. If you are having problems understanding what it does,
try executing it to see the debug information it prints.
Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)


-------
steps: 

```Bash
cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
```

```Bash
cat /usr/bin/cronjob_bandit23.sh 
```

```Bash
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget

```

```Bash
export myname=bandit23
```

```Bash

echo I am user $myname | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
```

```Bash 
cat /tmp/8ca319486bfbbc3663ea0fbe81326349
QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
```


-------


----------

password: QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G

----------

--------------------------------------

