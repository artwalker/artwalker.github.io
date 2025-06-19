---
title: 7 More Ways to Run a Command
date: 2025-06-19 14:54:00 +0800 
categories: [efficient-linux] 
tags: [Linux,Command]
---
#  7. More Ways to Run a Command

## List Techniques

### Technique #1: Conditional Lists

```bash
$ cd dir            Enter the directory
$ touch new.txt     Make the file
```

```bash
$ cd dir && touch new.txt
```

```bash
$ cp myfile.txt myfile.safe      Make a backup copy
$ nano myfile.txt                Change the original
$ rm myfile.safe                 Delete the backup
```

```bash
$ cp myfile.txt myfile.safe && nano myfile.txt && rm myfile.safe
```

```bash
$ git add . && git commit -m"fixed a bug" && git push
```

```bash
# the following command tries to enter dir, and if it fails to do so, it creates dir:
$ cd dir || mkdir dir
```

```bash
# If a directory can't be entered, exit with an error code of 1
cd dir || exit 1
```

```bash
$ cd dir || mkdir dir && cd dir || echo "I failed"
```

```bash
$ ls myfile.txt
myfile.txt
$ echo $?                          Print the value of the ? variable
0                                  ls succeeded
$ cp nonexistent.txt somewhere.txt
cp: cannot stat 'nonexistent.txt': No such file or directory
$ echo $?
1                                  cp failed
```

### Technique #2: Unconditional Lists

```bash
$ sleep 7200; cp -a ~/important-files /mnt/backup_drive
```

```bash
$ sleep 300; echo "remember to walk the dog" | mail -s reminder $USER
```

```bash
# Only the exit code of the last command run in the list is assigned to the shell variable ?:
$ mv file1 file2; mv file2 file3; mv file3 file4
$ echo $?
0                           The exit code for "mv file3 file4"
```

## Substitution Techniques

### Technique #3: Command Substitution

```
Title: Carry On Wayward Son
Artist: Kansas
Album: Leftoverture

Carry on my wayward son
There'll be peace when you are done
⋮
```

```bash
$ grep -l "Artist: Kansas" *.txt
carry_on_wayward_son.txt
dust_in_the_wind.txt
belexes.txt
```

```bash
$ mkdir kansas
$ mv carry_on_wayward_son.txt kansas
$ mv dust_in_the_wind.txt kansas
$ mv belexes.txt kansas
```

```bash
# $(any command here)
# $ mv carry_on_wayward_son.txt dust_in_the_wind.txt belexes.txt kansas
$ mv $(grep -l "Artist: Kansas" *.txt) kansas
```

```bash
$ ls eStmt*pdf | tail -n1
$ okular $(ls eStmt*pdf | tail -n1)
```

```bash
$ echo Today is $(date +%A).
Today is Saturday.
$ echo Today is `date +%A`.
Today is Saturday.
```

```bash
$ echo $(date +%A) | tr a-z A-Z                    Single
SATURDAY
echo Today is $(echo $(date +%A) | tr a-z A-Z)!   Nested
Today is SATURDAY!
```

In scripts, a common use of command substitution is to store the output of a command in a variable:
```bash
# VariableName=$(some command here)
$ kansasFiles=$(grep -l "Artist: Kansas" *.txt) 
$ echo "$kansasFiles"
```

### Technique #4: Process Substitution

```bash
$ mkdir /tmp/jpegs && cd /tmp/jpegs
$ touch {1..1000}.jpg
$ rm 4.jpg 981.jpg
```

```bash
$ ls -1 | sort -n | less
1.jpg
2.jpg
3.jpg
5.jpg            4.jpg is missing
⋮
```

```bash
$ ls *.jpg | sort -n > /tmp/original-list
$ seq 1 1000 | sed 's/$/.jpg/' > /tmp/full-list
$ diff /tmp/original-list /tmp/full-list
3a4
> 4.jpg
979a981
> 981.jpg
$ rm /tmp/original-list /tmp/full-list       Clean up afterwards
```

```bash
<(any command here)
# The following expression represents the output of ls -1 | sort -n as if it were contained in a file:
<(ls -1 | sort -n)
$ cat <(ls -1 | sort -n)
1.jpg
2.jpg
⋮
```

```bash
$ cp <(ls -1 | sort -n) /tmp/listing
$ cat /tmp/listing
1.jpg
2.jpg
⋮
```

```bash
ls *.jpg | sort -n
seq 1 1000 | sed 's/$/.jpg/'
```

```bash
$ diff <(ls *.jpg | sort -n) <(seq 1 1000 | sed 's/$/.jpg/')
3a4
> 4.jpg
979a981
> 981.jpg
```

