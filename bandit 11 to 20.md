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

```
