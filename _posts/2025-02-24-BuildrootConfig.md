---  
title: Buildroot Config Document 
date: 2025-02-21 13:27:25 +0800   
categories: [Embedded Linux]  
tags: [Embedded Linux]  
---  
# linux system programming introduction to buildroot

## 1. Buildroot子仓库配置 

### 第一次初始化一个Buildroot仓库

```bash
git clone git@github.com:artwalker/BuildrootLinux.git
git submodule add -b 2024.02.x https://gitlab.com/buildroot.org/buildroot.git buildroot
git submodule update --init --recursive # 递归更新子模块
git commit -m "Added Buildroot as a submodule targeting branch 2024.02.x"
git push origin main
```

### 他人拷贝上述包含子模块的仓库

```bash
git clone --recurse-submodules git@github.com:artwalker/BuildrootLinux.git
```

### 编译buidroot

```bash
make list-defconfigs # 显示预设置好的配置
make qemu_aarch64_virt_defconfig # 选择一个配置文件
make # 开始编译
```

### 更新子模块

```bash
cd buildroot
git checkout 2024.02.x
git pull origin 2024.02.x
cd ..
git add buildroot
git commit -m "Updated Buildroot submodule to latest 2024.02.x"
git push origin main
```

## 2. Linux 介绍

https://cvw.cac.cornell.edu/Linux

https://ryanstutorials.net/

## 3. 书籍推荐

[Linux System Programming, 2nd Edition](https://learning.oreilly.com/library/view/linux-system-programming/9781449341527/)

[Mastering Embedded Linux Programming - Third Edition](https://learning.oreilly.com/library/view/mastering-embedded-linux/9781789530384/)

## 4. git 参考网址

https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes

[git: fetch and merge, don’t pull](https://longair.net/blog/2009/04/16/git-fetch-and-merge/)

## 5. Makefile

https://makefiletutorial.com/

https://www.gnu.org/software/make/manual/html_node/Simple-Makefile.html

## 6. Linux man pages

https://www.die.net/

https://man7.org/index.html

http://man7.org/linux/man-pages/man8/start-stop-daemon.8.html

## 7. Buildroot documentation

* https://buildroot.org/downloads/manual/manual.html#requirement-mandatory
* https://buildroot.org/downloads/manual/manual.html#customize
* https://buildroot.org/downloads/manual/manual.html#generic-package-tutorial
* https://buildroot.org/downloads/manual/manual.html#configure

## 8. QEMU documentation

* https://qemu.readthedocs.io/en/v9.2.0/system/invocation.html#invocation

- https://www.qemu.org/docs/master/system/invocation.html#hxtool-5

## 9. Networking Programming

* https://beej.us/guide/bgnet/html/

## 10. sh 脚本说明模板

```bash
#!/bin/bash
#
# Script Name: myscript.sh
# Description: This is an example of how to write program documentation in a shell script.
# Author: Your Name
# Version: 1.0
# Date: January 27, 2025
#
# Arguments:
#   -h | --help       Display help message and exit
#   -v | --version    Display version information and exit
#
# Usage Examples:
#   ./myscript.sh -h
#   ./myscript.sh arg1 arg2
#
# Notes:
#   Ensure the script has executable permissions, use chmod +x myscript.sh to add permissions if necessary.

# Function definitions and main program code start here...\
```

## 11. 查看分支与标签

```bash
git clone https://gitlab.com/buildroot.org/buildroot.git
cd buildroot

git branch -a
git tag
```

## 12. 使用命令验证内存泄漏

```bash
sudo apt install valgrind

valgrind --error-exitcode=1 --leak-check=full --show-leak-kinds=all --track-origins=yes --errors-for-leak-kinds=definite --verbose --log-file=valgrind-out.txt ./aesdsocket
```
