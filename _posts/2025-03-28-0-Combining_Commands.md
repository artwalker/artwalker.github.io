---
title: 0 Combining Commands
date: 2025-03-26 13:15:26 +0800
categories: [efficient-linux]
tags: [Linux,Command]
---

# 1. Combining Commands

>[BookSite](https://learning.oreilly.com/library/view/efficient-linux-at/9781098113391/)

## Six Commands to Get You Started

### Command 1: wc

```bash
$ wc animals.txt
 7 51 325 animals.txt # 7 lines, 51 words, 325 characters including invisible newline character that ends each line
$ wc -l animals.txt
7 animals.txt
$ wc -w animals.txt
51 animals.txt
$ wc -c animals.txt
325 animals.txt

# How many files are visible in my current directory?
$ ls -l
animals.txt
myfile
myfile2
test.py
$ ls -l | wc -l
4

# Report the number of words in the output of wc
$ wc animals.txt
 7 51 325 animals.txt
$ wc animals.txt | wc -w
4
$ wc animals.txt | wc -w | wc
 1 1 2
# line "4" ends with an invisible newline character
```

### Command 2: head

```bash
#### Print the first three lines
$ head -n3 animals.txt
#### defaults 10 lines
$ head -n3 animals.txt | wc -w
20
#### list the first five filenames
$ ls /bin | head -n5
```

### Command 3: cut

```bash
#### print one or more columns from a file
$ cut -f2 animals.txt
Programming Python
SSH, The Secure Shell
Intermediate Perl
MySQL High Availability
Linux in a Nutshell
Cisco IOS in a Nutshell
Writing Word Macros
$ cut -f2 animals.txt|head -n3
Programming Python
SSH, The Secure Shell
Intermediate Perl
$ cut -f1,3 animals.txt|head -n3
python	2010
snail	2005
alpaca	2012
$ cut -f2-4 animals.txt|head -n3
Programming Python	2010	Lutz, Mark
SSH, The Secure Shell	2005	Barrett, Daniel
Intermediate Perl	2012	Schwartz, Randal
#### using `-c` character position
$ cut -c1-3 animals.txt
pyt
sna
alp
rob
hor
don
ory
$ cut -f4 animals.txt
Lutz, Mark
Barrett, Daniel
Schwartz, Randal
⋮
#### using '-d' to change separator character
```bash
$ cut -f4 animals.txt|cut -d, -f1
Lutz
Barrett
Schwartz
⋮
```

### Command 4: grep

```bash
$ grep Nutshell animals.txt
horse	Linux in a Nutshell	2009	Siever, Ellen
donkey	Cisco IOS in a Nutshell	2005	Boney, James
$ grep -v Nutshell animals.txt
python	Programming Python	2010	Lutz, Mark
snail	SSH, The Secure Shell	2005	Barrett, Daniel
alpaca	Intermediate Perl	2012	Schwartz, Randal
robin	MySQL High Availability	2014	Bell, Charles
oryx	Writing Word Macros	1999	Roman, Steven
#### -v : don't match a given string

$ grep Perl *.txt
animals.txt:alpaca      Intermediate Perl       2012    Schwartz, Randal
essay.txt:really love the Perl programming language, which is
essay.txt:languages such as Perl, Python, PHP, and Ruby

$ ls -l /usr/lib | cut -c1
d
d
d
-
-
⋮
#### know how many subdirectories are in the large directory /usr/lib

$ ls -l /usr/lib | cut -c1 | grep d
d
d
d
⋮

$ ls -l /usr/lib | cut -c1 | grep d | wc -l
145
```

### Command 5: sort

```bash
$ sort animals.txt
alpaca	Intermediate Perl	2012	Schwartz, Randal
donkey	Cisco IOS in a Nutshell	2005	Boney, James
horse	Linux in a Nutshell	2009	Siever, Ellen
oryx	Writing Word Macros	1999	Roman, Steven
python	Programming Python	2010	Lutz, Mark
robin	MySQL High Availability	2014	Bell, Charles
snail	SSH, The Secure Shell	2005	Barrett, Daniel

$ sort -r animals.txt
snail	SSH, The Secure Shell	2005	Barrett, Daniel
robin	MySQL High Availability	2014	Bell, Charles
python	Programming Python	2010	Lutz, Mark
oryx	Writing Word Macros	1999	Roman, Steven
horse	Linux in a Nutshell	2009	Siever, Ellen
donkey	Cisco IOS in a Nutshell	2005	Boney, James
alpaca	Intermediate Perl	2012	Schwartz, Randal

$ cut -f3 animals.txt
2010
2005
2012
2014
2009
2005
1999
$ cut -f3 animals.txt | sort -n
1999
2005
2005
2009
2010
2012
2014
$ cut -f3 animals.txt | sort -nr
2014
2012
2010
2009
2005
2005
1999

$ cut -f3 animals.txt | sort -nr | head -n1
2014

> Print the maximum value by piping the data to:
... | sort -nr | head -n1
> Print the minimum value:
... | sort -n | head -n1

$ head -n5 /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
smith:x:1000:1000:Aisha Smith,,,:/home/smith:/bin/bash
jones:x:1001:1001:Bilbo Jones,,,:/home/jones:/bin/bash
$ head -n5 /etc/passwd | cut -d: -f1
root
daemon
bin
smith
jones
$ head -n5 /etc/passwd | cut -d: -f1 | sort
bin
daemon
jones
root
smith
$ cat /etc/passwd | cut -d: -f1 | sort

$ cut -d: -f1 /etc/passwd | grep -w jones
jones
$ cut -d: -f1 /etc/passwd | grep -w rutabaga
```

### command 6: uniq

```bash
$ cat letters
A
A
A
B
B
A
C
C
C
C
$ uniq letters
A
B
A
C
$ uniq -c leeters
      3 A
      2 B
      1 A
      4 C

$ cat grades
C	Geraldine
B	Carmine
A	Kayla
A	Sophia
B	Haresh
C	Liam
B	Elijah
B	Emma
A	Olivia
D	Noah
F	Ava
$ cut -f1 grades | sort
A
A
A
B
B
B
B
C
C
D
F
$ cut -f1 grades | sort | uniq -c
      3 A
      4 B
      2 C
      1 D
      1 F
$ cut -f1 grades | sort | uniq -c | sort -nr
      4 B
      3 A
      2 C
      1 F
      1 D
$ cut -f1 grades | sort | uniq -c | sort -nr | head -n1 | cut -c9
B
```

### Detecting Duplicate Files

md5sum : examine a file's contents and compute a 32-charater string called a checksum

```bash
$ md5sum image001.jpg
146b163929b6533f02e91bdf21cb9563  image001.jpg
$ md5sum image001.jpg image002.jpg image003.jpg
146b163929b6533f02e91bdf21cb9563  image001.jpg
63da88b3ddde0843c94269638dfa6958  image002.jpg
146b163929b6533f02e91bdf21cb9563  image003.jpg
$ md5sum *.jpg | cut -c1-32 | sort
1258012d57050ef6005739d0e6f6a257
146b163929b6533f02e91bdf21cb9563
146b163929b6533f02e91bdf21cb9563
17f339ed03733f402f74cf386209aeb3
⋮
$ md5sum *.jpg | cut -c1-32 | sort | uniq -c
      1 1258012d57050ef6005739d0e6f6a257
      2 146b163929b6533f02e91bdf21cb9563
      1 17f339ed03733f402f74cf386209aeb3
      ⋮
$ md5sum *.jpg | cut -c1-32 | sort | uniq -c | sort -nr
      3 f6464ed766daca87ba407aede21c8fcc
      2 c7978522c58425f6af3f095ef1de1cd5
      2 146b163929b6533f02e91bdf21cb9563
      1 d8ad913044a51408ec1ed8a204ea9502
      ⋮
$ md5sum *.jpg | cut -c1-32 | sort | uniq -c | sort -nr | grep -v "      1 "
      3 f6464ed766daca87ba407aede21c8fcc
      2 c7978522c58425f6af3f095ef1de1cd5
      2 146b163929b6533f02e91bdf21cb9563
$ md5sum *.jpg | grep 146b163929b6533f02e91bdf21cb9563
146b163929b6533f02e91bdf21cb9563  image001.jpg
146b163929b6533f02e91bdf21cb9563  image003.jpg
$ md5sum *.jpg | grep 146b163929b6533f02e91bdf21cb9563 | cut -c35-
image001.jpg
image003.jpg
```

## Introducing the Shell

### Pattern Matching for Filenames

```bash
$ grep Linux chapter* 
= $ grep Linux chapter1 chapter2 chapter3 ...

$ grep Linux chapter?
$ grep Linux chapter??
$ grep Linux chapter[12345]
$ grep Linux chapter[1-5]
$ grep Linux chapter*[02468]
$ ls [A-Z]*_*@
$ ls -l /etc/*.conf
```
1. the shell performs the pattern matching
2. shell pattern matching applies only to file and directory paths
3. Some Linux commands such as grep, sed, awk perform their own brands of pattern matching
4. All programs that accept filenames as arguments automaticall work with paatern matching, even for programs and scripts you write yourself

### Evaluating Variables

```bash
$ printenv HOME
/home/smith
$ printenv USER
smith
$ echo My name is $USER and my files are in $HOME    Evaluating variables
My name is smith and my files are in /home/smith
$ echo ch*ter9                                       Evaluating a pattern
chapter9

$ work=$HOME/Projects
$ cd $work
$ pwd
/home/smith/Projects

$ cp myfile $work
$ ls $work
myfile

# When defining a variable, no spaces are permitted around the equals sign.

# the shell evaluates $HOME before running echo. From echo's perspective:
$ echo /home/smith

# The shell evaluates the variables in a command-as well as patterns and other shell constructs-before executing the command.

$ ls
mammals reptiles
$ ls mammals
lizard.txt snake.txt
$ mv mammals/*.txt reptiles = $ mv mammals/lizard.txt mammals/snake.txt reptiles
$ echo mammals/*.txt
mammals/lizard.txt mammals/snake.txt
$ FILES="lizard.txt snake.txt"
$ mv mammals/$FILES reptiles = $ mv mammals/lizard.txt snake.txt reptiles
$ echo mammals/$FILES
mammals/lizard.txt snake.txt

$ FILES="lizard.txt snake.txt"
$ for f in $FILES; do
      mv mammals/$f reptiles
  done
```

### Shortening Commands with Aliases

```bash
$ alias g=grep                 A command with no arguments
$ alias ll="ls -l"             A command with arguments: quotes are required

$ ll                                            Runs "ls -l"
-rw-r--r-- 1 smith smith 325 Jul  3 17:44 animals.txt
$ g Nutshell animals.txt                        Runs "grep Nutshell animals.txt"
horse   Linux in a Nutshell     2009    Siever, Ellen
donkey  Cisco IOS in a Nutshell 2005    Boney, James

$ alias less="less -c"

$ alias
alias g='grep'
alias ll='ls -l'

$ alias g
alias g='grep'

$ unalias g
```

### Redirecting Input and Output

```bash
$ grep Perl animals.txt > outfile                      (displays no output)
$ cat outfile
alpaca	Intermediate Perl	2012	Schwartz, Randal

$ grep Perl animals.txt > outfile              Create or overwrite outfile
$ echo There was just one match >> outfile     Append to outfile
$ cat outfile
alpaca	Intermediate Perl	2012	Schwartz, Randal
There was just one match

$ wc animals.txt                            Reading from a named file
  7  51 325 animals.txt
$ wc < animals.txt                          Reading from redirected stdin
  7  51 325

In addition to stdout, there is also stderr (pronounced “standard error” or “standard err”), a second stream of output that is traditionally reserved for error messages.
The streams stderr and stdout look identical on the display, but internally they are separate. 
You can redirect stderr with the symbol 2> followed by a filename:
$ cp nonexistent.txt file.txt 2> errors
$ cat errors
cp: cannot stat 'nonexistent.txt': No such file or directory

and append stderr to a file with 2>> followed by a filename:
$ cp nonexistent.txt file.txt 2> errors
$ cp another.txt file.txt 2>> errors
$ cat errors
cp: cannot stat 'nonexistent.txt': No such file or directory
cp: cannot stat 'another.txt': No such file or directory

To redirect both stdout and stderr to the same file, use &> followed by a filename:
$ echo This file exists > goodfile.txt               Create a file
$ cat goodfile.txt nonexistent.txt &> all.output
$ cat all.output
This file exists
cat: nonexistent.txt: No such file or directory

$ wc < animals.txt > count
$ cat count
  7  51 325

$ grep Perl < animals.txt | wc > count
$ cat count
      1       6      47
```

### Disabling Evaluation with Quotes and Escapes

```bash
$ cat Efficient Linux Tips.txt
cat: Efficient: No such file or directory
cat: Linux: No such file or directory
cat: Tips.txt: No such file or directory

$ cat 'Efficient Linux Tips.txt'
$ cat "Efficient Linux Tips.txt"
$ cat Efficient\ Linux\ Tips.txt

$ echo '$HOME'
$HOME

$ echo "Notice that $HOME is evaluated"                  Double quotes
Notice that /home/smith is evaluated
$ echo 'Notice that $HOME is not'                        Single quotes
Notice that $HOME is not

$ echo \$HOME
$HOME

$ echo "The value of \$HOME is $HOME"
The value of $HOME is /home/smith

$ echo 'The value of \$HOME is $HOME'
The value of \$HOME is $HOME

$ echo "This message is \"sort of\" interesting"
This message is "sort of" interesting

$ echo "This is a very long message that needs to extend \
onto multiple lines"
This is a very long message that needs to extend onto multiple lines

$ cut -f1 grades \
  | sort \
  | uniq -c \
  | sort -nr \
  | head -n1 \
  | cut -c9

$ alias less="less -c"        Define an alias
$ less myfile                 Run the alias, which invokes less -c
$ \less myfile                Run the standard less command, not the alias
```