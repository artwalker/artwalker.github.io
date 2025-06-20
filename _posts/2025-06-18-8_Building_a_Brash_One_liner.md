---
title: 8 Building a Brash One-Liner
date: 2025-06-20 12:54:00 +0800 
categories: [efficient-linux] 
tags: [Linux,Command]
---
# 8. Building a Brash One-Liner

## Get Ready to Be Brash

### Be Flexible
```bash
$ echo $(ls *.jpg)
$ bash -c 'ls *.jpg'
$ cat <(ls *.jpg)
$ find . -maxdepth 1 -type f -name \*.jpg -print
$ ls > tmp && grep '\.jpg$' tmp && rm -f tmp
$ paste <(echo ls) <(echo \*.jpg) | bash
$ bash -c 'exec $(paste <(echo ls) <(echo \*.jpg))'
$ echo 'monkey *.jpg' | sed 's/monkey/ls/' | bash
$ python -c 'import os; os.system("ls *.jpg")'
```

### Think About Where to Start
```bash
$ echo {A..Z} | awk '{print $(17)}'
Q
$ echo {A..Z} | sed 's/ //g' | cut -c17
Q
```

```bash
$ echo 2021-{01..12}-01 | xargs -n1 date +%B -d
January
February
March
⋮
December
```

```bash
$ ls | awk '{print "echo -n", $0, "| wc -c"}'
echo -n "animals.txt" | wc -c
echo -n "cartoon-mascots.txt | wc -c"
⋮
echo -n "zebra-stripes.txt | wc -c"
```

```bash
$ ls | awk '{print "echo -n", $0, "| wc -c"}' | bash | sort -nr | head -n1
23
```
The general principle is the same: figure out your starting data and manipulate it to fit your needs.
### Know Your Testing Tools
**Use command history and command-line editing.**
* Don’t retype commands while you experiment. Use techniques from Chapter 3 to recall previous commands, tweak them, and run them.

**Add echo to test your expressions.**
* If you aren’t sure how an expression will evaluate, print it with echo beforehand to see the evaluated results on stdout.

**Use ls or add echo to test destructive commands.**
* If your command invokes rm, mv, cp, or other commands that might overwrite or remove files, place echo in front of them to confirm which files will be affected. (So, instead of executing rm, execute echo rm.) Another safety tactic is to replace rm with ls to list files that would be removed.

**Insert a tee to view intermediate results.**
* If you want to view the output (stdout) in the middle of a long pipeline, insert the tee command to save output to a file for examination. The following command saves the output from command3 in the file outfile, while piping that same output to command4:
```bash
$ command1 | command2 | command3 | tee outfile | command4 | command5
$ less outfile
```
## Inserting a Filename into a Sequence
```bash
$ ls
ch01.asciidoc  ch03.asciidoc  ch05.asciidoc  ch07.asciidoc  ch09.asciidoc
ch02.asciidoc  ch04.asciidoc  ch06.asciidoc  ch08.asciidoc  ch10.asciidoc

$ paste <(seq -w 10 -1 3 | sed 's/\(.*\)/ch\1.asciidoc/') \
        <(seq -w 11 -1 4 | sed 's/\(.*\)/ch\1.asciidoc/') \
  | sed 's/^/mv /' \
  | bash
  
$ ls ch*.asciidoc
ch01.asciidoc  ch04.asciidoc  ch06.asciidoc  ch08.asciidoc  ch10.asciidoc
ch02.asciidoc  ch05.asciidoc  ch07.asciidoc  ch09.asciidoc  ch11.asciidoc
```

