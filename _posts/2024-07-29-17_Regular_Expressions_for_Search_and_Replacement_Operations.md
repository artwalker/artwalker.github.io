---  
title: 17 Regular Expressions for Search and Replacement       Operation  
date: 2024-07-29 07:59:42 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
Characters for creating regular expressions:


| **Character(s)** | **Match**                                                                                                                                             |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **^**            | Matches the beginning of a line.                                                                                                                      |
| **\$**           | Matches the end of a line.                                                                                                                            |
| .                | Matches any single character (like ? in filenames).                                                                                                   |
| **.\***          | Matches any group of zero or more characters (. matches any character and\* matches zero or more of the previous character).                          |
| **\\<**          | Matches the beginning of a word.                                                                                                                      |
| **\\>**          | Matches the end of a word.                                                                                                                            |
| **[ ]**          | Matches any character specified within the brackets; for example, [a-z] matches any alphabetic character.                                             |
| **\\s, \\S**     | Matches any whitespace character: space, a newline, a tab, a carriage return, a formfeed, or a backspace;\\S matches any character except whitespace. |
| **\\d, \\D**     | Matches any single digit, 0-9;\\D matches any character but a digit.                                                                                  |
| **\\w, \\W**     | Matches any "word" character (upper- and lowercase letters, digits, and the underscore character);\\W matches any character but these.                |

*Mastering Regular Expressions* by Jeffrey Friedl (O'Reilly)

Regular expression search commandsegular expression search commands:


| **Keystrokes**                                                                        | **Command name**            | **Action**                                                                |
| ------------------------------------------------------------------------------------- | --------------------------- | ------------------------------------------------------------------------- |
| **C-M-s Enter** *Edit* **→** *Search* **→** *Regexp Forward*                        | **re-search-forward**       | Search for a regular expression forward.                                  |
| **C-M-r Enter** *Edit* **→** *Search* **→** *Regexp Backwards*                      | **re-search-backward**      | Search for a regular expression backward.                                 |
| **C-M-s** *Edit* **→** *Search* **→** *Incremental Search* **→** *Forward Regexp*  | **isearch-forward-regexp**  | Search incrementally forward for a regular expression.                    |
| **C-M-r** *Edit* **→** *Search* **→** *Incremental Search* **→** *Backward Regexp* | **isearch-backward-regexp** | Search incrementally backward for a regular expression.                   |
| **C-M-%** *Edit* **→** *Replace* **→** *Replace Regexp*                             | **query-replace-regexp**    | Query-replace a regular expression.                                       |
| (*none*)                                                                              | **replace-regexp**          | Globally replace a regular expression unconditionally (use with caution). |
