## Level_12_to_Level_13

--------------------------------------



Level Goal
The password for the next level is stored in the file data.txt,
which is a hexdump of a file that has been repeatedly compressed.
For this level it may be useful to create a directory under /tmp in
which you can work using mkdir. For example: mkdir /tmp/myname123.
Then copy the datafile using cp, and rename it using mv (read the
manpages!)
Commands you may need to solve this level
grep, sort, uniq, strings, base64, tr, tar, gzip, bzip2, xxd, mkdir,
cp, mv, file
Helpful Reading Material

Hex dump on Wikipedia



-------
steps: 

```bash 
hexdump -c 
hexdump -C 
```


We then turn the hexdump back into an actual file using xxd:

bandit12@bandit:/tmp/hackinganarchy$ cat data.txt.dump | xxd -r > data.txt

```Bash
bandit12@bandit:/tmp/hackinganarchy$ ls -la
total 305932
drwxr-sr-x 2 bandit12 root 4096 Jan 17 14:17 .OverTheWire “Bandit” Write-Up
drwxrws-wt 1 root root 313204736 Jan 17 14:17 ..
-rw-r--r-- 1 bandit12 root 605 Jan 17 14:17 data.txt
-rw-r----- 1 bandit12 root 2581 Jan 17 14:16 data.txt.dump

Reminder: > is the redirect operator. If we don’t specify a file descriptor (like “2” in Level 6),
it instead redirects the stdout – or Standard Output. If we specify a filename on the right
side of that operator, it gets redirected to that file.
Some notes: If you use >, a new file is created. So if you specify the name of an already
existing file, it gets overwritten. If you want to append instead, use >, so for example cat
data.txt.dump | xxd -r >> data.txt
The description tells us something about “compression”, though, so let’s find out how the
file has been compressed using file:
bandit12@bandit:/tmp/hackinganarchy$ file data.txt
data.txt: gzip compressed data, was "data2.bin", last modified: Tue Oct 16 12:00:23 2018,
max compression, from Unix
file gives us some information about a file, most importantly the filetype. We can see that
“data.txt” is the result of running a gzip-compression against a file called “data2.bin”. Let’s
retrieve that file using gunzip:

bandit12@bandit:/tmp/hackinganarchy$ gunzip data.txt
gzip: data.txt: unknown suffix -- ignored
Oh, yeah, right, gunzip requires the filename to end with “.gz” in order to work:

bandit12@bandit:/tmp/hackinganarchy$ mv data.txt data.txt.gz

bandit12@bandit:/tmp/hackinganarchy$ gunzip data.txt.gz
bandit12@bandit:/tmp/hackinganarchy$ ls -la
total 305932
drwxr-sr-x 2 bandit12 root 4096 Jan 17 14:25 .
drwxrws-wt 1 root root 313204736 Jan 17 14:25 ..OverTheWire “Bandit” Write-Up
-rw-r--r-- 1 bandit12 root 572 Jan 17 14:17 data.txt
-rw-r----- 1 bandit12 root 2581 Jan 17 14:16 data.txt.dump

If we call gunzip without any other parameters, it deletes the original file and the newly
created file is named similar to the input file, just without the “.gz” – meaning the result of
our decompression is “data.txt”.

bandit12@bandit:/tmp/hackinganarchy$ file data.txt
data.txt: bzip2 compressed data, block size = 900k
We still don’t have a text file though, just a bzip2-compressed file.
So let’s decompress that as well:

bandit12@bandit:/tmp/hackinganarchy$ bzip2 -d data.txt
bzip2: Can't guess original name for data.txt -- using data.txt.out
bandit12@bandit:/tmp/hackinganarchy$ file data.txt.out
data.txt.out: gzip compressed data, was "data4.bin", last modified: Tue Oct 16 12:00:23
2018, max compression, from Unix
Still not a text file, so let’s keep decompressing:

bandit12@bandit:/tmp/hackinganarchy$ mv data.txt.out data.txt.gz
bandit12@bandit:/tmp/hackinganarchy$ gunzip data.txt.gz

bandit12@bandit:/tmp/hackinganarchy$ file data.txt
data.txt: POSIX tar archive (GNU)
A new kind of compression, tar. Let’s unpack that as well:

bandit12@bandit:/tmp/hackinganarchy$ tar -xvf data.txt
data5.bin
bandit12@bandit:/tmp/hackinganarchy$ file data5.bin
data5.bin: POSIX tar archive (GNU)OverTheWire “Bandit” Write-Up
bandit12@bandit:/tmp/hackinganarchy$ tar -xvf data5.bin

data6.bin
bandit12@bandit:/tmp/hackinganarchy$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k

bandit12@bandit:/tmp/hackinganarchy$ bzip2 -d data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out
bandit12@bandit:/tmp/hackinganarchy$ file data6.bin.out
data6.bin.out: POSIX tar archive (GNU)

bandit12@bandit:/tmp/hackinganarchy$ tar -xvf data6.bin.out

data8.bin
bandit12@bandit:/tmp/hackinganarchy$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Tue Oct 16 12:00:23 2018,
max compression, from Unix

bandit12@bandit:/tmp/hackinganarchy$ mv data8.bin data.txt.gz
bandit12@bandit:/tmp/hackinganarchy$ gunzip data.txt.gz
gzip: data.txt already exists; do you wish to overwrite (y or n)? y
bandit12@bandit:/tmp/hackinganarchy$ file data.txt
data.txt: ASCII text
bandit12@bandit:/tmp/hackinganarchy$ cat data.txt


-------

$bandit12@bandit:/tmp/solved$ cat data.txt | xxd  -r > data.txt.gz
$bandit12@bandit:/tmp/solved$ gunzip data.txt.gz
    gzip: data.txt already exists; do you wish to overwrite (y or n)? y
$bandit12@bandit:/tmp/solved$ bzip2 -d data.txt
    bzip2: Can't guess original name for data.txt -- using data.txt.out
$bandit12@bandit:/tmp/solved$ mv data.txt.out data.txt.gz
$bandit12@bandit:/tmp/solved$ gunzip data.txt.gz 
$bandit12@bandit:/tmp/solved$ tar -xvf data.txt
    data5.bin
$bandit12@bandit:/tmp/solved$ tar -xvf data5.bin
    data6.bin
$bandit12@bandit:/tmp/solved$ bzip2 -d data6.bin
    bzip2: Can't guess original name for data6.bin -- using data6.bin.out
$bandit12@bandit:/tmp/solved$ tar -xvf data6.bin.out
    data8.bin
$bandit12@bandit:/tmp/solved$ mv data8.bin data.txt.gz
$bandit12@bandit:/tmp/solved$ gunzip data.txt.gz 
    gzip: data.txt already exists; do you wish to overwrite (y or n)? y
$bandit12@bandit:/tmp/solved$ cat data.txt
    The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

```
-------


----------

password: wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

----------

--------------------------------------