## Checking Matched Pairs of Files
```bash
$ ls
bald_eagle.jpg  blue_jay.jpg  cardinal.txt  robin.jpg  wren.jpg
bald_eagle.txt  cardinal.jpg  oriole.txt    robin.txt  wren.txt

$ ls *.jpg | cut -d. -f1
bald_eagle
blue_jay
cardinal
robin
wren
$ ls *.txt | cut -d. -f1
bald_eagle
cardinal
oriole
robin
wren

$ diff <(ls *.jpg | cut -d. -f1) <(ls *.txt | cut -d. -f1)
2d1
< blue_jay
3a3
> oriole

$ diff <(ls *.jpg | cut -d. -f1) <(ls *.txt | cut -d. -f1) \
  | grep '^[<>]'
< blue_jay
> oriole

$ diff <(ls *.jpg | cut -d. -f1) <(ls *.txt | cut -d. -f1) \
  | grep '^[<>]' \
  | awk '/^</{print $2 ".jpg"} /^>/{print $2 ".txt"}'
blue_jay.jpg
oriole.txt

$ diff <(ls *.jpg | sed 's/\.[^.]*$//') \
       <(ls *.txt | sed 's/\.[^.]*$//') \
  | grep '^[<>]' \
  | awk '/</{print $2 ".jpg"} />/{print $2 ".txt"}'
blue_jay.txt
oriole.jpg
yellow.canary.txt
```

```bash
$ ls *.{jpg,txt} \
  | sed 's/\.[^.]*$//' \
  | uniq -c
      2 bald_eagle
      1 blue_jay
      2 cardinal
      1 oriole
      2 robin
      2 wren
      1 yellow.canary
      
$ ls *.{jpg,txt} \
  | sed 's/\.[^.]*$//' \
  | uniq -c \
  | awk '/^ *1 /{print $2}'
blue_jay
oriole
yellow.canary

$ ls *.{jpg,txt} \
  | sed 's/\.[^.]*$//' \
  | uniq -c \
  | awk '/^ *1 /{print $2 ".*"}'
blue_jay.*
oriole.*
yellow.canary.*

$ ls -1 $(ls *.{jpg,txt} \
  | sed 's/\.[^.]*$//' \
  | uniq -c \
  | awk '/^ *1 /{print $2 ".*"}')
blue_jay.jpg
oriole.txt
yellow.canary.jpg
```

## Generating a CDPATH from Your Home Directory
```bash
$ (cd && ls -d */)
Family/  Finances/  Linux/  Music/  Work/
```

```bash
$ (cd && ls -d */) | sed 's/^/$HOME\//g'
$HOME/Family/
$HOME/Finances/
$HOME/Linux/
$HOME/Music/
$HOME/Work/
```

```bash
$ (cd && ls -d */) | sed 's@^@$HOME/@g'
$HOME/Family/
$HOME/Finances/
$HOME/Linux/
$HOME/Music/
$HOME/Work/
```

```bash
$ (cd && ls -d */) | sed -e 's@^@$HOME/@' -e 's@/$@@'
$HOME/Family
$HOME/Finances
$HOME/Linux
$HOME/Music
$HOME/Work
```

```bash
$ echo $(cd && ls -d */ | sed -e 's@^@$HOME/@' -e 's@/$@@')
$HOME/Family $HOME/Finances $HOME/Linux $HOME/Music $HOME/Work
```

```bash
$ echo '$HOME' \
       $(cd && ls -d */ | sed -e 's@^@$HOME/@' -e 's@/$@@') \
       ..
$HOME $HOME/Family $HOME/Finances $HOME/Linux $HOME/Music $HOME/Work ..
```

```bash
$ echo '$HOME' \
       $(cd && ls -d */ | sed -e 's@^@$HOME/@' -e 's@/$@@') \
       .. \
  | tr ' ' ':'
```

```bash
$ echo 'CDPATH=$HOME' \
       $(cd && ls -d */ | sed -e 's@^@$HOME/@' -e 's@/$@@') \
       .. \
  | tr ' ' ':'
CDPATH=$HOME:$HOME/Family:$HOME/Finances:$HOME/Linux:$HOME/Music:$HOME/Work:..
```

## Generating Test Files
```bash
$ shuf /usr/share/dict/words | head -n3
evermore
shirttail
tertiary
$ shuf /usr/share/dict/words | head -n3
interactively
opt
perjurer
```

