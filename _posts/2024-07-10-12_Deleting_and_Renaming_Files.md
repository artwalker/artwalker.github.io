---
title: 12 Deleting and Renaming Files  
date: 2024-07-05 22:28:29 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ cd checks/
$ ls -l
```
## Code output:
```bash
total 8

-rw-rw-r-- 1 user user 659 Jul  9 19:28 disk_usage.py

-rw-rw-r-- 1 user user 659 Jul 15 21:43 processes.py
```
## Command:
```bash
$ git rm process.py
```
## Code output:
```bash
rm 'processes.py'
```
## Command:
```bash
$ ls -l 
```
## Code output:
```bash
total 4

-rw-rw-r-- 1 user user 659 Jul  9 19:28 disk_usage.py
```
## Command:
```bash
$ git status
```
## Code output:
```bash
On branch master

Changes to be committed:

  (use "git reset HEAD <file>..." to unstage)

        deleted: processes.py
```
## Command:
```bash
$ git commit -m 'Delete unneeded processes file'
```
## Code output:
```bash
[master 9939311] Delete unneeded processes file

 1 file changed, 24 deletions(-)

 delete mode 100644 processes.py
```
## Command:
```bash
$ git mv disk_usage.py check_free_space.py
$ git status
```
## Code output:
```bash
On branch master

Changes to be committed:

  (use "git reset HEAD <file>..." to unstage)

        renamed:    disk_usage.py -> check_free_space.py
```
## Command:
```bash
$ git commit -m 'New name for disk_usage.py'
```
## Code output:
```bash
[master 7d7167b] New name for disk_usage.py

 1 file changed, 0 insertions(+), 0 deletions(-)
```
## Command:
```bash
$ echo .DS_STORE > .gitignore
$ ls -la
```
## Code output:
```bash
total 20

drwxrwxr-x  3 user user 4096 Jul 15 22:15 .

drwxr-xr-x 19 user user 4096 Jul 15 16:37 ..

-rw-rw-r--  1 user user  659 Jul  9 19:28 check_free_space.py

drwxrwxr-x  8 user user 4096 Jul 15 21:52 .git

-rw-rw-r--  1 user user   10 Jul 15 22:15 .gitignore
```
## Command:
```bash
$ git add .gitignore 
$ git commit -m 'Add a gitignore file, ignoring .DS_STORE files'
```
## Code output:
```bash
[master abb0632] Add a gitignore file, ignoring .DS_STORE files

 1 file changed, 1 insertion(+)

 create mode 100644 .gitignore
```
