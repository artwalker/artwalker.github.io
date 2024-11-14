---  
title: 43 The typical pull request workflow on GitHub  
date: 2024-07-04 22:27:56 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command
```bash
$ git clone https://github.com/artwalker/rearrange.git
```

## Code output:
```bash
Cloning into 'rearrange'...

remote: Enumerating objects: 9, done.

remote: Counting objects: 100% (9/9), done.

remote: Compressing objects: 100% (7/7), done.

remote: Total 9 (delta 1), reused 9 (delta 1), pack-reused 0

Unpacking objects: 100% (9/9), done.
```

## Command
```bash
$ cd rearrange
$ ls -l
```

## Code output:
```bash
total 20

-rw-rw-r-- 1 user user 11357 Jan 7 09:42 LICENSE

-rw-rw-r-- 1 user user   211 Jan 7 09:42 rearrange.py

-rw-rw-r-- 1 user user   762 Jan 7 09:42 rearrange_test.py
```

## Command
```bash
$ git log
```

## Code output:
```bash
commit 367a127672c40a163a6f05ad930f2b0b857dc961  (HEAD -> master, origin/master, origin/HEAD)

Author: Blue Kale <bluekale@example.com>

Date:   Mon Jul 29 21:21:53 2019 +0200

    Add tests for the rearrange module

commit c89805e52a1afa143c503f946cc5ead0fdd20255

Author: Blue Kale <bluekale@example.com>

Date:   Mon Jul 29 21:20:57 2019 +0200

    Add the rearrange module

commit f4ddbc7a0ca3ac83a7e9ce7030e774b58e5dda42

Author: Blue Kale <53440916+blue-kale@users.noreply.github.com>

Date:   Mon Jul 29 16:07:42 2019 -0300

    Initial commit
```

## Command
```bash
$ git checkout -b add-readme
```

## Code output:
```bash
Switched to a new branch 'add-readme'
```
## Command
```bash
$ vim README.md
```

## Modify file:
```md
Rearrange
=========

This module is used for rearranging names.
```
## Command
```bash
$ git add README.md
$ git commit -m 'Add a simple README.md file'
```

## Code output:
```bash
[master 736d754] Add a simple README.md file

 1 file changed, 4 insertions(+)

 create mode 100644 README.md
```
## Command
```bash
$ git push -u origin add-readme
```

## Code output:
```bash
Username for 'https://github.com': artwalker

Password for 'https://artwalker@github.com': 

Enumerating objects: 4, done.

Counting objects: 100% (4/4), done.

Delta compression using up to 4 threads

Compressing objects: 100% (3/3), done.

Writing objects: 100% (3/3), 400 bytes | 400.00 KiB/s, done.

Total 3 (delta 0), reused 0 (delta 0)

remote: 

remote: Create a pull request for 'add-readme' on GitHub by visiting:

remote:      https://github.com/artwalker/rearrange/pull/new/add-readme

remote: 

To https://github.com/artwalker/rearrange.git

 * [new branch]      add-readme -> add-readme

Branch 'add-readme' set up to track remote branch 'add-readme' from 'origin'.
```
