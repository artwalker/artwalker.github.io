---
title: 4 First steps with Git  
date: 2024-07-06 21:31:00 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ git config --global user.email "me@example.com"
$ git config --global user.name "My name"
$ mkdir checks
$ cd checks

# Initialized empty Git repository in `/home/user/checks/.git/`
$ git init

$ ls -la
```
## Code output:
```bash
total 12

drwxrwxr-x  3 user user 4096 Jul  9 18:16 .

drwxr-xr-x 18 user user 4096 Jul  9 18:16 ..

drwxrwxr-x  7 user user 4096 Jul  9 18:16 .git
```
## Command:
```bash
$ ls -l .git/
```
## Code output:
```bash
total 32

drwxrwxr-x 2 user user 4096 Jul  9 18:16 branches

-rw-rw-r-- 1 user user   92 Jul  9 18:16 config

-rw-rw-r-- 1 user user   73 Jul  9 18:16 description

-rw-rw-r-- 1 user user   23 Jul  9 18:16 HEAD

drwxrwxr-x 2 user user 4096 Jul  9 18:16 hooks

drwxrwxr-x 2 user user 4096 Jul  9 18:16 info

drwxrwxr-x 4 user user 4096 Jul  9 18:16 objects

drwxrwxr-x 4 user user 4096 Jul  9 18:16 refs
```
## Command:
```bash
$ cp ../disk_usage.py .
$ ls -l
```
## Code output:
```bash
-rw-rw-r-- 1 user user 657 Jul  9 18:26 disk_usage.py
```
## Command:
```bash
$ git add disk_usage.py 
$ git status
```
## Code output:
```bash
On branch master

No commits yet

Changes to be committed:

  (use "git rm --cached <file>..." to unstage)

	new file:   disk_usage.py
```
## Command:
```bash
$ git commit
```
## Code output:
```bash
 GNU nano 3.2         /home/user/checks/.git/COMMIT_EDITMSG                    

# Please enter the commit message for your changes. Lines starting

# with '#' will be ignored, and an empty message aborts the commit.

#

# On branch master

#

# Initial commit

#

# Changes to be committed:

#       new file:   disk_usage.py
```
