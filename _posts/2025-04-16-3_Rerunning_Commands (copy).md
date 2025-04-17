---
title: 4 Cruising The Filesystem 
date: 2025-04-17 18:13:00 +0800 
categories: [efficient-linux] 
tags: [Linux,Command]
---
# 4. Cruising The Filesystem

## Visiting Specific Directories Efficiently

### Jump to Your Home Directory

```bash
$ pwd
/etc                              Start somewhere else
$ cd                              Run cd with no arguments...
$ pwd
/home/smith                       ...and you're home again
```

```bash
$ cd $HOME/Work
$ cd ~/Work
```

```bash
$ echo $HOME ~
/home/smith /home/smith
```

```bash
$ echo ~jones
/home/jones
```

### Move Faster with Tab Completion

```bash
$ cd /usr
$ ls
bin  games  include  lib  local  sbin  share  src
```

```bash
$ cd sha<Tab>
$ cd share/
```

```bash
$ cd s<Tab>

$ cd s<Tab><Tab>
sbin/  share/  src/

$ cd sh<Tab>
$ cd share/
```

Tab completion is not only for `cd` commands, but also works for most commands.

### Hop to Frequently Visited Directories Using Aliases or Variables

```bash
# In a shell configuration file:
alias work="cd $HOME/Work/Projects/Web/src/include"

$ work
$ pwd
/home/smith/Work/Projects/Web/src/include
```

```bash
$ work=$HOME/Work/Projects/Web/src/include
$ cd $work
$ pwd
/home/smith/Work/Projects/Web/src/include
$ ls $work/css                                Use the variable in other ways
main.css  mobile.css
```

```bash
# Place in a shell configuration file and source it:
alias rcedit='cc $HOME/.bashrc'
```

```bash
# Define the qcd function
qcd () {
  # Accept 1 argument that's a string key, and perform a different
  # "cd" operation for each key.
  case "$1" in
    work)
      cd $HOME/Work/Projects/Web/src/include
      ;;
    recipes)
      cd $HOME/Family/Cooking/Recipes
      ;;
    video)
      cd /data/Arts/Video/Collection
      ;;
    beatles)
      cd $HOME/Music/mp3/Artists/B/Beatles
      ;;
    *)
      # The supplied argument was not one of the supported keys
      echo "qcd: unknown key '$1'"
      return 1
      ;;
  esac
  # Helpfully print the current directory name to indicate where you are
  pwd
}
# Set up tab completion
complete -W "work recipes video beatles" qcd
```

```bash
$ qcd <Tab><Tab>
beatles  recipes  video    work
$ qcd v<Tab><Enter>                       Completes 'v' to 'video'
/data/Arts/Video/Collection
```

### Make a Big Filesystem Feel Smaller with CDPATH

```bash
$ CDPATH=/usr     Set a CDPATH
$ cd /tmp         No output: CDPATH wasn't consulted
$ cd bin          cd consults CDPATH...
/usr/bin          ...and prints the new working directory
```

### Organize Your Home Directory for Fast Navigation

![Two levels of subdirectories in the directory /home/smith](E:\00Project\Linux\elcl_0401.png)

```bash
# Place in a shell configuration file and source it:
export CDPATH=$HOME:$HOME/Work:$HOME/Family:$HOME/Linux:$HOME/Music:..
```

```bash
$ (ls -d */ && ls -d */*/ | cut -d/ -f2-) | sort | uniq -c | sort -nr | less
```

## Returning to Directories Efficiently

### Toggle Between Two Directories with "cd -"

```bash
$ pwd
/home/smith/Finances/Bank/Checking/Statements
$ cd /etc
$ cd -
/home/smith/Finances/Bank/Checking/Statements
```

### Toggle Among Many Directories with  pushd and popd

#### Push a directory onto the stack

```bash
$ pwd
/home/smith/Work/Projects/Web/src
$ pushd /var/www/html
/var/www/html ~/Work/Projects/Web/src
$ pushd /etc/apache2
/etc/apache2 /var/www/html ~/Work/Projects/Web/src
$ pushd /etc/ssl/certs
/etc/ssl/certs /etc/apache2 /var/www/html ~/Work/Projects/Web/src
$ pwd
/etc/ssl/certs
```

#### View a directory stack

```bash
$ dirs
/etc/ssl/certs /etc/apache2 /var/www/html ~/Work/Projects/Web/src
```

```bash
$ dirs -p
/etc/ssl/certs
/etc/apache2
/var/www/html
~/Work/Projects/Web/src
```

```bash
$ dirs -p | nl -v0
     0  /etc/ssl/certs
     1  /etc/apache2
     2  /var/www/html
     3  ~/Work/Projects/Web/src
```

```bash
$ dirs -v
 0  /etc/ssl/certs
 1  /etc/apache2
 2  /var/www/html
 3  ~/Work/Projects/Web/src
 
# Place in a shell configuration file and source it:
alias dirs='dirs -v'
```

#### Pop a directory from the stack

```bash
$ dirs
/etc/ssl/certs /etc/apache2 /var/www/html ~/Work/Projects/Web/src
```

```bash
$ popd
/etc/apache2 /var/www/html ~/Work/Projects/Web/src
$ popd
/var/www/html ~/Work/Projects/Web/src
$ popd
~/Work/Projects/Web/src
$ popd
bash: popd: directory stack empty
$ pwd
~/Work/Projects/Web/src
```

