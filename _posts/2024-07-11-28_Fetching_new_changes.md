---
title: 28 Fetching new changes    
date: 2024-07-04 22:28:11 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command
```bash
$ cd health-checks/
$ git remote show origin
```
## Code output
```bash
* remote origin

  Fetch URL: https://github.com/artwalker/health-checks.git

  Push  URL: https://github.com/artwalker/health-checks.git

  HEAD branch: master

  Remote branch:

    master tracked

  Local branch configured for 'git pull':

    master merges with remote master

  Local ref configured for 'git push':

    master pushes to master (local out of date)
```
## Command
```bash
$ git fetch
```
## Code output
```bash
remote: Enumerating objects: 5, done.

remote: Counting objects: 100% (5/5), done.

remote: Compressing objects: 100% (4/4), done.

remote: Total 4 (delta 0), reused 4 (delta 0), pack-reused 0

Unpacking objects: 100% (4/4), done.

From https://github.com/artwalker/health-checks

   807cb50..b62dc2e  master     -> origin/master
```
## Command
```bash
$ git log origin/master
```
## Code output
```bash
commit b62dc2eacfa820cd9a762adab9213305d1c8d344 (origin/master, origin/HEAD)

Author: Yellow <Yellow@example.com>

Date:   Mon Jan 6 14:32:45 2023 -0800

    Add initial files for the checks

commit 807cb5037ccac5512ba583e782c35f4e114f8599 (HEAD -> master)

Author: artwalker <artwalker@example.com>

Date:   Mon Jan 6 14:09:41 2023 -800

    Add one more line to README.md

commit 3d9f86c50b8651d41adabdaebd04530f4694efb5

Author: Green <55592533+Green@users.noreply.github.com>

Date:   Sat Sep 21 14:04:15 2023 -0700

    Initial commit
```
## Command
```bash
$ git status
```
## Code output
```bash
On branch master

Your branch is behind 'origin/master' by 1 commit, and can be fast-forwarded.

  (use "git pull" to update your local branch)

nothing to commit, working tree clean
```
## Command
```bash
$ git merge origin/master
```
## Code output
```bash
Updating 807cb50..b62dc2e

Fast-forward

 all_checks.py | 18 ++++++++++++++++++

 disk_usage.py | 24 ++++++++++++++++++++++++

 2 files changed, 42 insertions(+)

 create mode 100755 all_checks.py

 create mode 100644 disk_usage.py
```
## Command
```bash
$ git log
```
## Code output
```bash
commit 1e0a1dfccf01183bfca7e30fb25f115889f95022 (HEAD -> master, origin/master, origin/HEAD)

commit b62dc2eacfa820cd9a762adab9213305d1c8d344 (HEAD -> master, origin/master, origin/HEAD)

Author: Yellow <Yellow@example.com>

Date:   Mon Jan 6 14:32:45 2023 -0800

    Add initial files for the checks

commit 807cb5037ccac5512ba583e782c35f4e114f8599 (HEAD -> master)

Author: artwalker <artwalker@example.com>

Date:   Mon Jan 6 14:09:41 2023 -800

    Add one more line to README.md

commit 3d9f86c50b8651d41adabdaebd04530f4694efb5

Author: Green <55592533+Green@users.noreply.github.com>

Date:   Sat Sep 21 14:04:15 2023 -0700
```
