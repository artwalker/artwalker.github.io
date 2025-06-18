---
title: 2 Introducing The Shell
date: 2025-04-11 16:56:00 +0800
categories: [efficient-linux]
tags: [Linux,Command]
---
# 2. Introducing The Shell

## Pattern Matching for Filenames

```bash
$ grep Linux chapter*

$ grep Linux chapter?

$ grep Linux chapter??

$ grep Linux chapter[12345]

$ grep Linux chapter[1-5]

$ grep Linux chapter*[02468]

$ ls [A-Z]*_*@

$ ls -1 /etc/*.conf
/etc/adduser.conf
/etc/appstream.conf
⋮
/etc/wodim.conf
```

The first is that the shell, not the invoked program, performs the pattern matching.

The second important point is that shell pattern matching applies only to file and directory paths.

## Evaluating Variables

```bash
$ printenv HOME
/home/smith
$ printenv USER
smith

$ echo My name is $USER and my files are in $HOME    Evaluating variables
My name is smith and my files are in /home/smith
$ echo ch*ter9                                       Evaluating a pattern
chapter9
```
### Where Variables Come From

```bash
$ work=$HOME/Projects

$ cd $work
$ pwd
/home/smith/Projects

$ cp myfile $work
$ ls $work
myfile

$ work = $HOME/Projects               The shell assumes "work" is a command
work: command not found
```
### Variables and Superstition

```bash
$ echo $HOME
/home/smith

# From echo’s perspective,
$ echo /home/smith
```
### Patterns Versus Variables

```bash
$ ls
mammals   reptiles
$ ls mammals
lizard.txt  snake.txt

mv mammals/*.txt reptiles                     Method 1

FILES="lizard.txt snake.txt"
mv mammals/$FILES reptiles                    Method 2

$ echo mammals/*.txt
mammals/lizard.txt mammals/snake.txt
$ mv mammals/lizard.txt mammals/snake.txt reptiles

$ echo mammals/$FILES
mammals/lizard.txt snake.txt
$ mv mammals/lizard.txt snake.txt reptiles
$ mv mammals/$FILES reptiles
/bin/mv: cannot stat 'snake.txt': No such file or directory

FILES="lizard.txt snake.txt"
for f in $FILES; do
  mv mammals/$f reptiles
done
```
### Shortening Commands with Aliases
```bash
$ alias g=grep                 A command with no arguments
$ alias ll="ls -l"             A command with arguments: quotes are required

$ ll                                            # Runs "ls -l"
-rw-r--r-- 1 smith smith 325 Jul  3 17:44 animals.txt
$ g Nutshell animals.txt                        # Runs "grep Nutshell animals.txt"
horse   Linux in a Nutshell     2009    Siever, Ellen
donkey  Cisco IOS in a Nutshell 2005    Boney, James

# Shadowing the command
$ alias less="less -c"

# List a shell’s aliases
$ alias
alias g='grep'
alias ll='ls -l'

# See the value of a single alias
$ alias g
alias g='grep'

# Delete an alias from a shell
$ unalias g
```
### Redirecting Input and Output
```bash
$ grep Perl animals.txt > outfile                      (displays no output)
$ cat outfile
alpaca	Intermediate Perl	2012	Schwartz, Randal
```

```bash
$ grep Perl animals.txt > outfile              Create or overwrite outfile
$ echo There was just one match >> outfile     Append to outfile
$ cat outfile
alpaca	Intermediate Perl	2012	Schwartz, Randal
There was just one match
```

```bash
$ wc animals.txt                            Reading from a named file
  7  51 325 animals.txt
$ wc < animals.txt                          Reading from redirected stdin
  7  51 325
```

```bash
# Redirect stderr
$ cp nonexistent.txt file.txt 2> errors
$ cat errors
cp: cannot stat 'nonexistent.txt': No such file or directory
# Append stderr
$ cp nonexistent.txt file.txt 2> errors
$ cp another.txt file.txt 2>> errors
$ cat errors
cp: cannot stat 'nonexistent.txt': No such file or directory
cp: cannot stat 'another.txt': No such file or directory
```

