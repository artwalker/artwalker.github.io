---  
title: 19 Word abbreviation commands  
date: 2024-07-29 07:59:38 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
| **Keystrokes**                 | **Command name**              | **Action**                                                                                                                      |
| ------------------------------ | ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **M-/**                        | **dabbrev-expand**            | Complete this word based on the nearest word that starts with this string (press**M-/** again if that's not the word you want). |
| (*none*)                       | **abbrev-mode**               | Enter (or exit) word abbreviation mode.                                                                                         |
| **C-x a -** *or* **C-x a i g** | **inverse-add-global-abbrev** | After typing the global abbreviation, type the definition.                                                                      |
| **C-x a i l**                  | **inverse-add-mode-abbrev**   | After typing the local abbreviation, type the definition.                                                                       |
| (*none*)                       | **unexpand-abbrev**           | Undo the last word abbreviation.                                                                                                |
| (*none*)                       | **write-abbrev-file**         | Write the word abbreviation file.                                                                                               |
| (*none*)                       | **edit-abbrevs**              | Edit the word abbreviations.                                                                                                    |
| (*none*)                       | **list-abbrevs**              | View the word abbreviations.                                                                                                    |
| (*none*)                       | **kill-all-abbrevs**          | Kill abbreviations for this session.                                                                                            |

> Word abbreviation capitalization


| **Abbreviation** | **Definition** | **You type**: | **Expands to**: | **Because**:                                          |
| ---------------- | -------------- | ------------- | --------------- | ----------------------------------------------------- |
|                  |                |               |                 |                                                       |
| lc               | lamb chop      | **lc**        | lamb chop       | *lc* is lowercase, so *lamb chop* is lowercase.       |
| lc               | lamb chop      | **Lc**        | Lamb chop       | There's one capital in*Lc*, so *Lamb* is capitalized. |
| lc               | lamb chop      | **lC**        | Lamb chop       | There's one capital in*lC*, so *Lamb* is capitalized. |
| lc               | lamb chop      | **LC**        | Lamb Chop       | *LC* is all capitals, so both words are capitalized.  |
| lc               | Lamb Chop      | **lc**        | Lamb Chop       | Capitals in the definition are always unchanged.      |
| lc               | Lamb Chop      | **LC**        | Lamb Chop       | Capitals in the definition are always unchanged.      |
