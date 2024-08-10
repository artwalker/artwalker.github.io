---  
title: 20 Using Buffers Windows and Frames  
date: 2024-07-29 07:59:37 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
`*scratch*` is just what it sounds like: a temporary scratchpad where you can type. It won't be saved unless you explicitly write it to a file using **C-x C-w**.

+-------------------+    +-------------------+
| Frame 1           |    | Frame 2           |
| +-------------+   |    | +-------------+   |
| | Window 1    |   |    | | Window A    |   |
| +-------------+   |    | +-------------+   |
+-------------------+    +-------------------+

+------------------------------+
| Frame                        |
| +------------+-------------+ |
| | Window 1   | Window 2    | |
| |            |             | |
| +------------+-------------+ |
| | Window 3                 | |
| +--------------------------+ |
+------------------------------+
