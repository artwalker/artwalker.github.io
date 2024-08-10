---  
title: 33 Writing Code  
date: 2024-07-29 07:59:25 +0800  
categories: [emacs]  
tags: [emacs]  
---
## comment

**M-;**

**M-j**

**M-x comment-region**

**M-x kill-comment Enter**

## Indenting Code

Basic indentation commands


| **Keystrokes** | **Command name**        | **Action**                                        |
| -------------- | ----------------------- | ------------------------------------------------- |
| **C-M-\\**     | **indent-region**       | Indent each line between the cursor and mark.     |
| **M-m**        | **back-to-indentation** | Move to the first nonblank character on the line. |
| **M-^**        | **delete-indentation**  | Join this line to the previous one.               |

**C-x h** (for **mark-whole-buffer**) followed by **C-M-\\**

**M-m** is handy for moving to the beginning of the actual code on a line

As an example of **M-^**, let's say you want the opening curly brace for the **for** statement to appear on the same line as the **for**.

## etags

If you work on large, multifile projects, you will find **etags** to be an enormous help.

**M-!** (for **shell-command**) Then **etags \*.[ch]** Then **M-x visit-tags-table Enter**

**M-**. (for **find-tag**) or C-x 4

A nice feature of **M-**. is that it picks up the word the cursor is on and uses it as the default search string. For example, if your cursor is anywhere on the string **my\_function**, **M-**. uses **my\_function** as the default. Thus, when you are looking at a C statement that calls a function, you can type **M-**. to see the code for that function.

The command **M-x tags-apropos** rounds out the search facilities of **etags**. If you give it a regular expression argument, it opens a `*Tags List*` buffer that contains a list of all tags in the tag table (including names of files as well as functions) that match the regular expression. For example, if you want to find out the names of output routines in a multiple-file C program, you could invoke **tags-apropos** with the argument **print** or **write**.

you can type **M-x list-tags Enter** to list all the tags in the table

## Fonts and Font-lock Mode

**M-x font-lock-mode**

make it the default for all language sessions:

```.emacs
;; Turn on font-locking globally
(global-font-lock-mode t)
```

**M-x list-faces-display** produces a list of the named faces Emacs knows about

You can modify any of those faces with either **M-x modify-face** (a simple prompted "wizard" approach) or **M-x customize-face** (the big fancy interactive approach)
