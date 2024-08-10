---  
title: 9 Methods for undoing changes  
date: 2024-07-29 07:59:50 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
1. Enter the **INSERT** key
2. **M-x overwrite-mode Enter**

| **If you**:                                                                                                  | **Use this command**:                                            |
| ------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------- |
| Don't like the recent changes you've made and want to undo them one by one                                   | **C-\_** *or* **C-x u** (**undo**)                               |
| Want to undo all changes made since you last saved the file                                                  | **M-x revert-buffer Enter**                                      |
| Want to go back to an earlier version of the file (the file as it was when you started this editing session) | **C-x C-f** *filename* **\~ Enter C-x C-w** *filename* **Enter** |
