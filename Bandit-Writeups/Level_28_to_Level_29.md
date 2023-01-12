Level_28_to_Level_29

--------------------------------------



Level Goal
There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo. The password for the user bandit28-git is the same as for the user bandit28.

Clone the repository and find the password for the next level.
Commands you may need to solve this level
git


-------
steps: 

Make a temp folder 

Clone the repository same as the level 27 

```Bash
git checkout  2c1f82f75ab09c89166dd9e6e351bf479fb2d48f 
Previous HEAD position was 444da53 initial commit of README.md
HEAD is now at 2c1f82f add missing data
bandit28@bandit:/tmp/gitfolder28/repo$ cat README.md 
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S
```

We could also solve it with the command : 

```Bash
git log -p 
```

Which shows also the differences 

-------


----------

password: tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S

----------

--------------------------------------