```bash
# Place in a shell configuration file and source it:
alias gd=pushd
alias pd=popd
```

#### Swap directories on the stack

```bash
$ dirs
/etc/apache2 ~/Work/Projects/Web/src /var/www/html
$ pushd
~/Work/Projects/Web/src /etc/apache2 /var/www/html
$ pushd
/etc/apache2 ~/Work/Projects/Web/src /var/www/html
$ pushd
~/Work/Projects/Web/src /etc/apache2 /var/www/html
```

#### Turn a mistaken cd into a pushd

```bash
$ dirs
~/Work/Projects/Web/src /var/www/html /etc/apache2
$ cd /etc/ssl/certs
$ dirs
/etc/ssl/certs /var/www/html /etc/apache2
```

```bash
$ pushd -
~/Work/Projects/Web/src /etc/ssl/certs /var/www/html /etc/apache2
$ pushd
/etc/ssl/certs ~/Work/Projects/Web/src /var/www/html /etc/apache2
```

#### Go deeper into the stack

```bash
$ pushd +N
```

```bash
$ dirs
/etc/ssl/certs ~/Work/Projects/Web/src /var/www/html /etc/apache2
$ pushd +1
~/Work/Projects/Web/src /var/www/html /etc/apache2 /etc/ssl/certs
$ pushd +2
/etc/apache2 /etc/ssl/certs ~/Work/Projects/Web/src /var/www/html
```

```bash
# To shift /var/www/html to the top of the stack (and make it your current directory), run pushd +3.
$ dirs -v
 0  /etc/apache2
 1  /etc/ssl/certs
 2  ~/Work/Projects/Web/src
 3  /var/www/html
```

```bash
# To jump to the directory at the bottom of the stack, run pushd -0 (dash zero):
$ dirs
/etc/apache2 /etc/ssl/certs ~/Work/Projects/Web/src /var/www/html
$ pushd -0
/var/www/html /etc/apache2 /etc/ssl/certs ~/Work/Projects/Web/src
```

```bash
$ popd +N
```

```bash
$ dirs
/var/www/html /etc/apache2 /etc/ssl/certs ~/Work/Projects/Web/src
$ popd +1
/var/www/html /etc/ssl/certs ~/Work/Projects/Web/src
$ popd +2
/var/www/html /etc/ssl/certs
```

> An alternative is to open multiple virtual displays using command-line programs like `screen` and `tmux`, which are called *terminal multiplexers*. They’re more effort to learn than directory stacks but worth a look.

# Screen

## 会话管理

| 操作         | 快捷键                                                    | 说明                                                         |
| ------------ | --------------------------------------------------------- | ------------------------------------------------------------ |
| 创建新会话   | `screen` 或 `screen -S <会话名>`                          | 直接输入 `screen` 创建无名称会话；`-S` 选项可指定会话名，如 `screen -S myproject` 创建名为 `myproject` 的会话 |
| 分离当前会话 | `Ctrl + A`，然后按 `d`                                    | 将会话置于后台继续运行，可随时重新连接                       |
| 列出所有会话 | `screen -ls`                                              | 显示所有正在运行和已分离的 `screen` 会话                     |
| 恢复会话     | `screen -r <会话名或编号>`                                | 重新连接到指定会话，若只有一个分离会话，可直接用 `screen -r` |
| 终止会话     | 在会话中输入 `exit` 或 `screen -X -S <会话名或编号> quit` | 前者在会话内直接退出，后者在外部终止指定会话                 |

## 窗口操作

| 操作               | 快捷键                          | 说明                                    |
| ------------------ | ------------------------------- | --------------------------------------- |
| 创建新窗口         | `Ctrl + A`，然后按 `c`          | 在当前会话中创建一个新的终端窗口        |
| 切换到下一个窗口   | `Ctrl + A`，然后按 `n`          | 按顺序切换到下一个窗口                  |
| 切换到上一个窗口   | `Ctrl + A`，然后按 `p`          | 按顺序切换到上一个窗口                  |
| 切换到指定编号窗口 | `Ctrl + A`，然后按 `<窗口编号>` | 直接切换到对应编号的窗口，编号从 0 开始 |
| 列出所有窗口       | `Ctrl + A`，然后按 `w`          | 显示当前会话中所有窗口的列表及状态      |
| 重命名当前窗口     | `Ctrl + A`，然后按 `A`          | 输入新的窗口名称并回车确认              |

## 其他实用操作

| 操作         | 快捷键                                                       | 说明                                                        |
| ------------ | ------------------------------------------------------------ | ----------------------------------------------------------- |
| 锁定会话     | `Ctrl + A`，然后按 `x`                                       | 锁定当前会话，需要输入登录密码解锁                          |
| 进入滚动模式 | `Ctrl + A`，然后按 `[`                                       | 可以使用方向键、`Page Up`、`Page Down` 滚动屏幕查看历史输出 |
| 退出滚动模式 | 按 `Enter`                                                   | 在滚动模式下按此键退出                                      |
| 复制模式     | `Ctrl + A`，然后按 `[`，移动光标到起始位置，按 `Space` 开始标记，移动到结束位置按 `Enter` 完成复制 | 用于复制屏幕上的文本内容                                    |
| 粘贴内容     | `Ctrl + A`，然后按 `]`                                       | 将复制模式中复制的内容粘贴到当前位置                        |