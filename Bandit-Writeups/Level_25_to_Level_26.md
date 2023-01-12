Level_25_to_Level_26

--------------------------------------



Level Goal
Logging in to bandit26 from bandit25 should be fairly easy…
The shell for user bandit26 is not /bin/bash, but something else.
Find out what it is, how it works and how to break out of it.
Commands you may need to solve this level
ssh, cat, more, vi, ls, id, pwd


-------
steps: 
```Bash
bandit25@bandit:~$ ls
bandit26.sshkey

ssh -i bandit26.sshkey bandit26@localhost -p 2220
```


```Bash
cat /etc/passwd | grep 'bandit26'
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext

```


```Bash
bandit25@bandit:~$ cat /usr/bin/showtext 
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0

```

we minimize our terminal <6 lines 
and once we connect we see more 
then we press v and go into the editor 



```Bash
:e /etc/bandit_pass/bandit26 
```

we start editing the passwordfile for bandit26 

c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1



-------


----------
password: c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1

----------

--------------------------------------

