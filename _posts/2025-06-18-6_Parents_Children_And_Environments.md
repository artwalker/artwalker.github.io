---
title: 6 Parents Children And Environments 
date: 2025-06-18 18:54:00 +0800 
categories: [efficient-linux] 
tags: [Linux,Command]
---
# 6. Parents, Children, And Environments

## Shell Are Executable Files

```bash
$ cd /bin
$ ls -l bash cat ls grep
-rwxr-xr-x 1 root root 1113504 Jun  6  2019 bash
-rwxr-xr-x 1 root root   35064 Jan 18  2018 cat
-rwxr-xr-x 1 root root  219456 Sep 18  2019 grep
-rwxr-xr-x 1 root root  133792 Jan 18  2018 ls
```

```bash
$ cat /etc/shells
/bin/sh
/bin/bash
/bin/csh
/bin/zsh
```

```bash
$ echo $SHELL
/bin/bash
```

```shell
#!/bin/bash
# Print a prompt
echo -n '$ '
# Read the user's input in a loop. Exit when the user presses Ctrl-D.
while read line; do
 # Ignore the input $line and print a message
 echo "I'm sorry, I'm afraid I can't do that"
 # Print the next prompt
 echo -n '$ '
done
```

```bash
$ PS1="%% "
%% ls                                 The prompt has changed
animals.txt
%% echo "This is a new shell"
This is a new shell
%% exit
$
```

## Parent and Child Processes

A running Linux program is known as a process, so you’ll also see the terms parent process and child process.

Every time you run a simple command, you create a child process.

Each child’s environment is copied from its parent’s environment on startup.

```shell
#!/bin/bash
cd /etc
echo "Here is my current directory:"
pwd
```

```bash
$ chmod +x cdtest

$ pwd
/home/smith
$ ./cdtest
Here is my current directory:
/etc

$ pwd
/home/smith
```

## Environment Variables

```bash
$ printenv | sort -i | less
⋮
DISPLAY=:0
EDITOR=emacs
HOME=/home/smith
LANG=en_US.UTF-8
PWD=/home/smith/Music
SHELL=/bin/bash
TERM=xterm-256color
USER=smith
⋮
```

```bash
$ title="Efficient Linux"
$ echo $title
Efficient Linux
$ printenv title                               (produces no output)
```

### Creating Environment Variables

To turn a local variable into an environment variable, use the export command:

```bash
$ MY_VARIABLE=10                  A local variable
$ export MY_VARIABLE              Export it to become an environment variable
$ export ANOTHER_VARIABLE=20      Or, set and export in a single command
```

```bash
$ export E="I am an environment variable"     Set an environment variable
$ L="I am just a local variable"              Set a local variable
$ echo $E
I am an environment variable
$ echo $L
I am just a local variable
$ bash                                        Run a child shell
$ echo $E                                     Environment variable was copied
I am an environment variable
$ echo $L                                     Local variable was not copied
                                              Empty string is printed
$ exit                                        Exit the child shell
```

```bash
$ export E="I am the original value"          Set an environment variable
$ bash                                        Run a child shell
$ echo $E
I am the original value                       Parent's value was copied
$ E="I was modified in a child"               Change the child's copy
$ echo $E
I was modified in a child
$ exit                                        Exit the child shell
$ echo $E
I am the original value                       Parent's value is unchanged
```

### Superstition Alert: "Global" Variables

## Child Shells Versus Subshess

```bash
$ alias                        List aliases
alias gd='pushd'
alias l='ls -CF'
alias pd='popd'
$ bash --norc                  Run a child shell and ignore bashrc files
$ alias                        List aliases - none are known
$ echo $HOME                   Environment variables are known
/home/smith
$ exit                         Exit the child shell
```

```bash
$ (ls -l)                                      Launches ls -l in a subshell
-rw-r--r-- 1 smith smith 325 Oct 13 22:19 animals.txt
$ (alias)                                      View aliases in a subshell
alias gd=pushd
alias l=ls -CF
alias pd=popd
⋮
$ (l)                                          Run an alias from the parent
animals.txt
```

```bash
$ echo $BASH_SUBSHELL         Check the current shell
0                             Not a subshell
$ bash                        Run a child shell
$ echo $BASH_SUBSHELL         Check the child shell
0                             Not a subshell
$ exit                        Exit the child shell
$ (echo $BASH_SUBSHELL)       Run an explicit subshell
1                             Yes, it's a subshell
```

## Configuring Your Environment

|   File type   |                    Run by                    |                                               	System-wide location                                                |                                     Personal file locations (in order invoked)                                     |
| ------------- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| Startup files | Login shells, on invocation                  | /etc/profile                                                                                                       | $HOME/.bash_profile,   $HOME/.bash_login, and $HOME/.profile                                                       |
| Init files    | Interactive shells (nonlogin), on invocation | /etc/bashrc or /etc/bash.bashrc, depending on distro (look in /etc to check)                                       | $HOME/.bashrc                                                                                                      |
| Init files    | Shell scripts, on invocation                 | Set the variable BASH_ENV to the absolute path to an initialization file (example: BASH_ENV=/usr/local/etc/bashrc) | Set the variable BASH_ENV to the absolute path to an initialization file (example: BASH_ENV=/usr/local/etc/bashrc) |
| Cleanup files | Login shells, on exit                        | /etc/bash.bash_logout                                                                                              | $HOME/.bash_logout                                                                                                 |

```shell
# Place in $HOME/.bash_profile or other personal startup file
if [ -f "$HOME/.bashrc" ]
then
  source "$HOME/.bashrc"
fi
```

### Rereading a Configuration File

```bash
$ source ~/.bash_profile             Uses the builtin "source" command
$ . ~/.bash_profile                  Uses a dot
```

>Q: Why do you source a configuration file instead of making it executable with chmod and running it like a shell script? 
>A: Because a script runs in a child process. Any commands in the script would not affect your intended (parent) shell. They would affect only the child, which exits, leaving you with nothing changed.

### Traveling with Your Environment 

Version Control: Git Github
