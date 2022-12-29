## Level_08_to_Level_09

--------------------------------------



Level Goal
The password for the next level is stored in the file data.txt
and is the only line of text that occurs only once
Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd
Helpful Reading Material

Piping and Redirection



-------
steps: 


python program 

```Python
python3
Python 3.10.6 (main, Nov  2 2022, 18:53:38) [GCC 11.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> ls = []
>>> s = set()
>>> with open('data.txt') as f:
...     for i in f:
...             if i in s:
...                     if i in ls:
...                             ls.remove(i)
...             else:
...                     s.add(i)
...                     ls.append(i)
... 
>>> print(ls)
['EN632PlfYiZbn3PhVK3XOGSlNInNE00t\n']
>>> 
```
-------



----------

password: EN632PlfYiZbn3PhVK3XOGSlNInNE00t

----------

--------------------------------------

