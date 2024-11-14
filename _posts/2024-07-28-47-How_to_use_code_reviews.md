---  
title: 47 How to use code reviews  
date: 2024-07-04 22:27:52 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command
```bash
$ vim README.md
```

## Code output:
```bash
Rearrange
=========

This module is used for rearranging names.
Turns "LastName, FirstName" into "FirstName LastName".

## Examples

 * Calling `rearrange_name("Turing, Alan")` will return `"Alan Turing"`
 * Calling `rearrange_name("Hopper, Grace M.")` will return `"Grace M. Hopper"`
 * Calling `rearrange_name("Voltaire")` will return `"Voltaire"`
```

## Command
```bash
$ git commit -a --amend
```

## Code output:
```bash
[add-readme 55e32ed] Add a simple README.md file including an example use case

 Date: Tue Jan 7 09:47:17 2020 -0800

 1 file changed, 11 insertions(+)

 Create mode 100644 README.md
```
## Command
```bash
$ git push -f
```

## Code output:
```bash
Username for 'https://github.com': artwalker

Password for 'https://artwalker@github.com': artwalker

numerating objects: 4, done.

Counting objects: 100% (4/4), done.

Delta compression using up to 4 threads

Compressing objects: 100% (3/3), done.

Writing objects: 100% (3/3), 553 bytes | 553.00 KiB/s, done.

Total 3 (delta 0), reused 0 (delta 0)

To https://github.com/artwalker/rearrange.git

 + ae779e4...55e32ed master -> master (forced update)
```
