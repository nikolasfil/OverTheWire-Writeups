Level_29_to_Level_30

--------------------------------------



Level Goal
There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo. The password for the user bandit29-git is the same as for the user bandit29.

Clone the repository and find the password for the next level.
Commands you may need to solve this level
git


-------
steps: 


```Bash
git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
```


```Bash
bandit29@bandit:/tmp/gitfolder29/repo$ git branch -r 
  origin/HEAD -> origin/master
  origin/dev
  origin/master
  origin/sploits-dev

```


```Bash
bandit29@bandit:/tmp/gitfolder29/repo$ git checkout dev 
Branch 'dev' set up to track remote branch 'dev' from 'origin'.
Switched to a new branch 'dev'
bandit29@bandit:/tmp/gitfolder29/repo$ git log -p
commit be91af8ed9847de549d0e3361cfc675674b25867 (HEAD -> dev, origin/dev)
Author: Morla Porla <morla@overthewire.org>
Date:   Wed Jan 11 19:18:55 2023 +0000

    add data needed for development

diff --git a/README.md b/README.md
index 1af21d3..a4b1cf1 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for bandit30 of bandit.
 ## credentials
 
 - username: bandit30
-- password: <no passwords in production!>
+- password: xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS
 

commit 081cefe55da9661fb5e31f8f3a3132398c27be31
Author: Ben Dover <noone@overthewire.org>
Date:   Wed Jan 11 19:18:54 2023 +0000

    add gif2ascii

diff --git a/code/gif2ascii.py b/code/gif2ascii.py
new file mode 100644
index 0000000..8b13789
--- /dev/null
+++ b/code/gif2ascii.py
@@ -0,0 +1 @@
+

commit 8159c819f4d37d9491254035c9e74ffcb316652e (origin/master, origin/HEAD, master)
Author: Ben Dover <noone@overthewire.org>
Date:   Wed Jan 11 19:18:54 2023 +0000

    fix username

diff --git a/README.md b/README.md
index 2da2f39..1af21d3 100644
:

```



-------


----------

password: xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS

----------

--------------------------------------