```bash
$ diff <(ls *.jpg | sort -n) <(seq 1 1000 | sed 's/$/.jpg/') \
    | grep '>' \
    | cut -c3-
4.jpg
981.jpg
```

Process substitution is a non-POSIX feature that might be disabled in your shell. To enable non-POSIX features in your current shell, run set +o posix.

## Command-as-String Techniques

### Technique #5: Passing a Command as an Argument to bash

```bash
$ bash -c "ls -l"
-rw-r--r-- 1 smith smith 325 Jul  3 17:44 animals.txt    
```

```bash
$ pwd
/home/smith
$ touch /tmp/badfile                           Create a temporary file
$ bash -c "cd /tmp && rm badfile"
$ pwd
/home/smith                                    Current directory is unchanged
```

```bash
$ sudo echo "New log file" > /var/log/custom.log
bash: /var/log/custom.log: Permission denied
```

```bash
$ sudo bash -c 'echo "New log file" > /var/log/custom.log'
[sudo] password for smith: xxxxxxxx
$ cat /var/log/custom.log
New log file
```

> Remember this technique whenever you pair sudo with redirection.

### Technique #6: Piping a Command to bash

```bash
$ echo "ls -l"
ls -l
$ echo "ls -l" | bash
-rw-r--r-- 1 smith smith 325 Jul  3 17:44 animals.txt
```

```bash
$ ls -1 ??* 
apple
banana
cantaloupe
carrot
⋮
```

```bash
$ mkdir {a..z}
```

```bash
$ ls -1 ??* | sed 's/^\(.\)\(.*\)$/mv \1\2 \1/'
mv apple a
mv banana b
mv cantaloupe c
mv carrot c
⋮
```

```bash
$ ls -1 ??* | sed 's/^\(.\)\(.*\)$/mv \1\2 \1/' | less

$ ls -1 ??* | sed 's/^\(.\)\(.*\)$/mv \1\2 \1/' | bash
```

The steps you just completed are a repeatable pattern:
1. Print a sequence of commands by manipulating strings.
2. View the results with less to check correctness.
3. Pipe the results to bash.

### Technique #7: Executing a String Remotely with ssh

```bash
$ ssh myhost.example.com ls
remotefile1
remotefile2
remotefile3
```

```bash
$ ssh myhost.example.com ls > outfile       Creates outfile on local host
$ ssh myhost.example.com "ls > outfile"     Creates outfile on remote host
```

```bash
$ echo "ls > outfile" | ssh myhost.example.com
```

If you see messages about pseudo-terminals or pseudo-ttys, such as “Pseudo-terminal will not be allocated because stdin is not a terminal,” run ssh with the -T option to prevent the remote SSH server from allocating a terminal:
```bash
$ echo "ls > outfile" | ssh -T myhost.example.com
```

If you see welcome messages that normally appear when you log in (“Welcome to Linux!”) or other unwanted messages, try telling ssh explicitly to run bash on the remote host, and the messages should disappear:
```bash
$ echo "ls > outfile" | ssh myhost.example.com bash
```

### Technique #8: Running a List of Commands with xargs

```bash
$ ls -1
apple
banana
cantaloupe

$ ls -1 | xargs wc -l
3 apple
4 banana
1 cantaloupe
8 total

$ ls -1 | xargs cat
```

```bash
$ find . -type f -name \*.py -print
fruits/raspberry.py
vegetables/leafy/lettuce.py
⋮
```

```bash
$ find . -type f -name \*.py -print0 | xargs -0 wc -l
6 ./fruits/raspberry.py
3 ./vegetables/leafy/lettuce.py
⋮
```

```bash
$ ls | xargs echo                     Fit as many input strings as possible:
apple banana cantaloupe carrot          echo apple banana cantaloupe carrot
$ ls | xargs -n1 echo                 One argument per echo command:
apple                                   echo apple
banana                                  echo banana
cantaloupe                              echo cantaloupe
carrot                                  echo carrot
$ ls | xargs -n2 echo                 Two arguments per echo command:
apple banana                            echo apple banana
cantaloupe carrot                       echo cantaloupe carrot
$ ls | xargs -n3 echo                 Three arguments per echo command:
apple banana cantaloupe                 echo apple banana cantaloupe
carrot                                  echo carrot
```

```bash
# Safety with find and xargs
$ find options... -print0 | xargs -0 options...

$ ls | tr '\n' '\0' | xargs -0 ...
alias ls0="find . -maxdepth 1 -print0"
```

```bash
$ ls | xargs -I XYZ echo XYZ is my favorite food      Use XYZ as a placeholder
apple is my favorite food
banana is my favorite food
cantaloupe is my favorite food
carrot is my favorite food
```