```bash
# Redirect both stdout and stderr
$ echo This file exists > goodfile.txt               Create a file
$ cat goodfile.txt nonexistent.txt &> all.output
$ cat all.output
This file exists
cat: nonexistent.txt: No such file or directory
```

```bash
$ wc < animals.txt > count
$ cat count
  7  51 325
```

```bash
$ grep Perl < animals.txt | wc > count
$ cat count
      1       6      47
```

### Disabling Evaluation with Quotes and Escapes

Single quotes tell the shell to treat every character in a string literally:

```bash
$ echo '$HOME'
$HOME
```

Double quotes tell the shell to treat all characters literally except for certain dollar signs and a few others:

```bash
$ echo "Notice that $HOME is evaluated"                  Double quotes
Notice that /home/smith is evaluated
$ echo 'Notice that $HOME is not'                        Single quotes
Notice that $HOME is not
```

A backslash tells the shell to treat the next character literally:

```bash
$ echo \$HOME
$HOME

$ echo "The value of \$HOME is $HOME"
The value of $HOME is /home/smith

$ echo 'The value of \$HOME is $HOME'
The value of \$HOME is $HOME

$ echo "This message is \"sort of\" interesting"
This message is "sort of" interesting
```

A backslash at the end of a line allows shell commands to span multiple lines:

```bash
$ echo "This is a very long message that needs to extend \
onto multiple lines"
This is a very long message that needs to extend onto multiple lines
```

Final backslashes are great for making pipelines more readable:

```bash
$ cut -f1 grades \
  | sort \
  | uniq -c \
  | sort -nr \
  | head -n1 \
  | cut -c9
```

A leading backslash before an alias escapes the alias, causing the shell to look for a command of the same name, ignoring any shadowing:

```bash
$ alias less="less -c"        Define an alias
$ less myfile                 Run the alias, which invokes less -c
$ \less myfile                Run the standard less command, not the alias
```

### Locating Programs to Be Run

```bash
$ ls -l /bin/ls
-rwxr-xr-x 1 root root 133792 Jan 18  2018 /bin/ls

$ cd /bin
$ ls ls
ls
```

```bash
$ echo $PATH
/home/smith/bin:/usr/local/bin:/usr/bin:/bin:/usr/games:/usr/lib/java/bin
```

 ```bash
 $ echo $PATH | tr : "\n"
 /home/smith/bin
 /usr/local/bin
 /usr/bin
 /bin
 /usr/games
 /usr/lib/java/bin
 ```

To locate a program in your search path:

```bash
$ which cp
/bin/cp
$ which which
/usr/bin/which
```

The more powerful (and verbose) `type` command, a shell builtin that also locates aliases, functions, and shell builtins:

```bash
$ type cp
cp is hashed (/bin/cp)
$ type ll
ll is aliased to ‘/bin/ls -l’
$ type type
type is a shell builtin
```

When the shell searches for a command by name, it checks if that name is an alias before checking the search path.

### Environments and Initialization Files, the Short Version

```bash
$ ls $HOME
apple   banana   carrot
$ ls -a $HOME
.bashrc   apple   banana    carrot
```

```.bashrc
# Set the search path
PATH=$HOME/bin:/usr/local/bin:/usr/bin:/bin
# Set the shell prompt
PS1='$ '
# Set your preferred text editor
EDITOR=emacs
# Start in my work directory
cd $HOME/Work/Projects
# Define an alias
alias g=grep
# Offer a hearty greeting
echo "Welcome to Linux, friend!"
```

Force a running shell to reread and execute *$HOME/.bashrc* with either of the following commands:

```bash
$ source $HOME/.bashrc                 Uses the builtin "source" command
$ . $HOME/.bashrc                      Uses a dot
```

> In real life, do not put all of your shell configuration in *$HOME/.bashrc*.
