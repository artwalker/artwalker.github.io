---  
title: 18 Spell checking commands  
date: 2024-07-29 07:59:41 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
| **Keystrokes**                                                                       | **Command name**                | **Action**                                                                                            |
| ------------------------------------------------------------------------------------ | ------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **M-\$** *Tools* **→** *Spell Checking* **→** *Spell-Check Word*                   | **ispell-word**                 | Check the word the cursor is on or the word following the cursor.                                     |
| (*none*)*Tools* **→** *Spell Checking* **→** *Spell-Check Region*                  | **ispell-region**               | Check spelling of the region.                                                                         |
| (*none*)*Tools* **→** *Spell Checking* **→** *Spell-Check Buffer*                  | **ispell-buffer**               | Check spelling of the buffer.                                                                         |
| (*none*)*Tools* **→** *Spell Checking* **→** *Spell-Check Message*                 | **ispell-message**              | Check spelling of the body of a mail message.                                                         |
| (*none*)*Tools* **→** *Spell Checking* **→** *Spell-Check Comments*                | **ispell-comments-and-strings** | Check spelling of comments and strings in a program.                                                  |
| **C-u M-\$** *Tools* **→** *Spell Checking* **→** *Continue Spell-Checking*        | **ispell-continue**             | Resume Ispell; it works only if stopped Ispell with**C-g**.                                           |
| (*none*)                                                                             | **ispell-kill-ispell**          | Kill the Ispell process, which continues to run in the background after it is invoked.                |
| **M-Tab** *Tools* **→** *Spell Checking* **→** *Complete Word*                     | **ispell-complete-word**        | In text mode, list possible completions for the current word.                                         |
| (*none*)*Tools* **→** *Spell Checking* **→** *Automatic Spell-Checking (Flyspell)* | **flyspell-mode**               | Enter the Flyspell minor mode, in which incorrectly spelled words are highlighted.                    |
| (*none*)                                                                             | **flyspell-buffer**             | Spell-check the current buffer, underlining all misspelled words. Use middle mouse button to correct. |
