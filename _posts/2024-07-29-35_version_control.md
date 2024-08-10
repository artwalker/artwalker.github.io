---  
title: 35 version control  
date: 2024-07-29 07:59:23 +0800  
categories: [emacs]  
tags: [emacs]  
---
VC commands

| **Keystrokes** | **Command name**            | **Action**                                             |
| -------------- | --------------------------- | ------------------------------------------------------ |
| **C-x v v**    | **vc-next-action**          | Go to the next logical version control state.          |
| **C-x v d**    | **vc-directory**            | Show all registered files beneath a directory.         |
| **C-x v =**    | **vc-diff**                 | Generate a version difference report.                  |
| **C-x v u**    | **vc-revert-buffer**        | Throw away changes since the last checked-in revision. |
| **C-x v \~**   | **vc-version-other-window** | Retrieve a given revision in another window.           |
| **C-x v l**    | **vc-print-log**            | Display a file's change comments and history.          |
| **C-x v i**    | **vc-register**             | Register a file for version control.                   |
| **C-x v h**    | **vc-insert-headers**       | Insert version control headers in a file.              |
| **C-x v r**    | **vc-retrieve-snapshot**    | Check out a named project snapshot.                    |
| **C-x v s**    | **vc-create-snapshot**      | Create a named project snapshot.                       |
| **C-x v c**    | **vc-cancel-version**       | Throw away a saved revision.                           |
| **C-x v a**    | **vc-update-change-log**    | Update a GNU-style ChangeLog file.                     |

Two minor commands, **vc-rename-file** and **vc-clear-context**, are not bound to keys.
