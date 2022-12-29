Level_06_to_Level_07

--------------------------------------



Level Goal
The password for the next level is stored somewhere on the
server and has all of the following properties:

owned by user bandit7
owned by group bandit6
33 bytes in size

Commands you may need to solve this level
ls,cd,cat,file,du,find,grep


-------
steps: 

```Bash
find . -type f -size 33c -user bandit7 -group bandit6 -exec ls -lh {} \; | awk '{ print $9 ": " $5 }'


./var/lib/dpkg/info/bandit7.password: 33


cat /var/lib/dpkg/info/bandit7.password
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

```
-------


----------

password: z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

----------

--------------------------------------

