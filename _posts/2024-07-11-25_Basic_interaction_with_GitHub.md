---
title: 25 Basic interaction with GitHub  
date: 2024-07-04 22:28:13 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command
```bash
$ git clone https://github.com/artwalker/health-checks.git
```
## Code output
```bash
Cloning into 'health-checks'...

Username for 'https://github.com': redquinoa

Password for 'https://redquinoa@github.com': 

remote: Enumerating objects: 3, done.

remote: Counting objects: 100% (3/3), done.

remote: Compressing objects: 100% (2/2), done.

remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0

Unpacking objects: 100% (3/3), done.
```
## Command
```bash
$ cd health-checks/
$ ls -l
```
## Code output
```bash
total 4

-rw-rw-r-- 1 user user 62 Jan  6 14:06 README.md
```
## Command
```bash
$ vim README.md
```
## Modify file content
```bash
# health-checks
Scripts that check the health of my computers

This repo will be populated with lots of fancy checks. 
```
## Command
```bash
$ git commit -a -m "Add one more line to README.md"
```
## Code output
```bash
[master 807cb50] Add one more line to README.md

 1 file changed, 2 insertions(+)
```
## Command
```bash
$ git push
```
## Code output
```bash
Username for 'https://github.com': redquinoa

Password for 'https://redquinoa@github.com': 

Enumerating objects: 5, done.

Counting objects: 100% (5/5), done.

Delta compression using up to 4 threads

Compressing objects: 100% (2/2), done.

Writing objects: 100% (3/3), 347 bytes | 347.00 KiB/s, done.

Total 3 (delta 0), reused 0 (delta 0)

To https://github.com/redquinoa/health-checks.git

   3d9f86c..807cb50  master -> master
```
## Command
```bash
$ git config --global credential.helper cache
$ git pull
```
## Code output
```bash
Username for 'https://github.com': artwalker

Password for 'https://redquinoa@github.com': 

Already up to date.
```
## Command
```bash
git pull
```
## Code output
```bash
Already up to date.
```
