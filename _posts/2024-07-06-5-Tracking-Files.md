---
title: 5 Tracking Files  
date: 2024-07-06 21:30:00 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ cd checks
$ ls -l
```
## Code output:
```bash
total 4

-rw-r--r-- 1 user user 657 Jul  9 12:52 disk_usage.py
```
## Command:
```bash
$ git status
```
## Code output:
```bash
On branch master

nothing to commit, working tree clean
```
## Command:
```bash
$ vim disk_usage.py
$ git status
```
## Code output:
```bash
On branch master

Changes to be committed:

  (use "git restore --staged <file>..." to unstage)

	modified:   disk_usage.py
```
## Command:
```bash
$ git commit -m 'Add periods to the end of sentences.'
```
## Code output:
```bash
[master ae8d19c] Add periods to the end of sentences.

 1 file changed, 2 insertions(+), 2 deletions(-)
```
## Command:
```bash
$ git status
```
## Code output:
```bash
On branch master

nothing to commit, working tree clean
```
