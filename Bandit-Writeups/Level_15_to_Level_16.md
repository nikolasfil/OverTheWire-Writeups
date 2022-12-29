## Level_15_to_Level_16

--------------------------------------



Level Goal
The password for the next level can be retrieved by submitting the
password of the current level to port 30001 on localhost using
SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use
-ign_eof and read the “CONNECTED COMMANDS” section in the manpage.
Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of
that command…
Commands you may need to solve this level
ssh, telnet, nc, openssl, s_client, nmap
Helpful Reading Material

Secure Socket Layer/Transport Layer Security on Wikipedia
OpenSSL Cookbook - Testing with OpenSSL



-------
steps: 

```Bash
echo "jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt" | openssl s_client -connect localhost:30001 -ign_eof 


CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = localhost
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = localhost
verify error:num=10:certificate has expired
notAfter=Dec 14 04:49:45 2022 GMT
verify return:1
depth=0 CN = localhost
notAfter=Dec 14 04:49:45 2022 GMT
verify return:1
---
Certificate chain
 0 s:CN = localhost
   i:CN = localhost
   a:PKEY: rsaEncryption, 2048 (bit); sigalg: RSA-SHA1
   v:NotBefore: Dec 14 04:48:45 2022 GMT; NotAfter: Dec 14 04:49:45 2022 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIDCzCCAfOgAwIBAgIEL2w2qzANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjIxMjE0MDQ0ODQ1WhcNMjIxMjE0MDQ0OTQ1WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC/
AEWsokApldJe+l+3rTnUTTrzHNUiLVf5xiXGZQXZKUf6X1PtKBrwc6zdsHEX2FM1
a9K2DDYK/dr/G4ooU1n1CEeLMClflTEA6fJ5o5OBSsYR6WK0W/TQt7P4Ypwh9VYF
UmvFplgIDuSoO7BLD0xpf8ubWD1FQ02yH1STqKC/P5/Td0t6IoddMhNRTBhPjmv8
ccdecSXm1iTnjYoGAaBI8Vksgzam9FXOYyommodkywe8SDlFjYeicjt4k4bT4kps
yzIJ8hPeUufkJCJGtqF6g51gwO01eaAw3JTPh7jL9KtTHOtf7gGAqbdHzDPnIn3h
FrZU830mfv1Sum3+/vdhAgMBAAGjZTBjMBQGA1UdEQQNMAuCCWxvY2FsaG9zdDBL
BglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0ZWQgYnkgTmNhdC4g
U2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3DQEBBQUAA4IBAQCo
HptSZcS/ZT+p8nsBOkDjgAcPqkIjOE/gKINXNh4My3iJROoysBzc5mcSxwLX6+ea
EE0bQYZ82bpRhuknZliDcaQb7dR/VlY28YlWUXRurN+j6vU6xPTOxu4BiRADOors
Cgf6CLUK5LD6cr37ONGL/F9E6ey8kKyMp2Y3JWL7oUPIzPMxmXLPvOVESDAHJWu7
bmojHithq2UXJMgTbRedXUDqtt8J7jAvXMPIp3ls/83SQ4NIoNR89Xk1m2MSZ8CE
vWeYnDKy2Hlbt8+/MrbR+AfwrmRRth1qEPbq89GoWIfJoQDYldsyWhtQg7UHRFLI
5dn0fM6CT9pTcsIlck3T
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
    Session-ID: 268DE26D5FC870A57334FA4861FF206E3318B2403E5D32D4D05985FA44620354
    Session-ID-ctx: 
    Resumption PSK: FF549D504C9724CB9B355A40A0F3BB44277F8D4FCB9577CFA14AE5F520B2A3F8BEE6080B89AE9314CB3DE97B9005F6D1
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - ad c3 44 45 93 1b c7 b4-c9 09 ba 56 3a ab 2f 05   ..DE.......V:./.
    0010 - b8 31 4d d2 bb 1c ee 93-c3 52 0e fb d7 d5 aa bc   .1M......R......
    0020 - d7 39 ca 46 03 6e 89 05-f3 1d 88 20 34 c6 24 d0   .9.F.n..... 4.$.
    0030 - bb 68 c3 25 48 de 60 96-d2 5b 8e e8 b7 ce 0c 06   .h.%H.`..[......
    0040 - 7f 52 95 9b aa 27 e7 a5-83 6b df 3d 71 c7 a0 64   .R...'...k.=q..d
    0050 - 7c 54 ae 68 fa 87 b0 75-1e f7 40 eb 1f 9d 00 39   |T.h...u..@....9
    0060 - f8 ca 09 00 74 bd ac c1-14 de 4a f9 2e 24 11 84   ....t.....J..$..
    0070 - bd ad 01 ee 2c de 97 a4-06 d0 a2 63 09 ea 0b 27   ....,......c...'
    0080 - 75 76 83 9b e7 ba 1f 75-53 0f 6f f2 bd c5 12 5f   uv.....uS.o...._
    0090 - e5 c8 aa 68 0a eb 86 1d-3a f6 59 9e ea 83 d8 97   ...h....:.Y.....
    00a0 - 54 cf 1f e0 03 45 d4 03-08 8d 66 69 11 d0 58 c3   T....E....fi..X.
    00b0 - 97 b4 b0 45 48 99 be f2-43 17 ad 26 f8 ce be e7   ...EH...C..&....
    00c0 - 2e 5b 64 0e 98 aa 01 ba-10 9f 30 ec a4 f4 a7 ed   .[d.......0.....

    Start Time: 1671018283
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
    Session-ID: 1B14EFDAEF2CD627070A063FFE2D2E1F264985A91D7F81BF668CBB259DFA6ED1
    Session-ID-ctx: 
    Resumption PSK: 33BA8F5FE93DCED4EEB8E3B16A8B3182AFFECB38764031B22C0F3A48868829D7FCF6844E7DE74B03C55DD66217B850D2
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - ad c3 44 45 93 1b c7 b4-c9 09 ba 56 3a ab 2f 05   ..DE.......V:./.
    0010 - cd 1e 8d 52 18 fa d3 cc-f3 f7 d8 84 24 59 78 76   ...R........$Yxv
    0020 - 05 02 a1 55 12 a9 41 28-09 e7 1b ae 96 41 ab a9   ...U..A(.....A..
    0030 - 7b 70 15 21 06 31 2a 43-84 6c bb f6 ca 38 32 ac   {p.!.1*C.l...82.
    0040 - 20 d2 56 35 e2 bc 49 d8-df 81 c7 fa 4c 34 5d 10    .V5..I.....L4].
    0050 - 70 a6 23 75 7b 21 6a 53-c6 cd 3c 30 da 09 8c 49   p.#u{!jS..<0...I
    0060 - 50 4a d7 35 e4 0c 39 7d-5a b0 ab 36 3c f0 2b 5c   PJ.5..9}Z..6<.+\
    0070 - 76 36 61 3b f2 0d b1 38-37 6a 7b 49 36 03 4a 93   v6a;...87j{I6.J.
    0080 - 3c 2e b0 fd 36 bf f0 30-bb 3d c4 e8 fa 26 66 c6   <...6..0.=...&f.
    0090 - 42 a3 08 f3 fb 00 a5 2f-5f 92 a3 e6 ae 14 69 74   B....../_.....it
    00a0 - 40 05 1d 54 43 da 7a dd-1d 78 83 83 cc 36 ef 23   @..TC.z..x...6.#
    00b0 - 9f f5 e8 fe 3a 42 b7 f6-f0 98 37 51 e9 55 11 2f   ....:B....7Q.U./
    00c0 - fa 32 76 ea a1 f3 fa 92-20 68 c6 71 1e be 05 e1   .2v..... h.q....

    Start Time: 1671018283
    Timeout   : 7200 (sec)
    Verify return code: 10 (certificate has expired)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1

closed
```
-------


----------
password: JQttfApK4SeyHwDlI9SXGR50qclOAil1
----------

--------------------------------------