```bash
$ echo $RANDOM $RANDOM $RANDOM
7855 11134 262
```

```bash
$ shuf -n $RANDOM /usr/share/dict/words | wc -l
9922
$ shuf -n $RANDOM /usr/share/dict/words | wc -l
32465
```

```bash
$ pwgen
eng9nooG ier6YeVu AhZ7naeG Ap3quail poo2Ooj9 OYiuri9m iQuash0E voo3Eph1
IeQu7mi6 eipaC2ti exah8iNg oeGhahm8 airooJ8N eiZ7neez Dah8Vooj dixiV1fu
Xiejoti6 ieshei2K iX4isohk Ohm5gaol Ri9ah4eX Aiv1ahg3 Shaew3ko zohB4geu
⋮
```

```bash
$ pwgen -N1 10
ieb2ESheiw
```

```bash
$ echo $(pwgen -N1 10).txt
ohTie8aifo.txt
```

```bash
$ mkdir -p /tmp/randomfiles && cd /tmp/randomfiles
$ shuf -n $RANDOM -o $(pwgen -N1 10).txt /usr/share/dict/words
```

```bash
$ ls                           List the new file
Ahxiedie2f.txt
$ wc -l Ahxiedie2f.txt         How many lines does it contain?
13544 Ahxiedie2f.txt
$ head -n3 Ahxiedie2f.txt      Peek at the first few lines
saviors
guerillas
forecaster
```

```bash
for i in {1..1000}; do
  shuf -n $RANDOM -o $(pwgen -N1 10).txt /usr/share/dict/words
done
```

```bash
$ echo 'shuf -n $RANDOM -o $(pwgen -N1 10).txt /usr/share/dict/words'
shuf -n $RANDOM -o $(pwgen -N1 10).txt /usr/share/dict/words
```

```bash
$ echo 'shuf -n $RANDOM -o $(pwgen -N1 10).txt /usr/share/dict/words' | bash
$ ls
eiFohpies1.txt
```

```bash
$ yes 'shuf -n $RANDOM -o $(pwgen -N1 10).txt /usr/share/dict/words' \
  | head -n 1000 \
  | bash
$ ls
Aen1lee0ir.txt  IeKaveixa6.txt  ahDee9lah2.txt paeR1Poh3d.txt
Ahxiedie2f.txt  Kas8ooJahK.txt  aoc0Yoohoh.txt sohl7Nohho.txt
CudieNgee4.txt  Oe5ophae8e.txt  haiV9mahNg.txt uchiek3Eew.txt
⋮
```

```bash
#  produce random images of size 100 x 100 pixels consisting of multicolored squares:
$ yes 'convert -size 8x8 xc: +noise Random -scale 100x100 $(pwgen -N1 10).png' \
  | head -n 1000 \
  | bash
$ ls
Bahdo4Yaop.png  Um8ju8gie5.png  aing1QuaiX.png  ohi4ziNuwo.png
Eem5leijae.png  Va7ohchiep.png  eiMoog1kou.png  ohnohwu4Ei.png
Eozaing1ie.png  Zaev4Quien.png  hiecima2Ye.png  quaepaiY9t.png
⋮
$ display Bahdo4Yaop.png              View the first image
```

## Generating Empty Files
```bash
$ mkdir /tmp/empties           Create a directory for the files
$ cd /tmp/empties
$ touch file{01..1000}.txt     Generate the files
```

```bash
$ grep '^[a-z]*$' /usr/share/dict/words
a
aardvark
aardvarks
⋮
```

```bash
$ grep '^[a-z]*$' /usr/share/dict/words | shuf | head -n1000
triplicating
quadruplicates
podiatrists
⋮
```

```bash
$ grep '^[a-z]*$' /usr/share/dict/words | shuf | head -n1000 | xargs touch
$ ls
abases             distinctly      magnolia         sadden
abets              distrusts       maintaining      sales
aboard             divided         malformation     salmon
⋮
```
