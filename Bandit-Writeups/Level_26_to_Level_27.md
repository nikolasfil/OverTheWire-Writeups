Level_26_to_Level_27

--------------------------------------



Level Goal
Good job getting a shell! Now hurry and grab the password for bandit27!
Commands you may need to solve this level
ls


-------
steps: 

Connect to bandit 26 with the sshkey we obtained from bandit 25 

minimize the window, press v to go to the editor 

run 
```Bash
:set shell=\bin\bash
:shell
```


```Bash
$ ls      
bandit27-do  text.txt
$ 

$ ./bandit27-do
Run a command as another user.
  Example: ./bandit27-do id



bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27 
YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS


```

-------


----------
password: YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS

----------

--------------------------------------

