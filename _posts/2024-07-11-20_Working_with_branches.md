---
title: 20 Working with branches  
date: 2024-07-04 22:28:18 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ cd checks
$ git status
```
## Code output:
```bash
On branch even-better-feature

nothing to commit, working tree clean
```
## Command:
```bash
$ ls -l
```
## Code output:
```bash
total 8

-rw-rw-r-- 1 user user 659 Jul 17 00:02 disk_usage.py

-rw-rw-r-- 1 user user  53 Jul 17 15:33 free_memory.py
```
## Command:
```bash
$ git checkout master
```
## Code output:
```bash
Switched to branch 'master'
```
## Command:
```bash
$ git log -2
```
## Code output:
```bash
commit 80b2dacef4b567196e61651064f03089c5e70b5e (HEAD -> master, new-feature)

Author: artwalker <artwalker@example.com>

Date:   Wed Jul 17 00:02:39 2019 +0200

    Revert "New name for disk_usage.py"

    

    Rollback reason: the previous name was actually better.

    

    This reverts commit 7d7167b2db44abf8cf014230f9b9708786e41c2a.

commit abb063210c1f011b0d6470a4c5f1d8f672edd3ef

Author: artwalker <artwalker@example.com>

Date:   Mon Jul 15 22:20:45 2019 +0200

    Add a gitignore file, ignoring .DS_STORE files
```
## Command:
```bash
$ ls -l
```
## Code output:
```bash
total 4

-rw-rw-r-- 1 user user 659 Jul 17 00:02 disk_usage.py
```
## Command:
```bash
$ git branch
```
## Code output:
```bash
 even-better-feature

* master

  new-feature
```
## Command:
```bash
$ git branch -d new-feature 
```
## Code output:
```bash
Deleted branch new-feature (was 80b2dac).
```
## Command:
```bash
$ git branch
```
## Code output:
```bash
  even-better-feature

* master
```
## Command:
```bash
$ git branch -d even-better-feature 
```
## Code output:
```bash
error: The branch 'even-better-feature' is not fully merged.

If you are sure you want to delete it, run 'git branch -D even-better-feature'.
```
