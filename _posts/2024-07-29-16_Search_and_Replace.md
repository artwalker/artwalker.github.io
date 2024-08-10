---  
title: 16 Search and Replace  
date: 2024-07-29 07:59:43 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
To use query-replace, go to the beginning of the buffer using **M-<** and then type **M-%**.

Responses during query-replace:


| **Keystrokes**     | **Action**                                                                                |
| ------------------ | ----------------------------------------------------------------------------------------- |
| **Space** or **y** | Replace*`searchstring`* with *`newstring`* and go to the next instance of the string.     |
| **Del** or **n**   | Don't replace; move to next instance.                                                     |
| .                  | Replace the current instance and quit.                                                    |
| ,                  | Replace and let me see the result before moving on. (Press**Space** or **y** to move on.) |
| **!**              | Replace all the rest and don't ask.                                                       |
| **^**              | Back up to the previous instance.                                                         |
| **Enter** or **q** | Exit query-replace.                                                                       |
| **E**              | Modify the replacement string.                                                            |
| **C-r**            | Enter a recursive edit (discussed in detail later).                                       |
| **C-w**            | Delete this instance and enter a recursive edit (so you can make a custom replacement).   |
| **C-M-c**          | Exit recursive edit and resume query-replace.                                             |
| **C-]**            | Exit recursive edit and exit query-replace.                                               |

This list seems like a lot of keystrokes to remember, but you can get away with knowing two or three. Most of the time you'll respond to the prompt by pressing **Space**, telling Emacs to perform the replacement and go on to the next instance, or **n** to skip this replacement and go on to the next instance. If you're not too sure what will happen, enter a comma (,); Emacs makes the replacement but doesn't go on until you press **Space**. After performing the first few replaces, you may realize that there's no need to inspect every change individually. Typing an exclamation mark (**!**) tells Emacs to go ahead and finish the job without bothering you anymore. If you remember these keystrokes, you're all set.


## Repeating Query-Replaces (and Other Complex Commands)

Simply go the beginning of the file and press **C-x Esc Esc**. The last complex command you typed appears. If it's not the one you want, type **M-p** to see the previous command (do this as many times as necessary; **M-n** goes to the next command).

Type: **M-<** followed by **C-x Esc Esc**

## Recursive Editing

To start a recursive edit while in query-replace, press **C-r**.

When you want to resume the query-replace, press **C-M-c**. This command tells Emacs to leave the recursive edit and reactivate the query-replace. Emacs moves back to the point where you were when you started the recursive edit. You can then continue making replacements just as if nothing had happened.

If you decide to exit the recursive edit and cancel the query-replace in one fell swoop, you can type **C-]** (for **abort-recursive-edit**) or **M-x top-level Enter**.

In fact, you can start a recursive edit at any time, not just when you're in a query-replace. The command **M-x recursive-edit Enter** puts you into a recursive edit; **C-M-c** takes you out of the recursive edit and brings you back to what you were doing before. You can even have recursive edits within recursive edits, although the possibility for confusion increases with each new level.

## Are Emacs Searches Case-Sensitive?

type **M-x** **set-variable** **Enter case-replace Enter nil Enter**

You can set the value for the Case-Insensitive Search option permanently by selecting Save Options from the Options menu or by adding this line to your *.emacs* file:

```
(setq-default case-fold-search nil)  ; require exact matches
```

To set **case-replace** permanently, add the following line to your *.emacs* file. You'll need to restart Emacs to have the change take effect.

```
(setq-default case-replace nil)      ; never change case when replacing
```
