---
title: 1 Applying Changes  
date: 2024-07-06 21:34:00 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ cat cpu_usage.py 
```
## Code output:
```bash
#!/usr/bin/env python3

import psutil

def check_cpu_usage(percent):

    usage = psutil.cpu_percent()

    return usage < percent

if not check_cpu_usage(75):

    print("ERROR! CPU is overloaded")

else:

    print("Everything ok")
```
## Command:
```bash
$ diff -u cpu_usage.py cpu_usage_new.py > cpu_usage.diff
$ cat cpu_usage.diff 
```
## Code output:
```bash
--- cpu_usage.py	2019-06-23 08:16:04.666457429 -0700

+++ cpu_usage_fixed.py	2019-06-23 08:15:37.534370071 -0700

@@ -2,7 +2,8 @@

 import psutil

 

 def check_cpu_usage(percent):

-    usage = psutil.cpu_percent()

+    usage = psutil.cpu_percent(1)

+    print("DEBUG: usage: {}".format(usage))

     return usage < percent

 

 if not check_cpu_usage(75):
```

## Command:
```bash
$ patch cpu_usage.py < cpu_usage.diff
```
## Code output:
```bash
patching file cpu_usage.py
```
## Command:
```bash
$ cat cpu_usage.py
```
## Code output:
```bash
#!/usr/bin/env python3

import psutil

def check_cpu_usage(percent):

    usage = psutil.cpu_percent(1)

    print("DEBUG: usage: {}".format(usage))

    return usage < percent

if not check_cpu_usage(75):

    print("ERROR! CPU is overloaded")

else:

    print("Everything ok")
```
