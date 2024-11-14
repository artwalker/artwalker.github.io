---  
title: 44 Updating an Existing Pull Request  
date: 2024-07-04 22:27:55 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command
```bash
$ vim README.md
```

## Modify code:
```md
Rearrange
=========

This module is used for rearranging names. 
Turns "LastName,FirstName" into "Firstname LastName"

# Example

Calling `rearrange_name("Turing, Alan")` will return `"Alan Turing"`
```
## Command
```bash
$ git commit -a -m 'Add more information to the README'
```

## Code output:
```bash
[add-readme 01231b0] Add more information to the README

 1 file changed, 5 insertions(+)
```
## Command
```bash
$ git push
```

## Code output:
```bash
Username for 'https://github.com': artwalker

Password for 'https://artwalker@github.com': artwalker

Enumerating objects: 5, done.

Counting objects: 100% (5/5), done.

Delta compression using up to 4 threads

Compressing objects: 100% (3/3), done.

Writing objects: 100% (3/3), 407 bytes | 407.00 KiB/s, done.

Total 3 (delta 1), reused 0 (delta 0)

remote: Resolving deltas: 100% (1/1), completed with 1 local object.

To https://github.com/artwalker/rearrange.git

   736d754..01231b0  add-readme -> add-readme
```
