# Bandit 0
## Code:
```bash
shrikrishna_bhaktha@Krish:~$ ssh bandit0@bandit.labs.overthewire.org -p 2220
The authenticity of host '[bandit.labs.overthewire.org]:2220 ([16.16.163.126]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[bandit.labs.overthewire.org]:2220' (ED25519) to the list of known hosts.
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit0@bandit.labs.overthewire.org's password:

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

```
## Learnings:
i got to learn how to connect using ssh keys 

# Bandit 0 -> 1
## Code:
```bash
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

bandit0@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.
```
## Learnings:
i leanrt that we need to note down all the passwords.

# Bandit 1 -> 2
## Code:
```bash
bandit1@bandit:~$ ls -
-
bandit1@bandit:~$ cat ./-
263JGJPfgU6LtdEvgfWU1XP5yac29mFx
```

# Bandit 2 -> 3
## Code:
```bash
bandit2@bandit:~$ cat "spaces in this filename"
MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx
```

# Bandit 3 -> 4
## Code:
```bash
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls
bandit3@bandit:~/inhere$ ls -a
.  ..  ...Hiding-From-You
bandit3@bandit:~/inhere$ cat ...Hiding-From-You
2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
```

# Bandit 4 -> 5
## Code:
```bash
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ ls -l
total 40
-rw-r----- 1 bandit5 bandit4 33 Sep 19 07:08 -file00
-rw-r----- 1 bandit5 bandit4 33 Sep 19 07:08 -file01
-rw-r----- 1 bandit5 bandit4 33 Sep 19 07:08 -file02
-rw-r----- 1 bandit5 bandit4 33 Sep 19 07:08 -file03
-rw-r----- 1 bandit5 bandit4 33 Sep 19 07:08 -file04
-rw-r----- 1 bandit5 bandit4 33 Sep 19 07:08 -file05
-rw-r----- 1 bandit5 bandit4 33 Sep 19 07:08 -file06
-rw-r----- 1 bandit5 bandit4 33 Sep 19 07:08 -file07
-rw-r----- 1 bandit5 bandit4 33 Sep 19 07:08 -file08
-rw-r----- 1 bandit5 bandit4 33 Sep 19 07:08 -file09
bandit4@bandit:~/inhere$ cat -file00
cat: invalid option -- 'f'
Try 'cat --help' for more information.
bandit4@bandit:~/inhere$ cat -- -file00
�p��&�y�,�(jo�.at�:uf�^���@bandit4@bandit:~/inhere$ cat -- -file01
i�R�,�Λ�:Y���?�%�A����B��ͩ�bandit4@bandit:~/inhere$ cat -- -file02
3�      �)Ʈ�#Y��-6c��IR-�$����:��bandit4@bandit:~/inhere$ cat -- -file03
���/�
     ������qGi��,�2�Yb�
dbandit4@bandit:~/inhere$ cat -- -file04
ۙ�rOx����h0~ey
��c�~�h�n��G1bandit4@bandit:~/inhere$ cat -- -file05
}���ߓ��ߤ��W>��#lk�d�ܮ��yE��bandit4@bandit:~/inhere$ cat -- -file06
6�0]�\�$�1�%�������o@��b/��bandit4@bandit:~/inhere$ cat -- -file07
4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw
```

# Bandit 5 -> 6
## Code:
```bash
bandit5@bandit:~$ find inhere -type f -size 1033c ! -executable -exec file {} \; | grep 'ASCII text'
inhere/maybehere07/.file2: ASCII text, with very long lines (1000)
bandit5@bandit:~$ cd inhere/maybehere07
bandit5@bandit:~/inhere/maybehere07$ ls -l
total 36
-rwxr-x--- 1 root bandit5 3663 Sep 19 07:08 -file1
-rw-r----- 1 root bandit5 2488 Sep 19 07:08 -file2
-rwxr-x--- 1 root bandit5 3362 Sep 19 07:08 -file3
-rwxr-x--- 1 root bandit5 4130 Sep 19 07:08 spaces file1
-rw-r----- 1 root bandit5 9064 Sep 19 07:08 spaces file2
-rwxr-x--- 1 root bandit5 1022 Sep 19 07:08 spaces file3
bandit5@bandit:~/inhere/maybehere07$ ls -a
.  ..  -file1  .file1  -file2  .file2  -file3  .file3  spaces file1  spaces file2  spaces file3
bandit5@bandit:~/inhere/maybehere07$ cat .file2
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
```
## Learnings:
i got an idea about how to search for files of certain specifications according to our requirement.

