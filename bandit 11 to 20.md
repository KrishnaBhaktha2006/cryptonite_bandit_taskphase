# Bandit 11 -> 12
## Code:
```bash
bandit11@bandit:~$ tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt
The password is 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4
```
# Learnings:
this is actually much harder than pwn.college this has a lot of functions to filter out files.Really too much to remember actually

# Bandit 12 -> 13
## Code:
```bash
bandit12@bandit:~$ cp data.txt /tmp/challenge
bandit12@bandit:~$ cd /tmp/challenge
bandit12@bandit:/tmp/challenge$ ls
binary_file.gz  compressed_data.txt  data  data.hexdump  data.txt  gzip_part
bandit12@bandit:/tmp/challenge$ xxd -r data.txt > data
bandit12@bandit:/tmp/challenge$ ls
binary_file.gz  compressed_data.txt  data  data.hexdump  data.txt  gzip_part
bandit12@bandit:/tmp/challenge$ rm binary_file.gz
bandit12@bandit:/tmp/challenge$ rm compressed_data.txt
bandit12@bandit:/tmp/challenge$ rm data.hexdump
bandit12@bandit:/tmp/challenge$ rm gzip_part
bandit12@bandit:/tmp/challenge$ ls
data  data.txt
bandit12@bandit:/tmp/challenge$ file data
data: gzip compressed data, was "data2.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 574
bandit12@bandit:/tmp/challenge$ mv data file.gz
bandit12@bandit:/tmp/challenge$ gzip -d file.gz
bandit12@bandit:/tmp/challenge$ ls
data.txt  file
bandit12@bandit:/tmp/challenge$ file file
file: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/challenge$ mv file file.bz2
bandit12@bandit:/tmp/challenge$ bzip2 -d file.bz2
bandit12@bandit:/tmp/challenge$ ls
data.txt  file
bandit12@bandit:/tmp/challenge$ file file
file: gzip compressed data, was "data4.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 20480
bandit12@bandit:/tmp/challenge$ mv file file.gz
bandit12@bandit:/tmp/challenge$ gzip -d file.gz
bandit12@bandit:/tmp/challenge$ ls
data.txt  file
bandit12@bandit:/tmp/challenge$ file file
file: POSIX tar archive (GNU)
bandit12@bandit:/tmp/challenge$ mv file file.tar
bandit12@bandit:/tmp/challenge$ tar xf file.tar
bandit12@bandit:/tmp/challenge$ ls
data5.bin  data.txt  file.tar
bandit12@bandit:/tmp/challenge$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/challenge$ rm data.txt
bandit12@bandit:/tmp/challenge$ rm file.tar
bandit12@bandit:/tmp/challenge$ ls
data5.bin
bandit12@bandit:/tmp/challenge$ mv data5.bin data.tar
bandit12@bandit:/tmp/challenge$ tar xf data.tar
bandit12@bandit:/tmp/challenge$ ls
data6.bin  data.tar
bandit12@bandit:/tmp/challenge$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/challenge$ mv data6.bin data.bz2
bandit12@bandit:/tmp/challenge$ bzip2 -d data.bz2
bandit12@bandit:/tmp/challenge$ ls
data  data.tar
bandit12@bandit:/tmp/challenge$ file data'
> ^C
bandit12@bandit:/tmp/challenge$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/challenge$ mv data data.tar
bandit12@bandit:/tmp/challenge$ ls
data.tar
bandit12@bandit:/tmp/challenge$ tar xf data.tar
bandit12@bandit:/tmp/challenge$ ls
data8.bin  data.tar
bandit12@bandit:/tmp/challenge$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Sep 19 07:08:15 2024, max compression, from Unix, original size modulo 2^32 49
bandit12@bandit:/tmp/challenge$ mv data8.bin data.gz
bandit12@bandit:/tmp/challenge$ gzip -d data.gz
bandit12@bandit:/tmp/challenge$ ls
data  data.tar
bandit12@bandit:/tmp/challenge$ file data
data: ASCII text
bandit12@bandit:/tmp/challenge$ cat data
The password is FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn
```
## Learnings:
this was a beautiful marvelous question first man all the things to get to know about it and then step by step go on doing eveything.

# Bandit 13 -> 14
## Code:
```bash
bandit13@bandit:~$ ls
sshkey.private
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost -p 2220
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit13/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit13/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

!!! You are trying to log into this SSH server with a password on port 2220 from localhost.
!!! Connecting from localhost is blocked to conserve resources.
!!! Please log out and log in again.


      ,----..            ,----,          .---.
     /   /   \         ,/   .`|         /. ./|
    /   .     :      ,`   .'  :     .--'.  ' ;
   .   /   ;.  \   ;    ;     /    /__./ \ : |
  .   ;   /  ` ; .'___,/    ,' .--'.  '   \' .
  ;   |  ; \ ; | |    :     | /___/ \ |    ' '
  |   :  | ; | ' ;    |.';  ; ;   \  \;      :
  .   |  ' ' ' : `----'  |  |  \   ;  `      |
  '   ;  \; /  |     '   :  ;   .   \    .\  ;
   \   \  ',  /      |   |  '    \   \   ' \ |
    ;   :    /       '   :  |     :   '  |--"
     \   \ .'        ;   |.'       \   \ ;
  www. `---` ver     '---' he       '---" ire.org


Welcome to OverTheWire!

If you find any problems, please report them to the #wargames channel on
discord or IRC.

--[ Playing the games ]--

  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!

--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.

--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)

--[ More information ]--

  For more information regarding individual wargames, visit
  http://www.overthewire.org/wargames/

  For support, questions or comments, contact us on discord or IRC.

  Enjoy your stay!

bandit14@bandit:~$
```

