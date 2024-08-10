---  
title: 00 how to view md files in emacs  
date: 2024-07-29 08:00:00 +0800  
categories: [emacs]  
tags: [emacs]  
--- 
## Methods: Impatient-mode
[Reference](https://stackoverflow.com/questions/36183071/how-can-i-preview-markdown-in-emacs-in-real-time)

* Install impatient-mode with `M-x package-install RET impatient-mode
  RET, given you have configured package.el to use
  the [melpa](https://wikemacs.org/wiki/Melpa) repository.
* Start an emacs' web server with `M-x httpd-start.`
* Start impatient mode in the buffers you're interested to live
  preview: `M-x impatient-mode.`
* Open your browser to `localhost:8080/imp`. You'll see the list of
  buffers with the mode enabled. Click on one: you see live rendering
  of the buffer.
* Define this elisp function somewhere, like in your .emacs file:  
* Tell impatient mode to use it: `M-x imp-set-user-filter RET
  markdown-html RET`.
* Go back to your browser, it works!

```emacs-lisp
;; Define markdown-html function
(defun markdown-html (buffer)
  (princ (with-current-buffer buffer
           (format "<!DOCTYPE html><html><title>Impatient Markdown</title><xmp theme=\"united\" style=\"display:none;\"> %s  </xmp><script src=\"http://ndossougbe.github.io/strapdown/dist/strapdown.js\"></script></html>"
                   (buffer-substring-no-properties (point-min) (point-max))))
         (current-buffer)))
		 