# Bandit 6 -> 7
## Code:
```bash
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c
find: ‘/drifter/drifter14_src/axTLS’: Permission denied
find: ‘/root’: Permission denied
find: ‘/snap’: Permission denied
find: ‘/tmp’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/121798/task/121798/fd/6’: No such file or directory
find: ‘/proc/121798/task/121798/fdinfo/6’: No such file or directory
find: ‘/proc/121798/fd/5’: No such file or directory
find: ‘/proc/121798/fdinfo/5’: No such file or directory
find: ‘/home/bandit31-git’: Permission denied
find: ‘/home/ubuntu’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/drifter8/chroot’: Permission denied
find: ‘/home/drifter6/data’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/lost+found’: Permission denied
find: ‘/etc/polkit-1/rules.d’: Permission denied
find: ‘/etc/multipath’: Permission denied
find: ‘/etc/stunnel’: Permission denied
find: ‘/etc/xinetd.d’: Permission denied
find: ‘/etc/credstore.encrypted’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/etc/sudoers.d’: Permission denied
find: ‘/etc/credstore’: Permission denied
find: ‘/dev/shm’: Permission denied
find: ‘/dev/mqueue’: Permission denied
find: ‘/var/log/amazon’: Permission denied
find: ‘/var/log/unattended-upgrades’: Permission denied
find: ‘/var/log/chrony’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/tmp’: Permission denied
find: ‘/var/spool/cron/crontabs’: Permission denied
find: ‘/var/spool/bandit24’: Permission denied
find: ‘/var/spool/rsyslog’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/pollinate’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/cache/apparmor/2425d902.0’: Permission denied
find: ‘/var/cache/apparmor/baad73a1.0’: Permission denied
find: ‘/var/lib/polkit-1’: Permission denied
find: ‘/var/lib/amazon’: Permission denied
/var/lib/dpkg/info/bandit7.password
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/chrony’: Permission denied
find: ‘/var/lib/snapd/void’: Permission denied
find: ‘/var/lib/snapd/cookie’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/update-notifier/package-data-downloads/partial’: Permission denied
find: ‘/var/lib/udisks2’: Permission denied
find: ‘/var/crash’: Permission denied
find: ‘/boot/efi’: Permission denied
find: ‘/boot/lost+found’: Permission denied
find: ‘/sys/kernel/tracing’: Permission denied
find: ‘/sys/kernel/debug’: Permission denied
find: ‘/sys/fs/pstore’: Permission denied
find: ‘/sys/fs/bpf’: Permission denied
find: ‘/run/lock/lvm’: Permission denied
find: ‘/run/systemd/inaccessible/dir’: Permission denied
find: ‘/run/systemd/propagate/systemd-udevd.service’: Permission denied
find: ‘/run/systemd/propagate/systemd-resolved.service’: Permission denied
find: ‘/run/systemd/propagate/systemd-networkd.service’: Permission denied
find: ‘/run/systemd/propagate/irqbalance.service’: Permission denied
find: ‘/run/systemd/propagate/systemd-logind.service’: Permission denied
find: ‘/run/systemd/propagate/chrony.service’: Permission denied
find: ‘/run/systemd/propagate/polkit.service’: Permission denied
find: ‘/run/systemd/propagate/ModemManager.service’: Permission denied
find: ‘/run/systemd/propagate/fwupd.service’: Permission denied
find: ‘/run/systemd/propagate/bolt.service’: Permission denied
find: ‘/run/lvm’: Permission denied
find: ‘/run/log/journal/ec2dd69f90c4a6285216f71caca9bbca’: Permission denied
find: ‘/run/cryptsetup’: Permission denied
find: ‘/run/multipath’: Permission denied
find: ‘/run/screen/S-bandit20’: Permission denied
find: ‘/run/screen/S-bandit27’: Permission denied
find: ‘/run/screen/S-bandit28’: Permission denied
find: ‘/run/screen/S-bandit24’: Permission denied
find: ‘/run/screen/S-bandit17’: Permission denied
find: ‘/run/screen/S-bandit12’: Permission denied
find: ‘/run/screen/S-bandit29’: Permission denied
find: ‘/run/screen/S-bandit23’: Permission denied
find: ‘/run/screen/S-bandit1’: Permission denied
find: ‘/run/screen/S-bandit31’: Permission denied
find: ‘/run/screen/S-bandit21’: Permission denied
find: ‘/run/screen/S-bandit22’: Permission denied
find: ‘/run/screen/S-bandit19’: Permission denied
find: ‘/run/screen/S-bandit30’: Permission denied
find: ‘/run/screen/S-bandit33’: Permission denied
find: ‘/run/screen/S-bandit25’: Permission denied
find: ‘/run/screen/S-bandit16’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/run/user/11000’: Permission denied
find: ‘/run/user/11012’: Permission denied
find: ‘/run/user/11001’: Permission denied
find: ‘/run/user/11013’: Permission denied
find: ‘/run/user/11023’: Permission denied
find: ‘/run/user/11016’: Permission denied
find: ‘/run/user/11028’: Permission denied
find: ‘/run/user/11024’: Permission denied
find: ‘/run/user/11027’: Permission denied
find: ‘/run/user/11005’: Permission denied
find: ‘/run/user/11015’: Permission denied
find: ‘/run/user/11003’: Permission denied
find: ‘/run/user/11020’: Permission denied
find: ‘/run/user/11004’: Permission denied
find: ‘/run/user/11032’: Permission denied
find: ‘/run/user/11025’: Permission denied
find: ‘/run/user/11018’: Permission denied
find: ‘/run/user/11009’: Permission denied
find: ‘/run/user/11006/systemd/inaccessible/dir’: Permission denied
find: ‘/run/user/11002’: Permission denied
find: ‘/run/user/11022’: Permission denied
find: ‘/run/user/11017’: Permission denied
find: ‘/run/user/11010’: Permission denied
find: ‘/run/user/11014’: Permission denied
find: ‘/run/user/11011’: Permission denied
find: ‘/run/user/11007’: Permission denied
find: ‘/run/user/11026’: Permission denied
find: ‘/run/user/11019’: Permission denied
find: ‘/run/user/11008’: Permission denied
find: ‘/run/user/11031’: Permission denied
find: ‘/run/user/11021’: Permission denied
find: ‘/run/user/11029’: Permission denied
find: ‘/run/user/8003’: Permission denied
find: ‘/run/chrony’: Permission denied
find: ‘/run/udisks2’: Permission denied
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
```
## Learnings:
i learnt how to serach for files in servers acc to thier perceiving permissions.