```bash
$ rm *.txt
bash: /bin/rm: Argument list too long

$ find . -maxdepth 1 -name \*.txt -type f -print0 \
  | xargs -0 rm
```

## Process-Control Techniques

### Technique #9: Backgrounding a Command
#### Launching a command in the background
```bash
$ wc -c my_extremely_huge_file.txt &     Count characters in a huge file
[1] 74931                                Cryptic-looking response
$

# success
59837483748 my_extremely_huge_file.txt
[1]+  Done               wc -c my_extremely_huge_file.txt

# fail
[1]+  Exit 1             wc -c my_extremely_huge_file.txt
```

```bash
$ command1 & command2 & command3 &   All 3 commands
[1] 57351                            in background
[2] 57352
[3] 57353
$ command4 & command5 & echo hi      All in background
[1] 57431                            but "echo"
[2] 57432
hi
```
#### Suspending a command and sending it to the background
Press Ctrl-Z to stop the command temporarily (called suspending the command) and return to the shell prompt; 
then type bg to resume running the command in the background.
#### Jobs and job control
 A job is a shell’s unit of work: a single instance of a command running in a shell. Simple commands, pipelines, and conditional lists are all examples of jobs—​basically anything you can run at the command line.
 
A job is more than a Linux process. A job may consist of one process, two processes, or more. A pipeline of six programs, for example, is a single job that includes (at least) six processes. Jobs are a construct of the shell. The Linux operating system doesn’t keep track of jobs, just the underlying processes.

In the following command, the job number is 1 and the process ID is 74931:
```bash
$ wc -c my_extremely_huge_file.txt &
[1] 74931
```

#### Common job-control operations
| Command |                              Meaning                              |
| ------- | ----------------------------------------------------------------- |
| bg      | Move the current suspended job into the background                |
| bg %n   | Move suspended job number n into the background (example: bg %1)  |
| fg      | Move the current background job into the foreground               |
| fg %n   | Move background job number n into the foreground (example: fg %2) |
| kill %n | Terminate background job number n (example: kill %3)              |
| jobs    | View a shell’s jobs                                               |

```bash
$ sleep 20 &                        Run in the background
[1] 126288
$ jobs                              List this shell's jobs
[1]+  Running          sleep 20 &
$
...eventually...
[1]+  Done             sleep 20
#When jobs complete, the Done message might not appear until the next time you press Enter.
```

```bash
$ sleep 20 &                        Run in the background
[1] 126362
$ fg                                Bring into the foreground
sleep 20
...eventually...
$
```

```bash
$ sleep 20                          Run in the foreground
^Z                                  Suspend the job
[1]+  Stopped          sleep 20
$ jobs                              List this shell's jobs
[1]+  Stopped          sleep 20
$ fg                                Bring into the foreground
sleep 20
...eventually...
[1]+  Done             sleep 20
```

```bash
$ sleep 20                          Run in the foreground
^Z                                  Suspend the job
[1]+  Stopped          sleep 20
$ bg                                Move to the background
[1]+ sleep 20 &
$ jobs                              List this shell's jobs
[1]+  Running          sleep 20 &
$
...eventually...
[1]+  Done             sleep 20
```

```bash
$ sleep 100 &                        Run 3 commands in the background
[1] 126452
$ sleep 200 &
[2] 126456
$ sleep 300 &
[3] 126460
$ jobs                               List this shell's jobs
[1]   Running          sleep 100 &
[2]-  Running          sleep 200 &
[3]+  Running          sleep 300 &
$ fg %2                              Bring job 2 into the foreground
sleep 200
^Z                                   Suspend job 2
[2]+  Stopped          sleep 200
$ jobs                               See job 2 is suspended ("stopped")
[1]   Running          sleep 100 &
[2]+  Stopped          sleep 200
[3]-  Running          sleep 300 &
$ kill %3                            Terminate job 3
[3]+  Terminated       sleep 300
$ jobs                               See job 3 is gone
[1]-  Running          sleep 100 &
[2]+  Stopped          sleep 200
$ bg %2                              Resume suspended job 2 in the background
[2]+ sleep 200 &
$ jobs                               See job 2 is running again
[1]-  Running          sleep 100 &
[2]+  Running          sleep 200 &
$
```

#### Output and input in the background
```bash
$ sort /usr/share/dict/words | head -n2 &
[1] 81089
$
```

```bash
$ sort /usr/share/dict/words | head -n2 &
[1] 81089
$ A
A's

[1]+  Done               sort /usr/share/dict/words | head -n2
$
```

```bash
$ sort /usr/share/dict/words | head -n2 > /tmp/results &
[1] 81089
$
[1]+  Done               sort /usr/share/dict/words | head -n2 > /tmp/results
$ cat /tmp/results
A
A's
$
```

