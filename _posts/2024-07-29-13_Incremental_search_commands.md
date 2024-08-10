---  
title: 13 Incremental search commands  
date: 2024-07-29 07:59:46 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
| Keystrokes                                                                          | Command name                | Action                                                                                                              |
| ----------------------------------------------------------------------------------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **C-s** *Edit* **→** *Search* **→** *Incremental Search* **→** *Forward String*  | **isearch-forward**         | Start incremental search forward; follow by search string. Also, find next occurrence (forward) of search string.   |
| **C-r** *Edit* **→** *Search* **→** *Incremental Search* **→** *Backward String* | **isearch-backward**        | Start incremental search backward; follow by search string. Also, find next occurrence (backward) of search string. |
| **Enter**                                                                           | **isearch-exit**            | In an incremental search , exit the search.                                                                         |
| **C-g**                                                                             | **keyboard-quit**           | In an incremental search , cancel the search.                                                                       |
| **Del**                                                                             | **isearch-delete-char**     | In an incremental search, delete character from search string.                                                      |
| **C-s C-w**                                                                         | **isearch-yank-word**       | Start an incremental search with the word the cursor is on as the search string.                                    |
| **C-s C-y**                                                                         | **isearch-yank-line**       | Start an incremental search with the text from the cursor position to the end of the line as the search string.     |
| **C-s M-y**                                                                         | **isearch-yank-kill**       | Start an incremental search with text from the kill ring as the search string.                                      |
| **C-s C-s**                                                                         | **isearch-repeat-forward**  | Repeat previous search.                                                                                             |
| C-r C-r                                                                             | **isearch-repeat-backward** | Repeat previous search backward.                                                                                    |