# Bandit 7 -> 8
## Code:
```bash
bandit7@bandit:~$ grep millionth data.txt
millionth       dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc
```

# Bandit 8 -> 9
## Code:
```bash
bandit8@bandit:~$ sort data.txt | uniq -u
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
```
## Learnings:
I understood how to search for files having no repeated lines

# Bandit 9 -> 10
## Code:
```bash

bandit9@bandit:~$ strings data.txt | grep '^=*'
h!]v
r>)1
v0i)b
B:PyZ
#0/u
dyaE
F#X[
7$'0'T
^^^K
Y5}|
9g_$
^h#%EG
        Fq/
/OZ[4'
D#?P
POl%
}========== the
db*Nz
cc5M
`oaT
E:zr0
!S:%_
yG@q-
-c5N
xHp\
wS>n
^B~9
Q!vw
'5jl
. \,
66exg
h^Ad
,`Cd80
UB;N
U@j?
p\l=
te24
UNvlE
U%^6
JB]H:|v
|M '
{QMrWv
8:%     XD
H"hU
/uP_
(mhY
+6,hH
4vjm4
q09B
^8NSs
2>X)
Y>v4
lKUO
U>QkM:,V
imZ?L
>^?X
;c<Q=.dEXU!
j!ZL
jX09
5bBK
4Rl_7gH
F 4Cq
#61QW
hqI.X
3JprD========== passwordi
7`4(WG
& `T
_eOdY
G>Wu}
o|)s
z_b^
HCg\@0
z8N_-Z`
v7\y
s>|5
!$L&
Qm1U
JH|)
qi{|p
Yy6]
BWu7
qC(=
"t<2-u
i)W5
Czmnf&v
TO"'
~fDV3========== is
R<+{
)DtZ
)>tgdu
FvkY
Z)w,
|:H5
I;j@
0V[1
d_hnA;
oH`w
7=oc
_N]d
3>\kGG
drfx
}UQB
uP6{
hu%lLj
F>x!&
[^?_
M<ls%
"kz8I
zP=
6o+u
piUv
a*xX$
%!~D
xfvO
Oq.g
(p^A
-45c
^w#K
FP&!
ba+D
n.i3m
GMKB
#s}t
K>]`c
sn)>
v8jB
"x|L
}ZIg
r~rB
+_38
Z@bj:
~de=
.sjd
        qT\
>T`q
Ylyg<
t1QAk
@99F
oxGz$W~"
9+`1
_$>S
J]epm
pfT8
I`8l
fL'~_
a       Z
DT[N
z9wo
5Gfy
"}@>bn
O(k$N
zw[@
!a5^
9Z8]
sqEAj
D)A'r
an      g
'3pp(
s(-Qv
3k=fQ
usTR
Nyz3wI
+)&_i
WDp8
u"o~
p(67
WZ+(
?o&g
k        `
~o=0
6+$N
:'3z
uJw&
&kIIJ
b4glu
]NJR
 %uW
|r_s
zVw-
Q$QBW
Q{h%w
69}=
?uPsH
@WG|
%"=Y
Pew%J
&3[2
*u;(%P
dA`d
|>,p
oY%\
3W`j
D+io?
=tZ~07
^6Og
Tx+X
rs2J
 -M8<
Dq^B
Qv"Y
fk)B
g+;Y
 Uum
D9========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
u1Ebi
&x(>G
.`EQ
w>}x
D%(f
1#4!9
:79(
m!}B
| Zd
qQ>Gu
!6D(
J?,2
IEO*
uu>@    ;
KrQ!
$V8a
{vl0pup
AWwyxY
j(ue
X<'j
<HR]/
7!`tcT7
Gp(2
FoOvx
hF|W
3edvE%
_#@k
N=~[!N
-VSe
a0XJ
3;8_
zA=?0j
b}M>s
%Xi-
Qobt
6Cjk
H`U     ^
+v J
4(clh~U
#R^g
Xgz|
)oRj
bandit9@bandit:~$
```
# Learnings:
I learnt how to find files having beginning lines with =.

# Bandit 10 -> 11
## Code:
```bash
bandit10@bandit:~$ cat data.txt | base64 -d
The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
```
## Learnings:
i learnt how to use base64 to decode using terminal.
