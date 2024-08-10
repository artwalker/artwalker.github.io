---  
title: 24 Buffer manipulation commands  
date: 2024-07-29 07:59:33 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
| **Keystrokes**                                   | **Command name**      | **Action**                                         |
| ------------------------------------------------ | --------------------- | -------------------------------------------------- |
| **C-x b** *Buffers* **→** *Select Named Buffer* | **switch-to-buffer**  | Move to the buffer specified.                      |
| **C-x** **→** *Buffers* **→** *Next Buffer*    | **next-buffer**       | Move to the next buffer in the buffer list.        |
| **C-x** *Buffers* **→** *Previous Buffer*       | **previous-buffer**   | Move to the previous buffer in the buffer list.    |
| **C-x C-b** *Buffers* **→** *List All Buffers*  | **list-buffers**      | Display the buffer list.                           |
| **C-x k**                                        | **kill-buffer**       | Delete the buffer specified.                       |
| *(none)*                                         | **kill-some-buffers** | Ask about deleting each buffer.                    |
| *(none)*                                         | **rename-buffer**     | Change the buffer's name to the name specified.    |
| **C-x s**                                        | **save-some-buffers** | Ask whether you want to save each modified buffer. |

Buffer list commands


| **Keystrokes**                | **Action**                                                                     | **Occurs**          |
| ----------------------------- | ------------------------------------------------------------------------------ | ------------------- |
| **C-n**, **Space**, **n**, or | Move to the next buffer in the list (i.e., down one line).                     | Immediately         |
| **C-p**, **p**, or            | Move to the previous buffer in the list (i.e., up one line).                   | Immediately         |
| **d**                         | Mark buffer for deletion.                                                      | When you press**x** |
| **k**                         | Mark buffer for deletion.                                                      | When you press**x** |
| **s**                         | Save buffer.                                                                   | When you press**x** |
| **u**                         | Unmark buffer.                                                                 | Immediately         |
| **x**                         | Execute other one-letter commands on all marked buffers.                       | Immediately         |
| **Del**                       | Unmark the previous buffer in the list; if there is no mark, move up one line. | Immediately         |
| **\~**                        | Mark buffer as unmodified.                                                     | Immediately         |
| **%**                         | Toggle read-only status of buffer.                                             | Immediately         |
| **1**                         | Display buffer in a full screen.                                               | Immediately         |
| **2**                         | Display this buffer and the next one in horizontal windows.                    | Immediately         |
| **f**                         | Replace buffer list with this buffer.                                          | Immediately         |
| **o**                         | Replace other window with this buffer.                                         | Immediately         |
| **m**                         | Mark buffers to be displayed in windows.                                       | When you press**v** |
| **v**                         | Display buffers marked with**m**; Emacs makes as many windows as needed.       | Immediately         |
| **q**                         | Quit buffer list.                                                              | Immediately         |
