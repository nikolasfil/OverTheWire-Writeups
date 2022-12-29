## Level_18_to_Level_19

--------------------------------------



Level Goal
The password for the next level is stored in a file readme in
the homedirectory. Unfortunately, someone has modified .bashrc
to log you out when you log in with SSH.
Commands you may need to solve this level
ssh, ls, cat


-------
steps: 

```Bash
scp -P 2220 bandit18@bandit.labs.overthewire.org:/home/bandit18/readme readme 
```

```Bash
cat readme 
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```

-------


----------

password: awhqfNnAbc1naukrpqDYcF95h7HoMTrC

----------

--------------------------------------

