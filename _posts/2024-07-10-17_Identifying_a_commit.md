---
title: 17 Identifying a commit  
date: 2024-07-05 22:31:06 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ cd checks
$ git log -1
```
## Code output:
```bash
commit abb063210c1f011b0d6470a4c5f1d8f672edd3ef (HEAD -> master)

Author: artwalker <artwalker@example.com>

Date:   Mon Jul 15 22:20:45 2023 +0200

    Add a gitignore file, ignoring .DS_STORE files
```
## Command:
```bash
$ git log -2
```
## Code output:
```bash
commit abb063210c1f011b0d6470a4c5f1d8f672edd3ef (HEAD -> master)

Author: artwawlker <artwawlker@example.com>

Date:   Mon Jul 15 22:20:45 2023 +0200

    Add a gitignore file, ignoring .DS_STORE files

commit 7d7167b2db44abf8cf014230f9b9708786e41c2a

Author: artwawlker <artwawlker@example.com>

Date:   Mon Jul 15 21:52:59 2023 +0200

    New name for disk_usage.py
```
## Command:
```bash
$ git show 7d7167b2db44abf8cf014230f9b9708786e41c2a
```
## Code output:
```bash
Author: artwawlker <artwalker@example.com>

Date:   Mon Jul 15 21:52:59 2019 +0200

    New name for disk_usage.py

diff --git a/disk_usage.py b/check_free_space.py

similarity index 100%

rename from disk_usage.py

rename to check_free_space.py
```
## Command:
```bash
git show 7d
```
## Code output:
```bash
fatal: ambiguous argument '7d': unknown revision or path not in the working tree.

Use '--' to separate paths from revisions, like this:

'git <command> [<revision>...] -- [<file>...]'
```
## Command:
```bash
$ git show 7d71
```
## Code output:
```bash
commit 7d7167b2db44abf8cf014230f9b9708786e41c2a

Author: artwalker <artwalker@example.com>

Date:   Mon Jul 15 21:52:59 2019 +0200

    New name for disk_usage.py

diff --git a/disk_usage.py b/check_free_space.py

similarity index 100%

rename from disk_usage.py

rename to check_free_space.py
```
## Command:
```bash
$ git revert 7d71
```
## Modify commit message:
```bash
Revert "New name for disk_usage.py"

Rollback reason: the previous name was actually better.

This reverts commit 7d7167b2db44abf8cf014230f9b9708786e41c2a.

# Please enter the commit message for your changes. Lines starting

# with '#' will be ignored, and an empty message aborts the commit.

#

# On branch master

# Changes to be committed:

#       renamed:    check_free_space.py -> disk_usage.py

#
```
## Code output:
```bash
[master 80b2dac] Revert "New name for disk_usage.py"

 1 file changed, 0 insertions(+), 0 deletions(-)

 rename check_free_space.py => disk_usage.py (100%)
```
## Command:
```bash
$ git show 80b2dac
```
## Code output:
```bash
commit 80b2dacef4b567196e61651064f03089c5e70b5e (HEAD -> master)

Author: artwalker <artwalker@example.com>

Date:   Wed Jul 17 00:02:39 2019 +0200

    Revert "New name for disk_usage.py"

    

    Rollback reason: the previous name was actually better.

    

    This reverts commit 7d7167b2db44abf8cf014230f9b9708786e41c2a.

diff --git a/check_free_space.py b/disk_usage.py

similarity index 100%

rename from check_free_space.py

rename to disk_usage.py
```
