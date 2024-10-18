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

```
