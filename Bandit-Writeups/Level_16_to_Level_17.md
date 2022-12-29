## Level_16_to_Level_17

--------------------------------------



Level Goal
The credentials for the next level can be retrieved by submitting the
password of the current level to a port on localhost in the range
31000 to 32000. First find out which of these ports have a server
listening on them. Then find out which of those speak SSL and which
don’t. There is only 1 server that will give the next credentials, the
others will simply send back to you whatever you send to it.
Commands you may need to solve this level
ssh, telnet, nc, openssl, s_client, nmap
Helpful Reading Material

Port scanner on Wikipedia



-------
steps: 


---

```Python
#!/bin/python
import socket
import threading
import time
  
# function to scan ports and see which ports are open
def scan_port(port):
    # we will check port of localhost
    host = "localhost"
    host_ip = socket.gethostbyname(host)
      
    # print("host_ip = {}".format(host_ip))
    status = False
  
    # create instance of socket
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
  
    # connecting the host ip address and port
    try:
        s.connect((host_ip, port))
        status = True
    except:
        status = False
  
    if status:
        print("port {} is open".format(port))

start_time = time.time()
  
for i in range(31000,32001):
    thread = threading.Thread(target=scan_port, args=[i])
    thread.start()
  
end_time = time.time()
print("To all scan all ports it took {} seconds".format(end_time-start_time))

```
---


```Bash
/tmp/portfinder/port_finder.py 
port 31046 is open
port 31518 is open
port 31691 is open
port 31790 is open
port 31960 is open
```

To all scan all ports it took 0.21129703521728516 seconds

from previous challenge: 

