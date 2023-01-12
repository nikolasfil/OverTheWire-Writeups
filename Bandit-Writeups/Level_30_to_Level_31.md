Level_30_to_Level_31

--------------------------------------



Level Goal
There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo. The password for the user bandit30-git is the same as for the user bandit30.
Clone the repository and find the password for the next level.
Commands you may need to solve this level
git


-------
steps: 

```Bash
git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
```

```Bash
bandit30@bandit:/tmp/gitfolder30/repo/.git$ cat packed-refs 
# pack-refs with: peeled fully-peeled sorted
c027ef6d59c4031d56a6c6d16a526af0e8eb8383 refs/remotes/origin/master
831aac2e2341f009e40e46392a4f5dd318483019 refs/tags/secret
```

[git tags](https://devconnected.com/how-to-list-git-tags/)

git tags 

```Bash

bandit30@bandit:/tmp/gitfolder30/repo$ git show secret 
OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt

```


-------


----------
password: OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt

----------

--------------------------------------

