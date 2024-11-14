---  
title: 45 Squashing changes  
date: 2024-07-04 22:27:54 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command
```bash
$ git rebase -i master
```

## Code output:
```bash
pick 736d754 Add a simple README file
pick 01231b0 Add more information to the README

(...)
```
## Modify file:
```bash
pick 736d754 Add a simple README file
squash 01231b0 Add more information to the README

(...)
```
## Modify file:
```bash
# This is a combination of 2 commits. 
# This is the 1st commit message:

Add a simple README file including an example use case

# This is the commit message #2:

Add more information to the README

(...)
```

## Code output:
```bash
[detached HEAD ae779e4] Add a simple README.md file including an example use case

 Date: Tue Jan 7 09:47:17 2020 -0800

 1 file changed, 9 insertions(+)

 create mode 100644 README.md

Successfully rebased and updated refs/heads/add-readme.
```
## Command
```bash
$ git show
```

## Code output:
```bash
commit ae779e430288b082a19062ed087c547e1051a981 (HEAD -> add-readme)

Author: My name <me@example.com>

Date:   Tue Jan 7 09:47:17 2020 -0800

    Add a simple README file including an example use case

diff --git a/README.md b/README.md

new file mode 100644

index 0000000..5761a46

--- /dev/null

+++ b/README.md

@@ -0,0 +1,9 @@

+Rearrange

+=========

+

+This module is used for rearranging names.

+Turns "LastName, FirstName" into "FirstName LastName"

+

+# Example

+

+Calling `rearrange_name("Turing, Alan")` will return `"Alan Turing"`
```
## Command
```bash
$ git status
```

## Code output:
```bash
On branch add-readme

Your branch and 'origin/add-readme' have diverged,

and have 1 and 2 different commits each, respectively.

  (use "git pull" to merge the remote branch into yours)

nothing to commit, working tree clean


```
## Command
```bash
$ git log --graph --oneline --all -4
```

## Code output:
```bash
* ae779e4 (HEAD -> add-readme) Add a simple README.md file including an example use case

| * 01231b0 (origin/add-readme) Add more information to the README

| * 736d754 Add a simple README.md file

|/  

* 367a127 (origin/master, origin/HEAD, master) Add tests for the rearrange module
```
## Command
```bash
$ git push
```

## Code output:
```bash
Username for 'https://github.com': artwalker

Password for 'https://artwalker@github.com': artwalker

To https://github.com/artwalker/rearrange.git

 ! [rejected]        add-readme -> add-readme (non-fast-forward)

error: failed to push some refs to 'https://github.com/artwalker/rearrange.git'

hint: Updates were rejected because the tip of your current branch is behind

hint: its remote counterpart. Integrate the remote changes (e.g.

hint: 'git pull ...') before pushing again.

hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
## Command
```bash
$ git push -f
```

## Code output:
```bash
Enumerating objects: 4, done.

Counting objects: 100% (4/4), done.

Delta compression using up to 4 threads

Compressing objects: 100% (3/3), done.

Writing objects: 100% (3/3), 510 bytes | 510.00 KiB/s, done.

Total 3 (delta 0), reused 0 (delta 0)

To https://github.com/artwalker/rearrange.git

 + 01231b0...ae779e4 add-readme -> add-readme (forced update)
```
## Command
```bash
$ git log --graph --oneline --all -4
```

## Code output:
```bash
* ae779e4 (HEAD -> add-readme, origin/add-readme) Add a simple README.md file including an example use case

* 367a127 (origin/master, origin/HEAD, master) Add tests for the rearrange module

* c89805e Add the rearrange module

* f4ddbc7 Initial commit
```
