---
title: 19 Creating new branches  
date: 2024-07-05 22:28:19 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ cd checks/
$ git branch
```
## Code output:
```bash
* master
```
## Command:
```bash
$ git branch new-feature
$ git branch
```
## Code output:
```bash
* master

  New-feature
```
## Command:
```bash
$ git checkout new-feature
```
## Code output:
```bash
Switched to branch 'new-feature'
```
## Command:
```bash
$ git checkout -b even-better-feature
```
## Code output:
```bash
Switched to a new branch 'even-better-feature'
```
