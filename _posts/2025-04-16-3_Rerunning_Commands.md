---
title: 3 Rerunning Commands 
date: 2025-04-16 15:50:00 +0800 
categories: [efficient-linux] 
tags: [Linux,Command]
---
# 3. Rerunning Commands

> All the advice in this book will serve you better if you can type quickly. No matter how knowledgeable you are, if you type 40 words per minute and your equally knowledgeable friend types 120, they’re set up to work three times as fast as you. Search the web for “typing speed test” to measure your speed, then search for “typing tutor” and build a lifelong skill. Try to reach 100 words per minute. It’s worth the effort.
>
> Linux Command Line Program: gtypist

## Viewing the command History

```bash
$ history
 1000  cd $HOME/Music
 1001  ls
 1002  mv jazz.mp3 jazzy-song.mp3
 1003  play jazzy-song.mp3
 ⋮                                      Omitting 477 lines
 1481  cd
 1482  firefox https://google.com
 1483  history                         Includes the command you just ran
```

```bash
$ history 3                            Print the 3 most recent commands
 1482  firefox https://google.com
 1483  history
 1484  history 3
```

```bash
$ history | less                      Earliest to latest entry
$ history | sort -nr | less           Latest to earliest entry
```

```bash
$ history | grep -w cd
 1000  cd $HOME/Music
 1092  cd ..
 1123  cd Finances
 1375  cd Checking
 1481  cd
 1485  history | grep -w cd
```

```bash
# To clear (delete) the history for the current shell:
$ history -c
```

## Recalling Commands from the History

### Cursoring Through History

up arrow key

down arrow key

Enter to run it.

> On a full-sized American QWERTY keyboard, I place my right ring finger on the up arrow and my right index finger on Enter to tap both keys efficiently. (Try it.)

```bash
$ echo $HISTSIZE
500
$ HISTSIZE=10000
```

>  Store unlimited commands by setting the value to `-1`.

```bash
$ HISTCONTROL=ignoredups
```

If the value is `ignoredups` (which I recommend), then repeated commands are not appended if they are consecutive.

Whenever an interactive shell exits, it writes its history to the file *$HOME/.bash_history* or whatever path is stored in the shell variable `HISTFILE`:

```bash
$ echo $HISTFILE
/home/smith/.bash_history
```

The variable `HISTFILESIZE` controls how many lines of history are written to the file. 

If you change `HISTSIZE` to control the size of the history in memory, consider updating `HISTFILESIZE` as well:

```bash
$ echo $HISTFILESIZE
500
$ HISTFILESIZE=10000
```

### History Expansion

Two exclamation points in a row (“bang bang”) evaluates to the immediately previous command:

```bash
$ echo Efficient Linux
Efficient Linux
$ !!                            "Bang bang" = previous command
echo Efficient Linux            The shell helpfully prints the command being run
Efficient Linux
```

To refer to the most recent command that began with a certain string, place an exclamation point in front of that string:

```bash
$ !grep
grep Perl animals.txt
alpaca	Intermediate Perl	2012	Schwartz, Randal
```

To refer to the most recent command that contained a given string *somewhere*, not just at the beginning of the command, surround the string with question marks:

```bash
$ !?grep?
history | grep -w cd
 1000  cd $HOME/Music
 1092  cd ..
⋮
```

```bash
$ history | grep hosts
 1203  cat /etc/hosts
$ !1203                         The command at position 1203
cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       example.oreilly.com
::1             example.oreilly.com
```

```bash
$ history
 4197  cd /tmp/junk
 4198  rm *
 4199  head -n2 /etc/hosts
 4199  cd
 4200  history
$ !-3                         The command you executed three commands ago
head -n2 /etc/hosts
127.0.0.1       localhost
127.0.1.1       example.oreilly.com
```

```bash
$ !-3:p
head -n2 /etc/hosts              Printed, not executed

$ !-3:p
head -n2 /etc/hosts              Printed, not executed, and appended to history
$ !!                             Run the command for real
head -n2 /etc/hosts              Printed and then executed
127.0.0.1       localhost
127.0.1.1       example.oreilly.com
```

```bash
$ ls -l /etc | head -n3       Run any command
total 1584
drwxr-xr-x  2 root     root       4096 Jun 16 06:14 ImageMagick-6/
drwxr-xr-x  7 root     root       4096 Mar 19  2020 NetworkManager/

$ echo "!!" | wc -w           Count the words in the previous command
echo "ls -l /etc | head -n3" | wc -w
6
```

```bash
# History Expressions Don’t Appear in the Command History
$ ls               Run any command
hello.txt
$ cd Music         Run some other command
$ !-2              Use history expansion
ls
song.mp3
$ history          View the history
 1000  ls
 1001  cd Music
 1002  ls          "ls" appears in the history, not "!-2"
 1003  history
```

### Never Delete the Wrong File Again 

```bash
$ alias rm='rm -i'                  Often found in a shell configuration file
$ rm *.txt
/bin/rm: remove regular file 'a.txt'? y
/bin/rm: remove regular file 'b.txt'? y
/bin/rm: remove regular file 'c.txt'? y
```

1. *Verify*. Before running `rm`, run `ls` with the desired pattern to see which files match.

   ```bash
   $ ls *.txt
   a.txt   b.txt   c.txt
   ```

