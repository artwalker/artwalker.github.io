---  
title: 26 Bookmark commands  
date: 2024-07-29 07:59:31 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
| **Keystrokes**                                                    | **Command name**             | **Action**                                                  |
| ----------------------------------------------------------------- | ---------------------------- | ----------------------------------------------------------- |
| **C-x r m** *Edit* **→** *Bookmarks* **→** *Set Bookmark*       | **bookmark-set**             | Set a bookmark at the current cursor position.              |
| **C-x r b** *Edit* **→** *Bookmarks* **→** *Jump to Bookmark*   | **bookmark-jump**            | Jump to a bookmark.                                         |
| (*none*)*Edit* **→** *Bookmarks* **→** *Rename Bookmark*        | **bookmark-rename**          | Rename a bookmark.                                          |
| (*none*)*Edit* **→** *Bookmarks* **→** *Delete Bookmark*        | **bookmark-delete**          | Delete a bookmark.                                          |
| (*none*)*Edit* **→** *Bookmarks* **→** *Save Bookmarks*         | **bookmark-save**            | Save all bookmarks in default file.                         |
| **C-x r l** *Edit* **→** *Bookmarks* **→** *Edit Bookmark List* | **bookmark-menu-list**       | Move to`*Bookmark List*` buffer.                            |
| (*none*)*Edit* **→** *Bookmarks* **→** *Insert Contents*        | **bookmark-insert**          | Insert full text of file associated with a given bookmark.  |
| (*none*)*Edit* **→** *Bookmarks* **→** *Save Bookmarks As*      | **bookmark-write**           | Save all bookmarks in a specified file.                     |
| (*none*)*Edit* **→** *Bookmarks* **→** *Load a Bookmark File*   | **bookmark-load**            | Load bookmarks from specified file.                         |
| (*none*)*Edit* **→** *Bookmarks* **→** *Insert Location*        | **bookmark-insert-location** | Insert the path to a given bookmark at the cursor position. |

Commands for editing the bookmark list (**C-x r l**)


| **Command**                | **Action**                                                                                                                                     |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Enter**, **f**, or **j** | Go to the bookmark on the current line.                                                                                                        |
| **C-o** or **o**           | Open the bookmark on the current line in another window;**o** moves the cursor to that window; **C-o** keeps the cursor in the current window. |
| **d**, **C-d**, or **k**   | Flag bookmark for deletion.                                                                                                                    |
| **r**                      | Rename bookmark.                                                                                                                               |
| **s**                      | Save all bookmarks listed.                                                                                                                     |
| **m**                      | Mark bookmarks to be displayed in multiple windows.                                                                                            |
| **v**                      | Display marked bookmarks or the one the cursor is on if none are marked.                                                                       |
| **t**                      | Toggle display of paths to files associated with bookmarks.                                                                                    |
| **w**                      | In the minibuffer, display location of file associated with bookmark.                                                                          |
| **x**                      | Delete bookmarks flagged for deletion.                                                                                                         |
| **u**                      | Remove mark from bookmark.                                                                                                                     |
| **Del**                    | Remove mark from bookmark on previous line or move to the previous line (if there is no mark).                                                 |
| **q**                      | Exit bookmark list.                                                                                                                            |
| **Space** or **n**         | Move down a line.                                                                                                                              |
| **p**                      | Move up a line.                                                                                                                                |
| **l**                      | Load a bookmark file (other than the default).                                                                                                 |
| **A**                      | Display all annotations.                                                                                                                       |
| **a**                      | Display annotation for current bookmark.                                                                                                       |
| **e**                      | Edit (or create) annotation for the current bookmark.                                                                                          |
