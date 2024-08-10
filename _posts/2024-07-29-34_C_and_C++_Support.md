---  
title: 34 C and C++ Support  
date: 2024-07-29 07:59:24 +0800  
categories: [emacs]  
tags: [emacs]  
---
You can also put any file in C mode manually by typing **M-x c-mode Enter**. Similarly, you can use **c++-mode** to put a buffer into C++ mode.

## Motion Commands

Advanced C motion commands


| **Keystrokes** | **Command name**             | **Action**                                                                  |
| -------------- | ---------------------------- | --------------------------------------------------------------------------- |
| **M-a**        | **c-beginning-of-statement** | Move to the beginning of the current statement.                             |
| **M-e**        | **c-end-of-statement**       | Move to the end of the current statement.                                   |
| **M-q**        | **c-fill-paragraph**         | If in comment, fill the paragraph, preserving indentations and decorations. |
| **C-M-a**      | **beginning-of-defun**       | Move to the beginning of the body of the function surrounding the point.    |
| **C-M-e**      | **end-of-defun**             | Move to the end of the function.                                            |
| **C-M-h**      | **c-mark-function**          | Put the cursor at the beginning of the function, the mark at the end.       |
| **C-c C-q**    | **c-indent-defun**           | Indent the entire function according to indentation style.                  |
| **C-c C-u**    | **c-up-conditional**         | Move to the beginning of the current preprocessor conditional.              |
| **C-c C-p**    | **c-backward-conditional**   | Move to the previous preprocessor conditional.                              |
| **C-c C-n**    | **c-forward-conditional**    | Move to the next preprocessor conditional.                                  |

## Customizing Code Indentation Style

**M-x c-set-style**


| **Style**  | **Description**                                                                                                                                                                                                                                          |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| bsd        | Style used in code for BSD-derived versions of Unix.                                                                                                                                                                                                     |
| cc-mode    | The default coding style, from which all others are derived .                                                                                                                                                                                            |
| ellemtel   | Style used in C++ documentation from Ellemtel Telecommunication Systems Laboratories in Sweden .                                                                                                                                                         |
| gnu        | Style used in C code for Emacs itself and other GNU-related programs .                                                                                                                                                                                   |
| java       | Style used in Java code (the default for Java mode).                                                                                                                                                                                                     |
| k&r        | Style of the classic text on C, Kernighan and Ritchie's*The C Programming Language* .                                                                                                                                                                    |
| linux      | Style used in C code that is part of the Linux kernel.                                                                                                                                                                                                   |
| python     | Style used in python extensions.                                                                                                                                                                                                                         |
| stroustrup | C++ coding style of the standard reference work, Bjarne Stroustrup's*The C++ Programming Language* .                                                                                                                                                     |
| user       | Customizations you make to*.emacs* or via Custom (see [Chapter 10](https://learning.oreilly.com/library/view/learning-gnu-emacs/0596006489/ch10.html "Chapter 10. Customizing Emacs")). All other styles inherit these customizations if you set them. |
| whitesmith | Style used in Whitesmith Ltd.'s documentation for their C and C++ compilers .                                                                                                                                                                            |

Once you decide on a coding style, you can set it up permanently by putting a line in your *.emacs* file that looks like this:

```.emacs
(add-hook 'c-mode-hook
       '(lambda ( )
         (c-set-style "stylename")))
```

## Additional C and C++ Mode Features

Auto-newline is off by default. To turn it on, type **C-c C-a** for **c-toggle-auto-state**. (Repeat the same command to turn it off again.) You will see the **(C)** in the mode line change to **(C/a)** as an indication.

The other optional electric feature, **hungry-delete-key**, is also off by default. To toggle it on, type **C-c C-d** (for **c-toggle-hungry-state**). You will see the **(C)** on the mode line change to **(C/h)**, or if you have **auto-newline** turned on, from **(C/a)** to **(C/ah)**.

You can toggle the states of both **auto-newline** and **hungry-delete-key** with the command **C-c C-t** (for **c-toggle-auto-hungry-state**).

If you want either of these features on by default when you invoke Emacs, you can put lines like the following in your *.emacs* file:

```.emacs
(add-hook 'c-mode-hook
      '(lambda ( )
         (c-toggle-auto-state)))
```

If you want to combine this customization with another C mode customization, such as the indentation style in the previous example, you need to combine the lines of Emacs Lisp code as follows:

```.emacs
(add-hook 'c-mode-hook
      '(lambda ( )
         (c-set-style "stylename")
          (c-toggle-auto-state)))
```

You can customize **M-j** (for **indent-new-comment-line**) so that Emacs continues the same comment on the next line instead of creating a new pair of delimiters. The variable **comment-multi-line** controls this feature: if it is set to **nil** (the default), Emacs generates a new comment on the next line, as in the example from earlier in the chapter:

This outcome is the result of typing **M-j** after **multiplicand**, and it shows that the cursor is positioned so that you can type the text of the second comment line. However, if you set **comment-multi-line** to **t** (or any value other than **nil**), you get this outcome instead:

The final feature we'll cover is **C-c C-e**, (for **c-macro-expand**). Like the conditional compilation motion commands (e.g., **C-c C-u** for **c-up-conditional**), **c-macro-expand** helps you answer the often difficult question, "What code actually gets compiled?" when your source code contains a morass of preprocessor directives.

To use **c-macro-expand**, you must first define a region. Then, when you type **C-c C-e**, it takes the code within the region, passes it through the actual C preprocessor, and places the output in a window called `*Macroexpansion*`.

If you want to use **c-macro-expand** with a different C preprocessor command, instead of the default **/lib/cpp -C** (the **-C** option means "preserve comments in the output"), you can set the variable **c-macro-preprocessor**. For example, if you want to use an experimental preprocessor whose filename is */usr/local/lib/cpp*, put the following line in your *.emacs* file:

```.emacs
(setq c-macro-preprocessor "/usr/local/lib/cpp -C")
```

## C++ Mode Differences

If you want C++ mode's indentation style set to **Stroustrup** with automatic newlines instead of the default style, put the following in your *.emacs* file:

```.emacs
(add-hook 'c++-mode-hook
      '(lambda ( )
         (c-set-style "Stroustrup")
         (c-toggle-auto-state)))
```

C++ mode provides an additional command: **C-c **: (for **c-scope-operator**). This command inserts the C++ double colon (::) scope operator.

Finally, both C and C++ mode contain the commands **c-forward-into-nomenclature** and **c-backward-into-nomenclature**, which aren't bound to any keystrokes by default. These are like **forward-word** and **backward-word**, respectively, but they treat capital letters in the middle of words as if they were starting new words. For example, they treat *ThisVariableName* as if it were three separate words while the standard **forward-word** and **backward-word** commands treat it as one word. *ThisTypeOfVariableName* is a style used by C++ programmers, as opposed to *this\_type\_of\_variable\_name*, which is somehow more endemic to old-school C code.
