---
title: 6 The Basic Git Workflow  
date: 2024-07-06 21:29:00 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ mkdir scripts
$ cd scripts
$ git init
```
## Code output:
```bash
Initialized empty Git repository in /home/user/scripts/.git/
```
## Command:
```bash
$ git config -l
```
## Code output:
```bash
user.email=artwalker@example.com

user.name=artwalker

core.repositoryformatversion=0

core.filemode=true

core.bare=false

core.logallrefupdates=true
```
## File with code:
```python
#!/usr/bin/env python3

def main():
    pass

main()

```
## Command:
```bash
$ chmod +x all_checks.py
$ git status
```
## Code output:
```bash
On branch master

No commits yet

Untracked files:

  (use "git add <file>..." to include in what will be committed)

	all_checks.py

nothing added to commit but untracked files present (use "git add" to track)
```
## Command:
```bash
$ git add all_checks.py
$ git commit
```
## Code output:
```bash
Create an empty all_checks.
# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
#
# Initial commit
#
# Changes to be committed:
#       new file:   all_checks.py
#

```
## File with code:
```python
#!/usr/bin/env python3

import os

def check_reboot():
    """Returns True if the computer has a pending reboot."""
    return os.path.exists("/run/reboot-required")	

def main():
    pass

main()

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

no changes added to commit (use "git add" and/or "git commit -a")
```
## Command:
```bash
$ git add all_checks.py 
$ git status
```
## Code output:
```bash
On branch master

Changes to be committed:

  (use "git reset HEAD <file>..." to unstage)

	modified:   all_checks.py
```
## Command:
```bash
$ git commit -m 'Add a check_reboot function'
```
## Code output:
```bash
[master d8e139c] Add a check_reboot function

 1 file changed, 6 insertions(+)
```
