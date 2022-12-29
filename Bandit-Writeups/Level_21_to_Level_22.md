## Level_21_to_Level_22

--------------------------------------



Level Goal
A program is running automatically at regular intervals from
cron, the time-based job scheduler. Look in /etc/cron.d/ for
the configuration and see what command is being executed.
Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)


-------
steps: 

```Bash
/etc/cron.d$ cat cronjob_bandit22 
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```

```Bash
cat /usr/bin/cronjob_bandit22.sh 

```

```Bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv


WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff
```

-------


----------

password: WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff

----------

--------------------------------------

