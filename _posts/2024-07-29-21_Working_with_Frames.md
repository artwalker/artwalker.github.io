---  
title: 21 Working with Frames  
date: 2024-07-29 07:59:36 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
For a more convenient solution, add these lines to your *.emacs* file:

```.emacs
(setq initial-frame-alist '((top . 10) (left . 30)
(width . 90) (height . 50)))
(setq default-frame-alist '((width . 80) (height . 45)))
```

Frame commands



| **Keystrokes**                           | **Command name**                    | **Action**                                        |
| ---------------------------------------- | ----------------------------------- | ------------------------------------------------- |
| **C-x 5 o** *Buffers* **→** *Frames*    | **other-frame**                     | Move to other frame.                              |
| **C-x 5 0** *File* **→** *Delete Frame* | **delete-frame**                    | Delete current frame.                             |
| **C-x 5 2** *File* **→** *New Frame*    | **make-frame**                      | Create a new frame on the current buffer.         |
| **C-x 5 f**                              | **find-file-other-frame**           | Find file in a new frame.                         |
| **C-x 5 r**                              | **find-file-read-only-other-frame** | Finds a file in a new frame, but it is read-only. |
| **C-x 5 b**                              | **switch-to-buffer-other-frame**    | Make frame and display other buffer in it.        |
