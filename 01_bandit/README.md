Almost all question instructions can (and need to) be found at [https://overthewire.org/wargames/bandit/bandit0.html](https://overthewire.org/wargames/bandit/bandit0.html)

0. 
`ssh bandit0@bandit.labs.overthewire.org -p 2220`, password `bandit0`
1. **bandit0 -> bandit1**
```
$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```
1. **bandit1 -> bandit2**
```
$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```
2. **bandit2 -> bandit3**
```
$ cat spaces\ in\ this\ filename
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```
3. **bandit3 -> bandit4**
```
$ cat inhere/.hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```
4. **bandit4 -> bandit5**
```
$ cat $(file ./inhere/* | grep ASCII | cut -d':' -f1)
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```
5. **bandit5 -> bandit6**
```
$ cat $(find ./inhere/ -size 1033c)
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```
6. **bandit6 -> bandit7**
```
$ cat $(find / -size 33c -user bandit7 -group bandit6 2>/dev/null)
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```
7. **bandit7 -> bandit8**
```
$ cat data.txt | grep millionth | cut -f 2
TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```
8. **bandit8 -> bandit9**
```
$ cat data.txt | sort | uniq -c | grep '^ *1 '
      1 EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```
9. **bandit9 -> bandit10**
```
$ strings data.txt | grep ===
c========== the
h;========== password
========== isT
n.E========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```
10. **bandit10 -> bandit11**
```
$ cat data.txt | base64 -d
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```
11. **bandit11 -> bandit12*8
```
$ cat data.txt | tr 'G-ZA-F' 'T-ZA-S' | tr 'g-za-f' 't-za-s'
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```
12. **bandit12 -> bandit13**
```
$ cat data.txt | xxd -r | file - ; cat data.txt | xxd -r | gunzip - | file - ; # and so on ...
/dev/stdin: gzip compressed data, was "data2.bin", last modified: Tue Feb 21 22:02:52 2023, max compression, from Unix
/dev/stdin: bzip2 compressed data, block size = 900k
$ cat data.txt | xxd -r | gunzip - | bzip2 -d | gunzip - | tar -xf- -O | tar -xf- -O | bzip2 -d | tar -xf- -O | gunzip -
The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
```
13. **bandit13 -> bandit14**
```
$ scp -P 2220 bandit13@bandit.labs.overthewire.org:~/sshkey.private ./ ; chmod 600 sshkey.private
$ ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```
14. **bandit14 -> bandit15**
```
$ cat /etc/bandit_pass/bandit14 | nc localhost 30000
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
```
15. **bandit15 -> bandit16**
```
$ cat /etc/bandit_pass/bandit15 | openssl s_client -connect  localhost:30001 -quiet 2>/dev/null
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```
16. **bandit16 -> bandit17**
```
$ for PORT in $(nmap localhost -p 31000-32000 | grep open | cut -d'/' -f1); 
    do cat /etc/bandit_pass/bandit16 | timeout 1 openssl s_client -connect  localhost:$PORT -quiet  2>/dev/null | grep -v $(cat /etc/bandit_pass/bandit16); 
  done
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
...
```
17. **bandit17 -> bandit18**
```
$ cat passwords.new | grep -v -f passwords.old
hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg    
```
18. **bandit18 -> bandit19**
```
ssh bandit18@bandit.labs.overthewire.org -p 2220 -- cat readme
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```
19. **bandit19 -> bandit20** Using executable with sticky bit set for bandit20 user 
```
$ ll bandit20-do ; ./bandit20-do cat /etc/bandit_pass/bandit20
-rwsr-x--- 1 bandit20 bandit19 14876 Feb 21 22:03 bandit20-do*
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
```
20. **bandit20 -> bandit21** 
```
$ cat /etc/bandit_pass/bandit20 | nc -l localhost 12345 & sleep 1; ./suconnect 12345
[1] 1444220
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
```
21. **bandit21 -> bandit22**
```
```
22. 
