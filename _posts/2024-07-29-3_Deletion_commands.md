---  
title: 3 Deletion commands  
date: 2024-07-29 07:59:56 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
| Keystrokes                  | Command name                | Action                                     |
| --------------------------- | --------------------------- | ------------------------------------------ |
| **C-d**                     | **delete-char**             | Delete character under cursor.             |
| **Del**                     | **delete-backward-char**    | Delete previous character.                 |
| **M-d**                     | **kill-word**               | Delete next word.                          |
| **M-Del**                   | **backward-kill-word**      | Delete previous word.                      |
| **C-k**                     | **kill-line**               | Delete from cursor to end of line.         |
| **M-k**                     | **kill-sentence**           | Delete next sentence.                      |
| **C-x Del**                 | **backward-kill-sentence**  | Delete previous sentence.                  |
| **C-y**                     | **yank**                    | Restore what you've deleted.               |
| **C-w** *Edit* **→** *Cut* | **kill-region**             | Delete a marked region (see next section). |
| (*none*)                    | **kill-paragraph**          | Delete next paragraph.                     |
| (*none*)                    | **backward-kill-paragraph** | Delete previous paragraph.                 |
