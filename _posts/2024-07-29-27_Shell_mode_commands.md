---  
title: 27 Shell mode commands  
date: 2024-07-29 07:59:30 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
If you want to run another particular shell (for example, the zed shell) when you're in Emacs, you can add the following command to your *.emacs* file:

```zsh
(setq shell-file-name "/bin/zsh")
```

When Emacs starts an interactive shell, it runs an additional initialization file after your shell's normal startup files. The name of this file is *.emacs\_shell-name*, where *shell-name* is the name of the shell you want to use in Emacs. It must be located in your home directory. For example, if you use the C shell, you can add Emacs-only startup commands by placing them in the file *.emacs\_csh*. Let's say that when you're in Emacs, you want to change the prompt to **emacs:%** and you want an environment variable called **WITHIN\_EDITOR** to be set to **T**. Here's the contents of your *.emacs\_csh* file:

```zsh
set prompt="emacs:% "
setenv WITHIN_EDITOR T
```

Within a shell buffer, Emacs also sets the environment variable **EMACS** to **t**, and sets your terminal type (the **TERM** variable) to **emacs**.


| **Keystrokes**                                            | **Command name**                | **Action**                                                                   |
| --------------------------------------------------------- | ------------------------------- | ---------------------------------------------------------------------------- |
| (*none*)                                                  | **shell**                       | Enter shell mode.                                                            |
| **C-c C-c** *Signals* **→** *BREAK*                      | **comint-interrupt-subjob**     | Interrupt current job; equivalent to**C-c**.                                 |
| **C-d**                                                   | **comint-delchar-or-maybe-eof** | Send EOF character if at end of buffer; delete a character elsewhere.        |
| **C-c C-d** *Signals* **→** *EOF*                        | **comint-send-eof**             | Send EOF character.                                                          |
| **C-c C-u**                                               | **comint-kill-input**           | Erase current line; equivalent to**C-u** in Unix shells.                     |
| **C-c C-z** *Signals* **→** *STOP*                       | **comint-stop-subjob**          | Suspend or stop a job;**C-z** in Unix shells.                                |
| **M-p** *In/Out* **→** *Previous Input*                  | **comint-previous-input**       | Retrieve previous commands (can be repeated to find earlier commands).       |
| **M-n** *In/Out* **→** *Next Input*                      | **comint-next-input**           | Retrieve subsequent commands (can be repeated to find more recent commands). |
| **Enter**                                                 | **comint-send-input**           | Send input on current line.                                                  |
| **Tab**                                                   | **comint-dynamic-complete**     | Complete current command, filename, or variable name.                        |
| **C-c C-o** *In/Out* **→** *Delete Current Output Group* | **comint-kill-output**          | Delete output from last command.                                             |
| **C-c C-r**                                               | **comint-show-output**          | Move first line of output to top of window.                                  |
| **C-c C-e** *In/Out* **→** *Show Maximum Output*         | **comint-show-maximum-output**  | Move last line of output to bottom of window.                                |
| **C-c C-p** *In/Out* **→** *Backward Output Group*       | **comint-previous-prompt**      | Move to previous command.                                                    |
| **C-c C-n** *In/Out* **→** *Forward Output Group*        | **comint-next-prompt**          | Move to next command.                                                        |