```Bash
echo "JQttfApK4SeyHwDlI9SXGR50qclOAil1" | openssl s_client -connect localhost:31046 -ign_eof ;
echo "JQttfApK4SeyHwDlI9SXGR50qclOAil1" | openssl s_client -connect localhost:31518 -ign_eof ;
echo "JQttfApK4SeyHwDlI9SXGR50qclOAil1" | openssl s_client -connect localhost:31691 -ign_eof ;
echo "JQttfApK4SeyHwDlI9SXGR50qclOAil1" | openssl s_client -connect localhost:31790 -ign_eof ;
echo "JQttfApK4SeyHwDlI9SXGR50qclOAil1" | openssl s_client -connect localhost:31960 -ign_eof ;

echo "JQttfApK4SeyHwDlI9SXGR50qclOAil1" | openssl s_client -connect localhost:31790 -ign_eof ;

echo "JQttfApK4SeyHwDlI9SXGR50qclOAil1" | openssl s_client -connect localhost:31790 -ign_eof ;
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Dec 15 17:27:57 2022 GMT
verify return:1
depth=0 CN = localhost
notAfter=Dec 15 17:27:57 2022 GMT
verify return:1
---
Certificate chain
 0 s:CN = localhost
   i:CN = localhost
   a:PKEY: rsaEncryption, 2048 (bit); sigalg: RSA-SHA1
   v:NotBefore: Dec 15 17:26:57 2022 GMT; NotAfter: Dec 15 17:27:57 2022 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDCzCCAfOgAwIBAgIEfkuw6zANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjIxMjE1MTcyNjU3WhcNMjIxMjE1MTcyNzU3WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQCh
LMX0D/Yz82CCwnOPFHvokeAF28h6fgF65Ymz6AYAfb1G5xKSaQJsQFRBxnosIpCp
Cspz+r+ZVt7Ge8INGIQidVs35NinoFz4bda9j9PuKmqcLLJE7WnlSpnCFLcmTXD2
f47bos1gMWFCuzsV7nSLwfYQovF/15+MtamMw/MCTnFeN9V7X0gDJiVdKLD5LMnh
i+XzUHYcq801YuxSNvgkbXENyiWVlVjZh8LG0V1ZyGS3u3HkNm25Ij6MV0SSkl1X
I7ZWRLYZmcw4thH2TRiH6WL9oBrSizdsVCqV1Rydmdg5nDUItgi7V7umBsF2kQsh
7Skgf+a8q32Zi544BWdfAgMBAAGjZTBjMBQGA1UdEQQNMAuCCWxvY2FsaG9zdDBL
BglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0ZWQgYnkgTmNhdC4g
U2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3DQEBBQUAA4IBAQAA
YXpAJEvlLxaqSV3B5WlhM66Dup/f97eGpqCw9sfOgtE/WuXRmlJ0LnN0m4mKZgDU
yneyGQj70+P2x5lxG+Y2MSuuE33HOidbXTITzwdfssuHzTGVsltIvH8CKLbyvXUy
FWgP5EzTWloO9p/KmORfKN4GMJIs4MF7bC7+ey6wJBnrPr0e3G3AkCCjpdcJKQQ0
HMOBnXzRcDU2/6Nupg10K8VUXlAmFHjebnv9sGTWklHAb+dxXwcUxvcb6WXcj0de
RaOEEycEqsCf804W2OiTLO9yTYQFKPtOYuHFI1dYBWcn6S0YASQTz+fWf2CW77x+
KJqsYx0nx707DXooVQpV
-----END CERTIFICATE-----
subject=CN = localhost
issuer=CN = localhost
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1339 bytes and written 373 bytes
Verification error: certificate has expired
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 2048 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 10 (certificate has expired)

---
---

Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: FE4600C36D8480379F13A54139DFB5E4E8C0C3FA4149983545F6219A588E49F7
    Session-ID-ctx: 
    Resumption PSK: 5D3A51BF8B4DD463CBC7EEF534FB646B8E540AEBC848AC15AA30482F905A6F1CDBEA0699001EFC66CB3498BAA12035E2
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 40 72 8f 4f 95 51 9f 42-34 77 e2 42 d6 ce 83 8f   @r.O.Q.B4w.B....
    0010 - 8c 9f 9b fc 26 40 98 ed-10 7d 4b 2d ec da 38 9b   ....&@...}K-..8.
    0020 - 89 5c 7e d5 38 d0 42 13-c7 44 0d b6 34 89 fc 90   .\~.8.B..D..4...
    0030 - d6 c8 fe 64 b1 7e 1f cb-7b 69 df 7f f1 89 28 6b   ...d.~..{i....(k
    0040 - a4 60 44 3e 81 04 4d f0-e8 a4 e8 9a 12 e5 9f ed   .`D>..M.........
    0050 - b4 5c 48 0b 61 56 c6 1c-0e 80 58 eb 67 79 f6 e5   .\H.aV....X.gy..
    0060 - ea 1e 2d 2d cf 19 9f ed-97 3e 5b 84 ff 2c 59 17   ..--.....>[..,Y.
    0070 - 94 36 ab 9d 61 35 dd 71-57 d1 bb 53 c7 71 51 82   .6..a5.qW..S.qQ.
    0080 - 70 b0 27 23 a1 ec 8e a5-c7 84 da 80 25 12 79 99   p.'#........%.y.
    0090 - 21 cd 82 ff 88 2f 13 64-99 77 b2 77 0b d8 46 11   !..../.d.w.w..F.
    00a0 - eb d6 48 b2 f0 14 7a cd-b6 35 ff e9 05 33 68 3f   ..H...z..5...3h?
    00b0 - fc 59 df 10 a4 3f fe 6e-26 ea 2d 81 e7 03 eb 19   .Y...?.n&.-.....
    00c0 - f6 af 52 3d 18 30 e9 de-a5 17 97 bc e6 0b 5a 02   ..R=.0........Z.

    Start Time: 1671127040
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0


---

read R BLOCK

---

Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: A1D0D0390635923FD05DC40F94BEA5080866BD345C496ABD9EAED4EDC1D4914C
    Session-ID-ctx: 
    Resumption PSK: 0B204A22208E039E2E54479130074F3FBCA5EE1C45B8B157BE61AD35506B565C8072F3763E07521D74BC9E383BCDC965
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 40 72 8f 4f 95 51 9f 42-34 77 e2 42 d6 ce 83 8f   @r.O.Q.B4w.B....
    0010 - 6e 05 54 99 cb 78 aa 4c-03 92 ec d5 7a f2 53 59   n.T..x.L....z.SY
    0020 - ee 7b 24 a1 23 47 83 8c-96 90 31 dd 97 fc 09 d9   .{$.#G....1.....
    0030 - 9b a0 39 de 08 b5 2a cf-82 75 53 74 0d 36 41 d3   ..9...*..uSt.6A.
    0040 - 0b 47 37 1f 9b 6f b7 27-3d fa fa 03 f5 3e 63 be   .G7..o.'=....>c.
    0050 - 74 23 91 07 34 07 fd 3e-90 6c ae f9 e9 2e 63 a1   t#..4..>.l....c.
    0060 - 67 8f d9 1f 88 b0 64 3b-fd 9c ac e9 8e 49 1c fd   g.....d;.....I..
    0070 - ad ee 4e 5b 16 f8 62 83-cf d6 ee 1d 6d 15 cb 03   ..N[..b.....m...
    0080 - 1a fb 30 21 90 09 34 c5-57 9e 70 a1 ea 3c d5 d3   ..0!..4.W.p..<..
    0090 - 4b a8 5e 1a 38 83 7a 81-70 fe f8 79 62 ad b4 0e   K.^.8.z.p..yb...
    00a0 - ab 02 d8 7d cf 71 1f 33-62 e1 4f 31 c3 63 19 59   ...}.q.3b.O1.c.Y
    00b0 - ef 48 39 1d fc 81 2f 88-81 e9 2d 5c 1b 66 f0 8c   .H9.../...-\.f..
    00c0 - 15 7d 2b 8c b6 4b 7c a0-c8 78 50 92 51 90 5d 10   .}+..K|..xP.Q.].

    Start Time: 1671127040
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
Correct!

-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

closed

```
so we save the private key as the bandit_level17 key .

```Bash
chmod 400 bandit_level17.key
ssh -i sshkey.private bandit14@localhost -p 2220
```

and then we can see the password for level 17
/etc/bandit_pass/bandit17

-------


----------

password: VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e

----------

--------------------------------------