```bash
$ cat &
[1] 82455
[1]+  Stopped            cat

$ fg
cat
Here is some input
Here is some input
⋮

# After supplying all input, do any of the following:
#    Continue running the command in the foreground until it completes.
#    Suspend and background the command again by pressing Ctrl-Z followed by bg.
#    End the input with Ctrl-D, or kill the command with Ctrl-C.
```

#### Backgrounding tips
Backgrounding is ideal for commands that take a long time to run, such as text editors during long editing sessions, or any program that opens its own windows. 
For example, programmers can save a lot of time by suspending their text editor rather than exiting. 
 If they suspend the editor (Ctrl-Z), test their code, and resume the editor (fg), they avoiding wasting time unnecessarily.
 
Backgrounding is also great for running a sequence of commands in the background using a conditional list. 
If any command within the list fails, the rest won’t run and the job completes. (Just watch out for commands that read input, since they’ll cause the job to suspend and wait for input.)
```bash
$ command1 && command2 && command3 &
```

### Technique #10: Explicit Subshells
```bash
# simply enclose a command in parentheses and it runs in a subshell:
$ (cd /usr/local && ls)
bin   etc   games   lib   man   sbin   share
$ pwd
/home/smith                   "cd /usr/local" occurred in a subshell
```

```bash
# you want to extract them into a different directory
$ cat package.tar.gz | (mkdir -p /tmp/other && cd /tmp/other && tar xzvf -)

# This technique also works to copy files from one directory dir1 to another existing directory dir2 using two tar processes, one writing to stdout and one reading from stdin:
$ tar czf - dir1 | (cd /tmp/dir2 && tar xvf -)

# The same technique can copy files to an existing directory on another host via SSH:
$ tar czf - dir1 | ssh myhost '(cd /tmp/dir2 && tar xvf -)'
```

```bash
$ echo $BASH_SUBSHELL                  Ordinary execution
0                                      Not a subshell
$ (echo $BASH_SUBSHELL)                Explicit subshell
1                                      Subshell
$ echo $(echo $BASH_SUBSHELL)          Command substitution
1                                      Subshell
$ cat <(echo $BASH_SUBSHELL)           Process substitution
1                                      Subshell
$ bash -c 'echo $BASH_SUBSHELL'        bash -c
0                                      Not a subshell
```

### Technique #11: Process Replacement 
```bash
$ bash                   Run a child shell
$ PS1="Doomed> "         Change the new shell's prompt
Doomed> echo hello       Run any command you like
hello

Doomed> exec ls          ls replaces the child shell, runs, and exits
animals.txt
$                        A prompt from the original (parent) shell
```
Shell scripts sometimes make use of this optimization by running exec on the final command in the script. 

exec has a second ability—​it can reassign stdin, stdout, and/or stderr for the current shell. 
```bash
#!/bin/bash
echo "My name is $USER"                                 > /tmp/outfile
echo "My current directory is $PWD"                     >> /tmp/outfile
echo "Guess how many lines are in the file /etc/hosts?" >> /tmp/outfile
wc -l /etc/hosts                                        >> /tmp/outfile
echo "Goodbye for now"                                  >> /tmp/outfile
```

```bash
#!/bin/bash
# Redirect stdout for this script
exec > /tmp/outfile2
# All subsequent commands print to /tmp/outfile2
echo "My name is $USER"
echo "My current directory is $PWD"
echo "Guess how many lines are in the file /etc/hosts?"
wc -l /etc/hosts
```

```bash
$ cat /tmp/outfile2
My name is smith
My current directory is /home/smith
Guess how many lines are in the file /etc/hosts?
122 /etc/hosts
Goodbye for now
```
## Summary
Common idioms for running commands
| Problem    |  	Solution   |
| --- | --- |
|  Sending stdout from one program to stdin of anothe   |    	Pipelines |
|  Inserting output (stdout) into a command   |  	Command substitution   |
|  Providing output (stdout) to a command that doesn’t read from stdin, but does read disk files  | Process substitution    |
|  Executing one string as a command   |   	`bash -c`, or piping to bash  |
|   Printing multiple commands on stdout and executing them  |  Piping to bash   |
| Executing many similar commands in a row     |    `xargs`, or constructing the commands as strings and piping them to `bash` |
|  Managing commands that depend on one other’s success   |  Conditional lists   |
|   Running several commands at a time  |  Backgrounding   |
|  Running several commands at a time that depend on one another’s success   |  Backgrounding a conditional list  |
|   Running one command on a remote host  | 	Run ssh host command    |
| Changing directory in the middle of a pipeline    |  Explicit subshells   |
| Running a command later    | Unconditional list with `sleep` followed by the command    |
| Redirecting to/from protected files    | Run `sudo bash -c "command > file" `   |