---
title: 22 Merge confilcts  
date: 2024-07-04 22:28:16 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ vim free_memory.py
```
## Modify code
```python
#!/usr/bin/env python3
  
def main():
    """Checks if there's enough free memory in the computer."""

main()
```
## Command:
```bash
$ git commit -a -m 'Add comment to main()'
```
## Code output:
```bash
[master fe2fc5b] Add comment to main()

  1 file changed, 2 insertions(+), 2 deletions(-)
```
## Command:
```bash
$ git checkout even-better-feature 
```
## Code output:
```bash
Switched to branch 'even-better-feature'
```
## Command:
```bash
$ vim free_memory.py
```
## Modify code
```python
#!/usr/bin/env python3
  
def main():
    print("Everything ok.")

main()
```
## Command:
```bash
$ git commit -a -m 'Print everything ok'
```
## Code output:
```bash
[even-better-feature 6a6de99] Print everything ok

1 file changed, 2 insertions(+), 2 deletions(-)
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
$ git merge even-better-feature 
```
## Code output:
```bash
Auto-merging free_memory.py

CONFLICT (content): Merge conflict in free_memory.py

Automatic merge failed; fix conflicts and then commit the result.
```
## Command:
```bash
$ git status
```
## Code output:
```bash
On branch master

You have unmerged paths.

  (fix conflicts and run "git commit")

  (use "git merge --abort" to abort the merge)

Unmerged paths:

  (use "git add <file>..." to mark resolution)

        both modified:   free_memory.py

no changes added to commit (use "git add" and/or "git commit -a")
```
## Command:
```bash
$ vim free_memory.py 
```
## Modify code:
```python
#!/usr/bin/env python3
  
def main():
<<<<<<< HEAD
    """Checks if there's enough free memory in the computer."""
=======
    print("Everything ok.")
>>>>>>> even-better-feature

main()
```
## Modify code:
```python
#!/usr/bin/env python3
  
def main():
    """Checks if there's enough free memory in the computer."""
    print("Everything ok.")

main()
```
## Command:
```bash
$ git add free_memory.py
$ git status
```
## Code output:
```bash
On branch master

All conflicts fixed but you are still merging.

  (use "git commit" to conclude merge)

Changes to be committed:

        modified:   free_memory.py
```
## Command:
```bash
$ git commit
```
## Code output:
```bash
Merge branch 'even-better-feature'

Kept lines from both branches

# Conflicts:

#       free_memory.py

#

# It looks like you may be committing a merge.

# If this is not correct, please remove the file

#       .git/MERGE_HEAD

# and try again.

# Please enter the commit message for your changes. Lines starting

# with '#' will be ignored, and an empty message aborts the commit.

#

# On branch master

# All conflicts fixed but you are still merging.

#

# Changes to be committed:

#       modified:   free_memory.py
```
## Command:
```bash
$ git log --graph --oneline
```
## Code output:
```bash
*   8cb5e62 (HEAD -> master) Merge branch 'even-better-feature'

|\  

| * ca6de99 (even-better-feature) Print everything ok

* | fe2fc5b Add comment to main()

|/  

* 4361880 Add an empty free_memory.py

* 7d1de19 Revert "New name for disk_usage.py"

* bb9bd78 Add a gitignore file, ignoring .DS_STORE files

* 30e7071 New name for disk_usage.py

* 0d5a271 Delete unneeded processes file

* 5aada26 Adding file to delete it later

* cfb2b8e Add periods to the end of sentences.

* 21e6a1a Add new disk_usage check.
```
