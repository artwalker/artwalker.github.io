---
title: 15 Amending commits  
date: 2024-07-05 22:28:25 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ cd scripts/
$ touch auto-update.py
$ touch gather-information.sh
$ ls -l
```
## Code output:
```bash
total 8

-rwxrwxr-x 1 user user 319 Jul 16 17:56 all_checks.py

-rw-rw-r-- 1 user user   0 Jul 16 20:19 auto-update.py

-rw-rw-r-- 1 user user   0 Jul 16 20:19 gather-information.sh

-rw-rw-r-- 1 user user  15 Jul 16 18:03 output.txt

user@ubuntu:~/scripts$ git add auto-update.py 

user@ubuntu:~/scripts$ git commit -m 'Add two new scripts'

[master 9c78761] Add two new scripts

 1 file changed, 0 insertions(+), 0 deletions(-)

 create mode 100644 auto-update.py
```
## Command:
```bash
$ git add auto-update.py
$ git commit -m 'Add two new scripts'
```
## Code output:
```bash
# Please enter the commit message for your changes. Lines starting

# with '#' will be ignored, and an empty message aborts the commit.

#

# Date:      Tue Jul 16 20:20:24 2019 +0200

#

# On branch master

# Changes to be committed:

#       new file:   auto-update.py

#       new file:   gather-information.sh

#

# Untracked files:

#       output.txt

#
```
## Command:
```bash
$ git add gather-information.sh
$ git commit --amend
```
## Code output:
```bash
Add two new scripts.

# Please enter the commit message for your changes. Line starting
#with '#' will be ignored, and an empty message aborts the commit.
#
#Date: Mon Jan 6 08:28:17 2020 -0800
#
# On branch master
# Changes to be committed:
#	new file: auto-update.py
#	new file: gather-information.sh
#
# Untracked files:
#	output.txt
```
## Modify commit message:
```bash
Add two new scripts.

gather-information.sh will collect information in case of errors.
auto-update.py will run daily to update computers automatically.

# Please enter the commit message for your changes. Line starting
#with '#' will be ignored, and an empty message aborts the commit.
#
#Date: Mon Jan 6 08:28:17 2020 -0800
#
# On branch master
# Changes to be committed:
#	new file: auto-update.py
#	new file: gather-information.sh
#
# Untracked files:
#	output.txt
```