# Bandit 14 -> 15
## Code:
```bash
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
bandit14@bandit:~$ nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
Correct!
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
bandit14@bandit:~$ exit
logout
Connection to localhost closed.
bandit13@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```

# Bandit 15 -> 16
## Code:
```bash
bandit15@bandit:~$ pass=8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN = SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN = SnakeOil
verify return:1
---
Certificate chain
 0 s:CN = SnakeOil
   i:CN = SnakeOil
   a:PKEY: rsaEncryption, 4096 (bit); sigalg: RSA-SHA256
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN = SnakeOil
issuer=CN = SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: RSA-PSS
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 2103 bytes and written 373 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Server public key is 4096 bit
Secure Renegotiation IS NOT supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 9795876A745FE931E9ACEE0E228D95AF61A54C03C506AD79092399E313929F86
    Session-ID-ctx:
    Resumption PSK: 222F605533CCF0600E787D3020D27CF44AD774ED2E498542CD433E8E4907E3A800A5778F1C0FFFF8E467D0B2AF5D6B11
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - c0 c6 3d 9e 22 a9 6f a8-d6 08 ea 57 e8 ec 3e f7   ..=.".o....W..>.
    0010 - 76 4e 80 9a e8 c8 bf 43-fb a0 fd 26 c3 0f f7 4b   vN.....C...&...K
    0020 - 86 22 91 bf 52 36 2d 87-4a db bc c7 f6 05 a7 8f   ."..R6-.J.......
    0030 - a2 2d 57 5d 6a ef 82 ab-0c 6a 1e c6 5b 6d c3 f9   .-W]j....j..[m..
    0040 - 4d 39 b5 c1 46 73 ac fb-9b b4 55 88 bb ff 2f 15   M9..Fs....U.../.
    0050 - 4a 0c 7e d4 1b 7f ff 74-19 74 6a 44 05 29 39 00   J.~....t.tjD.)9.
    0060 - 25 d4 65 e4 14 c0 2b 2d-d6 0d 08 50 f3 05 5e 3e   %.e...+-...P..^>
    0070 - fa bf ae 87 8c fe 96 f2-95 e4 7c 94 4d 34 8e c6   ..........|.M4..
    0080 - ec 87 6f 31 da 1e 13 00-30 32 e6 53 9f 9d 3d 39   ..o1....02.S..=9
    0090 - e7 b5 34 67 11 6a 32 c9-fc ba 4e 90 e7 4e f7 9e   ..4g.j2...N..N..
    00a0 - 7e 5e 11 b4 2b 15 37 b1-f2 a7 28 1d a3 3f d3 e2   ~^..+.7...(..?..
    00b0 - 47 2a 87 ba dc cd 1b 29-b5 be 5a 4f e6 68 fb 58   G*.....)..ZO.h.X
    00c0 - 59 9b be fc c4 40 a7 67-ab 0b 81 5f 2f 9d 16 09   Y....@.g..._/...
    00d0 - ee fa 34 a5 0c ef 33 63-ec 1b b6 4e 5e 5a c9 ab   ..4...3c...N^Z..

    Start Time: 1729270750
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: C72FDFAA2FAFBB0D3D5110039B6E5DADB7FB7FF15126B878F0048A831E06C026
    Session-ID-ctx:
    Resumption PSK: 5ABAE676C86F685A67408A9E528C321D5EF48B7F11C05D864C4DDC6DE92009F7A1D8FE7266207E551202D8224192CD4F
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - c0 c6 3d 9e 22 a9 6f a8-d6 08 ea 57 e8 ec 3e f7   ..=.".o....W..>.
    0010 - 5e ed df d5 2a 8c ce 53-4d e5 b4 af d0 2d b4 78   ^...*..SM....-.x
    0020 - 5b 11 80 79 49 ea 29 1e-d7 07 d9 d9 63 55 e0 98   [..yI.).....cU..
    0030 - c1 43 fd 2b 04 a0 11 62-1a d3 a1 76 f9 7f cd 2d   .C.+...b...v...-
    0040 - 9f 75 16 71 9b 3f 44 ed-a3 a6 5f 2c 68 4b 03 50   .u.q.?D..._,hK.P
    0050 - 0a 75 63 ca 79 6e 1e 08-cf 97 e0 04 f0 1c f4 71   .uc.yn.........q
    0060 - c4 82 eb 02 df 45 d1 de-c8 44 7a 7d 68 12 44 0a   .....E...Dz}h.D.
    0070 - 30 a6 c9 08 5b ab 53 fd-a3 79 be 08 89 1c bd 82   0...[.S..y......
    0080 - 25 da 8f a8 45 c8 fe 94-94 f1 f8 50 f2 78 f3 ba   %...E......P.x..
    0090 - f7 20 a3 72 a3 50 38 56-bd 1d 57 6b 81 d7 c3 42   . .r.P8V..Wk...B
    00a0 - 96 50 7d d2 40 b4 c1 29-d9 f5 4e 32 0e 22 55 af   .P}.@..)..N2."U.
    00b0 - 01 91 20 b2 58 b5 87 87-eb b0 f7 66 fa 91 16 2e   .. .X......f....
    00c0 - 15 12 b8 3e 32 96 2a 73-c5 65 1b dc 89 3a e5 0c   ...>2.*s.e...:..
    00d0 - 45 fd e7 ed 6d 9d cb ca-c5 e2 56 3b c2 64 9d 54   E...m.....V;.d.T

    Start Time: 1729270750
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

closed
```
## Learnings:
i first time learnt how to use openssl

# Bandit 16 -> 17
## Code:
```bash

```
