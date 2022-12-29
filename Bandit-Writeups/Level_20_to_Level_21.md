## Level_20_to_Level_21

--------------------------------------



Level Goal
There is a setuid binary in the homedirectory that does the
following: it makes a connection to localhost on the port you
specify as a commandline argument. It then reads a line of text from
the connection and compares it to the password in the previous level
(bandit20). If the password is correct, it will transmit the
password for the next level (bandit21).
NOTE: Try connecting to your own network daemon to see if it
works as you think
Commands you may need to solve this level
ssh, nc, cat, bash, screen, tmux, Unix ‘job control’ (bg, fg, jobs, &, CTRL-Z, …)


-------
steps: 

```Bash
echo "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | ncat -lvp 61337 & ./suconnect 61337
[2] 146700
Ncat: Connection from 127.0.0.1.
Ncat: Connection from 127.0.0.1:34668.
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq

```

-------


----------

password: NvEJF7oVjkddltPSrdKEFOllh9V1IBcq

----------

--------------------------------------

