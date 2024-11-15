---  
title: 36 Comparing with Ediff  
date: 2024-07-29 07:59:22 +0800  
categories: [emacs]  
tags: [emacs]  
---
## Comparing with Ediff

Ediff commands


| **Keystrokes**     | **Command name**                      | **Action**                                                                                                                                                                              |
| ------------------ | ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Space** or **n** | **ediff-next-difference**             | Move to the next difference between the files.                                                                                                                                          |
| **Del** or **p**   | **ediff-previous-difference**         | Move to the preceding difference between the files.                                                                                                                                     |
| **j**              | **ediff-jump-to-difference**          | Go to the difference specified as a numeric prefix argument.                                                                                                                            |
| **v** or **C-v**   | **ediff-scroll-vertically**           | Move forward one page in both buffers.                                                                                                                                                  |
| **V** or **M-v**   | **ediff-scroll-vertically**           | Move backward one page in both buffers.                                                                                                                                                 |
| **<**              | **ediff-scroll-horizontally**         | Scroll each buffer to the left.                                                                                                                                                         |
| **>**              | **ediff-scroll-horizontally**         | Scroll each buffer to the right.                                                                                                                                                        |
| **                 | ** (vertical bar)                     | **ediff-toggle-split**                                                                                                                                                                  |
| **m**              | **ediff-toggle-wide-display**         | Toggle between normal frame size and making it as wide as possible.                                                                                                                     |
| **a**              | **ediff-copy-A-to-B**                 | Copy the version of the current difference found in buffer A to buffer B.                                                                                                               |
| **b**              | **ediff-copy-B-to-A**                 | Copy the version of the current difference found in buffer B to buffer A.                                                                                                               |
| **r a** or **r b** | **ediff-restore-diff**                | Restore the current difference in buffer A (or B) to the way it was before copying from the other buffer.                                                                               |
| **A** or **B**     | **ediff-toggle-read-only**            | Switch the specified buffer into (or out of) read-only mode.                                                                                                                            |
| **g a** or **g b** | **ediff-jump-to-difference-at-point** | Recenter the comparison buffers on the difference nearest to your current location (point) in the specified buffer.                                                                     |
| **C-l**            | **ediff-recenter**                    | Restore the comparison display so that the highlighted regions of all buffers being compared are visible; useful if you've been doing something else and want to get back to comparing. |
| **!**              | **ediff-update-diffs**                | Recalculate and redisplay the highlighted regions; useful if you've manually made extensive changes to a buffer.                                                                        |
| **w a** or **w b** | **ediff-save-buffer**                 | Save the specified buffer to disk.                                                                                                                                                      |
| **E**              | **ediff-documentation**               | Open the manual for Ediff.                                                                                                                                                              |
| **z**              | **ediff-suspend**                     | Close the Ediff control window, but leave the session active so you can resume it later.                                                                                                |
| **q**              | **ediff-quit**                        | Close the Ediff window and end this comparison session.                                                                                                                                 |
