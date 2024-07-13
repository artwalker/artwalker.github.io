---
title: 29 Updating the local resository  
date: 2024-07-04 22:28:10 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command
```bash
$ git pull
```
## Code output
```bash
remote: Enumerating objects: 8, done.

remote: Counting objects: 100% (8/8), done.

remote: Compressing objects: 100% (5/5), done.

Unpacking objects: 100% (6/6), done.

remote: Total 6 (delta 1), reused 6 (delta 1), pack-reused 0

From https://github.com/redquinoa/health-checks

   807cb50..b62dc2e  master       -> origin/master

 * [new branch]      experimental -> origin/experimental

Updating 807cb50..b62dc2e

Fast-forward

 all_checks.py | 15 +++++++++++++++

 1 file changed, 15 insertions(+)
```
## Command
```bash
$ git -log -p -1
```
## Code output
```bash
commit 922d65950b5325109525a24b71d8df8a46412d04 (HEAD -> master, origin/master, origin/HEAD)

Author: Blue Kale <bluekale@example.com>

Date:   Mon Jan 6 14:42:44 2020 -0800

    Add disk full check to all_checks.py

diff --git a/all_checks.py b/all_checks.py

index fdc4476..e46cdae 100755

--- a/all_checks.py

+++ b/all_checks.py

@@ -1,16 +1,31 @@

 #!/usr/bin/env python3

 

 import os

+import shutil

 import sys

(...)

def(check_reboot): 

	""" Returns True if the computer has a pending reboot."""

	Return os.path.exists(“/run/reboot-required”)

+def check_disk_full(disk, mmin_absolute, min_percent):

+	"""Returns True if there isn’t enough disk space, False otherwise."""

+	du = shutil.disk_usage(disk)

+	# Calculate the percentage of free space

+	percent_free = 100 * du.free / du.total

+	# Calculate how many free gigabytes
```
## Command
```bash
$ git remote show origin
```
## Code output
```bash
* remote origin

  Fetch URL: https://github.com/redquinoa/health-checks.git

  Push  URL: https://github.com/redquinoa/health-checks.git

  HEAD branch: master

  Remote branches:

    experimental tracked

    master       tracked

  Local branch configured for 'git pull':

    master merges with remote master

  Local ref configured for 'git push':

    master pushes to master (up to date)
```
## Command
```bash
$ git checkout experimental 
```
## Code output
```bash
Branch 'experimental' set up to track remote branch 'experimental' from 'origin'.

Switched to a new branch 'experimental'
```