2. *Delete*. If the output of `ls` looks correct, run `rm !$` to delete the same files that were matched.

   ```bash
   $ rm !$
   rm *.txt
   ```

   `!$` (“bang dollar”) means the final word that you typed in the previous command.

```bash
$ head myfile.txt
(first 10 lines of the file appear)
$ rm !$
rm myfile.txt
```

```bash
$ ls *.txt *.o *.log
a.txt   b.txt   c.txt   main.o   output.log   parser.o
$ rm !* 
rm *.txt *.o *.log
```

`!*`  (Bang Star) matches all arguments you typed in the previous command.

### Incremental Search of Command History

1. At the shell prompt, press Ctrl-R (the *R* stands for reverse incremental search).
2. Start typing *any part* of a previous command—beginning, middle, or end.
3. With each character you type, the shell displays the most recent historical command that matches your typing so far.
4. When you see the command you want, press Enter to run it.

Press `Ctrl-R` a second time. This keystroke causes the shell to jump to the *next* matching command in the history.



Here are a few more tricks with incremental search:

- To recall the most recent string that you searched for and executed, begin by pressing Ctrl-R twice in a row.
- To stop an incremental search and continue working on the current command, press the Escape key, or Ctrl-J, or any key for command-line editing, such as the left or right arrow key.
- To quit an incremental search and clear the command line, press Ctrl-G or Ctrl-C.

## Command-Line Editing

### Cursoring Within a Command

Cursor keys for simple command-line editing:

| Keystroke          | Action                                  |
| :----------------- | :-------------------------------------- |
| Left arrow         | Move left by one character              |
| Right arrow        | Move right by one character             |
| Ctrl + left arrow  | Move left by one word                   |
| Ctrl + right arrow | Move right by one word                  |
| Home               | Move to beginning of command line       |
| End                | Move to end of command line             |
| Backspace          | Delete one character before the cursor  |
| Delete             | Delete one character beneath the cursor |

### History Expansion with Carets

```bash
$ md5sum *.jg | cut -c1-32 | sort | uniq -c | sort -nr
md5sum: '*.jg': No such file or directory
$ ^jg^jpg
$ ^jg^jpg
md5sum *.jpg | cut -c1-32 | sort | uniq -c | sort -nr
⋮
```

> Notice that the shell helpfully prints the new command before executing it, which is standard behavior for history expansion.

```bash
s/source/target/

$ !!:s/jg/jpg/
$ !md5sum:s/jg/jpg/
```

### Emacs- or Vim-Style Command-Line Editing

Vim-style editing:

```bash
$ set -o vi
```

Emacs-style editing:

```bash
$ set -o emacs
```

Keystrokes for Emacs- or Vim-style editing:

| Action                                                       | Emacs                      | Vim    |
| :----------------------------------------------------------- | :------------------------- | :----- |
| Move forward by one character                                | Ctrl-f                     | l      |
| Move backward by one character                               | Ctrl-b                     | h      |
| Move forward by one word                                     | Meta-f                     | w      |
| Move backward by one word                                    | Meta-b                     | b      |
| Move to beginning of line                                    | Ctrl-a                     | 0      |
| Move to end of line                                          | Ctrl-e                     | $      |
| Transpose (swap) two characters                              | Ctrl-t                     | xp     |
| Transpose (swap) two words                                   | Meta-t                     | *n/a*  |
| Capitalize word (uppercase first letter)                     | Meta-c                     | *n/a*  |
| Uppercase to end of word                                     | Meta-u                     | *n/a*  |
| Lowercase to end of word                                     | Meta-l                     | *n/a*  |
| Change case of the current character                         | *n/a*                      | ~      |
| Insert the next character verbatim, including control characters | Ctrl-v                     | Ctrl-v |
| Delete forward by one character                              | Ctrl-d                     | x      |
| Delete backward by one character                             | Backspace *or* Ctrl-h      | X      |
| Cut forward by one word                                      | Meta-d                     | dw     |
| Cut backward by one word                                     | Meta-Backspace *or* Ctrl-w | db     |
| Cut from cursor to beginning of line                         | Ctrl-u                     | d^     |
| Cut from cursor to end of line                               | Ctrl-k                     | D      |
| Delete the entire line                                       | Ctrl-e Ctrl-u              | dd     |
| Paste (yank) the most recently deleted text                  | Ctrl-y                     | p      |
| Paste (yank) the next deleted text (after a previous yank)   | Meta-y                     | *n/a*  |
| Undo the previous editing operation                          | Ctrl-_                     | u      |
| Undo all edits made so far                                   | Meta-r                     | U      |
| Switch from insertion mode to command mode                   | *n/a*                      | Escape |
| Switch from command mode to insertion mode                   | *n/a*                      | i      |
| Abort an edit operation in progress                          | Ctrl-g                     | *n/a*  |
| Clear the display                                            | Ctrl-l                     | Ctrl-l |
| Move ‘back’ through the history list, fetching the previous command. | Ctrl-p                     |        |
| Move ‘forward’ through the history list, fetching the next command. | Ctrl-n                     |        |

https://www.gnu.org/software/bash/manual/html_node/Bindable-Readline-Commands.html

https://catonmat.net/ftp/bash-vi-editing-mode-cheat-sheet.pdf