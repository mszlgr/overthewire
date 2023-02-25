Almost all question instructions can (and need to) be found at [https://overthewire.org/wargames/bandit/bandit0.html](https://overthewire.org/wargames/bandit/bandit0.html)

0. 
`ssh bandit0@bandit.labs.overthewire.org -p 2220`, password `bandit0`
1. bandit0 -> bandit1
```
$ cat readme
NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
```
1. bandit1 -> bandit2
```
$ cat ./-
rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
```
1. bandit2 -> bandit3
```
$ cat spaces\ in\ this\ filename
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
```
1. bandit3 -> bandit4
```
$ cat inhere/.hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
```
1. bandit4 -> bandit5
```
$ cat $(file ./inhere/* | grep ASCII | cut -d':' -f1)
lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
```
1. bandit5 -> bandit6
```
$ cat $(find ./inhere/ -size 1033c)
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```
1. bandit6 -> bandit7
```
$ cat $(find / -size 33c -user bandit7 -group bandit6 2>/dev/null)
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```
1. bandit7 -> bandit8
```
$ cat data.txt | grep millionth | cut -f 2
TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```
1. bandit8 -> bandit9
```
$ cat data.txt | sort | uniq -c | grep '^ *1 '
      1 EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```
1. bandit9 -> bandit10
```
$ strings data.txt | grep ===
c========== the
h;========== password
========== isT
n.E========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```
1. bandit10 -> bandit11
```
$ cat data.txt | base64 -d
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```
1. bandit11 -> bandit12
```
$ cat data.txt | tr 'G-ZA-F' 'T-ZA-S' | tr 'g-za-f' 't-za-s'
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```
1. bandit12 -> bandit13
```
```
