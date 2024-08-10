---  
title: 22 Working with Multiple Buffers  
date: 2024-07-29 07:59:35 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
1. **创建缓冲区包含文件：**

   - 使用 `C-x C-f` 查找文件。
   - Emacs 会自动创建第二个缓冲区并切换过去。
2. **已有文件缓冲区：**

   - 如果文件已在缓冲区中，`C-x C-f` 只会移动到已有缓冲区。
3. **防止多版本文件：**

   - 避免每次从磁盘读取文件，防止多个稍有不同的版本。
4. **新文件：**

   - 如果指定的文件名不存在，Emacs 会创建一个新文件并移动到空白缓冲区。


这里是这段文字的重点内容总结：

1. **在缓冲区之间移动：**

   - 使用 `C-x b` 移动。
2. **默认缓冲区名：**

   - Emacs 显示一个默认的缓冲区名称。
   - 如果是你想要的缓冲区，按 Enter。
3. **选择正确缓冲区：**

   - 输入正确缓冲区名称的前几个字符，然后按 Tab 键，Emacs 会补全名称。
   - 按 Enter 移动到该缓冲区。


| **If you type C-x b followed by**: | **Emacs**:                                                                                      |
| ---------------------------------- | ----------------------------------------------------------------------------------------------- |
| A new buffer name                  | Creates a new buffer that isn't connected with a file and moves there.                          |
| The name of an existing buffer     | Moves you to the buffer (it doesn't matter whether the buffer is connected with a file or not). |

Alternatively, the Buffer Menu popup lists buffers by major mode, and you can choose one. Hold down **Ctrl** and click the left mouse button to see a pop-up menu of your current buffers. (The Buffers menu at the top of the screen also shows all current buffers.)

To cycle through all the buffers you have, type **C-x** **→** to go to the next buffer (in the buffer list) or **C-x** to go to the previous buffer. (Don't hold down Ctrl while you press the arrow key or Emacs beeps unhappily.)

To delete a buffer, type **C-x k** (for **kill-buffer**). Emacs shows the name of the buffer currently displayed; press **Enter** to delete it or type another buffer name if the one being displayed is not the one you want to delete, then press **Enter**.

Type **M-x kill-some-buffers** to weed out unneeded buffers this way. Emacs displays the name of each buffer and whether or not it was modified, then asks whether you want to kill it.
