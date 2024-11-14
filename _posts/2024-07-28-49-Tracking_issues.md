---  
title: 49 Tracking issues  
date: 2024-07-04 22:27:50 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command
```bash
$ cd health-checks/
$ vim README.md
```

## Modify file
```bash
# health-checks

This repo will be populated with lots of fancy checks. 

Currently the main script is health_checks.py

This script will print "Everything ok" if all checks pass, 
or the corresponding error messages if some checks fail.
```
## Command
```bash
$ git commit -a
```

## Edit message
```bash
Update README to use the new name of the script

Also add more information about how this works. 
Closes #1
(...)
```

## Code output
```bash
[master 8981efe] Update README to use the new name of the script

 1 file changed, 4 insertions(+), 1 deletion(-)
```

## Command
```bash
$ git push
```
## COde output
```bash
Username for 'https://github.com': artwalker

Password for 'https://artwalker@github.com': 

Enumerating objects: 5, done.

Counting objects: 100% (5/5), done.

Delta compression using up to 2 threads

Compressing objects: 100% (3/3), done.

Writing objects: 100% (3/3), 564 bytes | 564.00 KiB/s, done.

Total 3 (delta 0), reused 0 (delta 0)

To https://github.com/artwalker/health-checks.git

   160b5f3..8981efe  master -> master
```
