---
title: 3 Study guide diff and patch  
date: 2024-07-06 21:32:00 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
# diff and patch

### The diff command
You use the diff command to find the differences between two files. On its own, it’s a bit hard to use; instead, use diff -u to find lines that differ in two files:

### Using diff -u
You use the diff -u command to compare two files, line by line, and have the differing lines compared side-by-side in the same output. For an example of what this looks like, see below:
#### Command:
```bash
$ cat menu1.txt 
```
#### Code output:
```bash
Menu1:

Apples
Bananas
Oranges
Pears
```
#### Command:
```bash
$ cat menu2.txt 
```
#### Code output:
```bash
Menu:

Apples
Bananas
Grapes
Strawberries
```
#### Command:
```bash
$ diff -u menu1.txt menu2.txt 
```
#### Code output:
```bash
--- menu1.txt   2019-12-16 18:46:13.794879924 +0900
+++ menu2.txt   2019-12-16 18:46:42.090995670 +0900
@@ -1,6 +1,6 @@
-Menu1:
+Menu:
 
 Apples
 Bananas
-Oranges
-Pears
+Grapes
+Strawberries
```
#### Explaination
1. `--- menu1.txt   2019-12-16 18:46:13.794879924 +0900`: Indicates the filename and modification time of the first file.

2. `+++ menu2.txt   2019-12-16 18:46:42.090995670 +0900`: Indicates the filename and modification time of the second file.

3. `@@ -1,6 +1,6 @@`: Marks a block of differences, indicating where differences occur between the two files. `-1,6` denotes six lines starting from the first line in the original file, and `+1,6` represents the same in the modified file.

4. `-Menu1:`: Represents the content in the original file. `-` signifies deleted lines.

5. `+Menu:`: Represents the modified content in the new file. `+` signifies added lines.

6. `Apples`, `Bananas`: These lines remain unchanged from the original file.

7. `Oranges`, `Pears`: These lines from the original file were removed in the modified file.

8. `Grapes`, `Strawberries`: These lines were added in the modified file.

### The patch command
The patch command is useful for applying file differences. See the example below, which compares two files. The comparison is saved as a .diff file, which is then patched to the original file!
#### Command:
```bash
$ cat hello_world.txt 
```
#### Code output:
```bash
Hello World
```
#### Command:
```bash
$ cat hello_world_long.txt 
```
#### Code output:
```bash
Hello World

It's a wonderful day!
```
#### Command:
```bash
$ diff -u hello_world.txt hello_world_long.txt 
```
#### Code output:
```bash
--- hello_world.txt     2019-12-16 19:24:12.556102821 +0900
+++ hello_world_long.txt        2019-12-16 19:24:38.944207773 +0900
@@ -1 +1,3 @@
 Hello World
+
+It's a wonderful day!
```
#### Command:
```bash
$ diff -u hello_world.txt hello_world_long.txt > hello_world.diff
$ patch hello_world.txt < hello_world.diff 
```
#### Code output:
```bash
patching file hello_world.txt
```
#### Command:
```bash
$ cat hello_world.txt 
```
#### Code output:
```bash
Hello World

It's a wonderful day!
```
#### Explanation
1. `$ diff -u hello_world.txt hello_world_long.txt`: This part represents the execution of the `diff` command to compare `hello_world.txt` and `hello_world_long.txt`.

2. `--- hello_world.txt     2019-12-16 19:24:12.556102821 +0900`: This line shows the filename and the last modification time of the first file.

3. `+++ hello_world_long.txt        2019-12-16 19:24:38.944207773 +0900`: This line shows the filename and the last modification time of the second file.

4. `@@ -1 +1,3 @@`: This is a diff block marker, indicating the difference between the two files. `-1` refers to the first line in the original file, and `+1,3` indicates the first line to the third line in the new file.

5. `Hello World`: This line represents the content in the original file.

6. `+`: Signifies added content.

7. `It's a wonderful day!`: This line represents the added content in the new file.
