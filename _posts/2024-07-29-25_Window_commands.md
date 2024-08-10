---  
title: 25 Window commands  
date: 2024-07-29 07:59:32 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
| **Keystrokes**                                                                | **Command name**                        | **Action**                                                                                          |
| ----------------------------------------------------------------------------- | --------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **C-x 2** *File* **→** *Split Window*                                        | **split-window-vertically**             | Divide current window into two windows, one above the other.                                        |
| **C-x 3**                                                                     | **split-window-horizontally**           | Divide current window into two side-by-side windows.                                                |
| **C-x >**                                                                     | **scroll-right**                        | Scroll the window right.                                                                            |
| **C-x <**                                                                     | **scroll-left**                         | Scroll the window left.                                                                             |
| **C-x o**                                                                     | **other-window**                        | Move to the other window; if there are several, move to the next window (see "Navigating Windows"). |
| **C-x 0**                                                                     | **delete-window**                       | Delete the current window.                                                                          |
| **C-x 1** *File* **→** *Unsplit Windows*                                     | **delete-other-windows**                | Delete all windows but this one.                                                                    |
| (*none*)                                                                      | **delete-windows-on**                   | Delete all windows on a given buffer.                                                               |
| **C-x ^**                                                                     | **enlarge-window**                      | Make window taller.                                                                                 |
| (*none*)                                                                      | **shrink-window**                       | Make window shorter.                                                                                |
| **C-x }**                                                                     | **enlarge-window-horizontally**         | Make window wider.                                                                                  |
| **C-x {**                                                                     | **shrink-window-horizontally**          | Make window narrower.                                                                               |
| **C-x -**                                                                     | **shrink-window-if-larger-than-buffer** | Make window smaller if buffer is smaller than window.                                               |
| **C-x +**                                                                     | **balance-windows**                     | Make windows the same size.                                                                         |
| **C-M-v**                                                                     | **scroll-other-window**                 | Scroll other window.                                                                                |
| **C-x 4 f**                                                                   | **find-file-other-window**              | Find a file in the other window.                                                                    |
| **C-x 4 b**                                                                   | **switch-to-buffer-other-window**       | Select a buffer in the other window.                                                                |
| (*none*)*Tools* **→** *Compare (Ediff)* **→** *This Window and Next Window* | **compare-windows**                     | Compare this window with the next window and show the first difference.                             |
