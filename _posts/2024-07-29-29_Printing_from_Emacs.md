---  
title: 29 Printing from Emacs  
date: 2024-07-29 07:59:28 +0800  
categories: [emacs]  
tags: [emacs]  
---
If you want to use the printer named lpt1 whenever you print from Emacs, you would want to set **lpr-switches** to -`Plpt1`. To do so, add the following line to your *.emacs* file:


```
(setq lpr-switches '("-Plpt1"))
```

Printing commands:


| **Keystrokes**                                                             | **Action**                                                                                                      |
| -------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **M-x print-buffer** *File* **→** *Print Buffer*                          | Print the buffer (similar to Unix **pr                                                                          |
| **M-x print-region** *File* **→** *Print Region*                          | Print the region (similar to Unix **pr                                                                          |
| **M-x lpr-buffer**                                                         | Print buffer with no page numbers (similar to Unix**lpr**).                                                     |
| **M-x lpr-region**                                                         | Print region with no page numbers (similar to Unix**lpr**).                                                     |
| **P** *Operate* **→** *Print*                                             | From Dired, put the default print command in the minibuffer; you can change it or press**Enter** to execute it. |
| **M-x ps-print-buffer-with-faces** *File* **→** *Postscript Print Buffer* | Print the buffer with text attributes.                                                                          |
| **M-x ps-print-region-with-faces** *File* **→** *Postscript Print Region* | Print the region with text attributes.                                                                          |
