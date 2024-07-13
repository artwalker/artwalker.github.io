---
title: 27 Working With Remotes  
date: 2024-07-04 22:28:11 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command
```bash
$ cd health-checks/
$ git remote -v
```
## Code output
```bash
origin  https://github.com/artwalker/health-checks.git (fetch)

origin  https://github.com/artwalker/health-checks.git (push)
```
## Command
```bash
$ git remote show origin
```
## Code output
```bash
Username for 'https://github.com': artwalker

Password for 'https://artwalker@github.com': 

* remote origin

  Fetch URL: https://github.com/artwalker/health-checks.git

  Push  URL: https://github.com/artwalker/health-checks.git

  HEAD branch: master

  Remote branch:

    master tracked

  Local branch configured for 'git pull':

    master merges with remote master

  Local ref configured for 'git push':

    master pushes to master (up to date)
```
## Command
```bash
$ git branch -r
```
## Code output
```bash
 origin/HEAD -> origin/master

 origin/master
```
## Command
```bash
$ git status
```
## Code output
```bash
On branch master

Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```
