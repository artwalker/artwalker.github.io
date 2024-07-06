---
title: 0 Diffing Files  
date: 2024-07-06 21:35:00 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ cat rearrange1.py 
```
## Code output:
```bash
#!/usr/bin/env python3

import re

def rearrange_name(name):

    result = re.search(r"^([\w .]*), ([\w .]*)$", name)

    if result == None:

        return name

    return "{} {}".format(result[2], result[1])
```
## Command:
```bash
$ cat rearrange2.py 
```
## Code output:
```bash
#!/usr/bin/env python3

import re

def rearrange_name(name):

    result = re.search(r"^([\w .-]*), ([\w .-]*)$", name)

    if result == None:

        return name


    return "{} {}".format(result[2], result[1])
```
## Command:
```bash
$ diff rearrange1.py rearrange2.py 
```
## Code output:
```bash
6c6

<     result = re.search(r"^([\w .]*), ([\w .]*)$", name)

---

>     result = re.search(r"^([\w .-]*), ([\w .-]*)$", name)
```
## Command:
```bash
$ diff validations1.py validations2.py 
```
## Code output:
```bash
5c5,6

<	assert (type(username) == str), "username must be a string"

--

>	if type(username) != str: 

> 	    raise TypeError("username must be a string")

11a13,15

>	    return False

>	# Usernames can't begin with a number

>	if username[0].isnumeric():
```
## Command:
```bash
$ diff -u validations1.py validations2.py 
```
## Code output:
```bash
--- validations1.py	2019-06-06 14:28:49.639209499 +0200

+++ validations2.py	2019-06-06 14:30:48.019360890 +0200

@@ -2,7 +2,8 @@

 

 

 def validate_user(username, minlen):

-    assert type(username) == str, "username must be a string"

+    if type(username) != str:

+        raise TypeError("username must be a string")

     if minlen < 1:

         raise ValueError("minlen must be at least 1")

     

@@ -10,5 +11,8 @@

         return False

     if not username.isalnum():

         return False

+    # Usernames can't begin with a number

+    if username[0].isnumeric():

+        return False

     return True
```
