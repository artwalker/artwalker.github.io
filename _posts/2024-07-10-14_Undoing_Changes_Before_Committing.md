---
title: 14 Undoing Changes Before Committing  
date: 2024-07-05 22:28:26 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ cd scripts
$ vim all_checks.py
```
## File with code:
```python
#!/usr/bin/env python3
  
import os
import sys

def main():
    if check_reboot():
        print("Pending Reboot.")
        sys.exit(1)

    print("Everything ok.")
    sys.exit(0)

main()
```
## Command:
```bash
$ ./all_checks.py 
```
## Code output:
```bash
Traceback (most recent call last):

  File "all_checks.py", line 14, in <module>

    main()

  File "all_checks.py", line 7, in main

    if check_reboot():

NameError: name 'check_reboot' is not defined
```
## Command:
```bash
$ git status
```
## Code output:
```bash
On branch master

Changes not staged for commit:

  (use "git add <file>..." to update what will be committed)

  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   all_checks.py
```
## Command:
```bash
$ git checkout all_checks.py
$ git status
```
## Code output:
```bash
On branch master

nothing to commit, working tree clean
```
## Command:
```bash
$ ./all_checks.py 
```
## Code output:
```bash
Everything ok.
```
## Command:
```bash
$ ./all_checks.py > output.txt
$ git add *
$ git status
```
## Code output:
```bash
On branch master

Changes to be committed:

  (use "git reset HEAD <file>..." to unstage)

        new file:   output.txt
```
## Command:
```bash
$ git reset HEAD output.txt
$ git status
```
## Code output:
```bash
On branch master

Untracked files:

  (use "git add <file>..." to include in what will be committed)

        Output.txt
```
## Command:
```bash
git commit -m "it should be os.path.exists"
```
