---  
title: 23 Working with Windows  
date: 2024-07-29 07:59:34 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
## Creating Horizontal Windows

**C-x 2** (for **split-window-vertically**)

If you wanted to edit *dickens* and *joyce*, you would type **emacs dickens joyce** and Emacs would display these files in two horizontal windows. If you try this with more than two files, Emacs displays two horizontal windows, with a file in one and a list of buffers in the other.

A number of the "other window" commands are just the ordinary command with a *4* inserted in it. For example, to find a file in another window, type **C-x 4 f**. (If only one window is currently open, Emacs opens another one.) To select a different buffer in another window, type **C-x 4 b**. Many users find these commands preferable to the normal **C-x C-f** and **C-x b** commands because they save you a step: you need not move to the window, give a command, and move back.

Once you've got multiple windows open, it's helpful to be able to scroll them without moving there. To scroll the other window, type **C-M-v**.

## Moving Between Windows

**C-x o** (**o** stands for *other* in this command)

## Getting Rid of Windows

Deleting a window only means that it isn't displayed anymore; it doesn't delete any of the information or any of your unsaved changes. The underlying buffer is still there, and you can switch to it using **C-x b**. To delete the window you're in, type **C-x 0** (zero). If you want to delete all windows but the one you're working on, type **C-x 1** (one), meaning "make this my one and only window." As you'd expect, the remaining window "grows" to fill up the rest of the space. You can also delete all windows on a certain buffer by typing: **M-x delete-windows-on Enter** *`buffername`* **Enter**.
