---  
title: 4 Commands for working with regions  
date: 2024-07-29 07:59:55 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
| Keystrokes              | Command name                | Action                                             |
| ----------------------- | --------------------------- | -------------------------------------------------- |
| **C-@** or **C- Space** | **set-mark-command**        | Mark the beginning (or end) of a region.           |
| **C-x C-x**             | **exchange-point-and-mark** | Exchange location of cursor and mark.              |
| **C-w**                 | **kill-region**             | Delete the region.                                 |
| **C-y**                 | **yank**                    | Paste most recently killed or copied text.         |
| **M-w**                 | **kill-ring-save**          | Copy the region (so it can be pasted with**C-y**). |
| **M-h**                 | **mark-paragraph**          | Mark paragraph.                                    |
| **C-x C-p**             | **mark-page**               | Mark page.                                         |
| **C-x h**               | **mark-whole-buffer**       | Mark buffer.                                       |
| **M-y**                 | **yank-pop**                | After **C-y**, pastes earlier deletion.           |
