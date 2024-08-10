---  
title: 32 Compilation mode commands  
date: 2024-07-29 07:59:26 +0800  
categories: [emacs]  
tags: [emacs]  
---
To use the Java build tool **ant** as your default compile command, just add this line:

```.emacs
(setq 'compile-command "ant -emacs")
```

Compilation mode commands


| **Keystrokes** | **Command name**               | **Action**                                                              |
| -------------- | ------------------------------ | ----------------------------------------------------------------------- |
| **C-x \`**     | **next-error**                 | Move to the next error message and visit the corresponding source code. |
| **M-n**        | **compilation-next-error**     | Move to the next error message.                                         |
| **M-p**        | **compilation-previous-error** | Move to the previous error message.                                     |
| **C-c C-c**    | **compilation-goto-error**     | Visit the source code for the current error message.                    |
| **Space**      | **scroll-down**                | Scroll down one screen.                                                 |
| **Del**        | **scroll-up**                  | Scroll up one screen.                                                   |
