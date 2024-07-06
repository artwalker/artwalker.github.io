---
title: 2 Practical Application of diff and patch  
date: 2024-07-06 21:33:00 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## File with code
```python
#!/usr/bin/env python3

import shutil

def check_disk_usage(disk, min_absolute, min_percent):
	"""Returns True if there is enough free disk space, false otherwise."""
	du = shutil.disk_usage(disk)
	# Calculate the percentage of free space
	percent_free = 100 * du.free / du.total
	# Calculate how many free gigabytes
	gigabytes_free = du.free / 2**30
	if percent_free < min_percent or gigabytes_free < min_absolute:
		return False
	return True

# Check for at least 2 GB and 10% free
if not check_disk_usage("/", 2*2**30, 10):
	print("ERROR: Not enough disk space")
	return 1

print("Everything ok")
return 0
```
## Command:
```bash
$ cp disk_usage.py disk_usage_original.py 
$ cp disk_usage.py disk_usage_fixed.py 
# this throws an error
$ ./disk_usage_fixed.py 
```
## Code output:
```bash
File "./disk_usage_fixed.py", line 19

	return 1

	^

SyntaxError: 'return' outside function
```
## File with code 
Adds `import sys` at the beginning, then change `return 1` to `sys.exit(1)` and `return 0` to `sys.exit(0)`.
```python
#!/usr/bin/env python3

import shutil
import sys

def check_disk_usage(disk, min_absolute, min_percent):
	"""Returns True if there is enough free disk space, false otherwise."""
	du = shutil.disk_usage(disk)
	# Calculate the percentage of free space
	percent_free = 100 * du.free / du.total
	# Calculate how many free gigabytes
	gigabytes_free = du.free / 2**30
	if percent_free < min_percent or gigabytes_free < min_absolute:
		return False
	return True

# Check for at least 2 GB and 10% free
if not check_disk_usage("/", 2*2**30, 10):
	print("ERROR: Not enough disk space")
	sys.exit(1)

print("Everything ok")
sys.exit(0)
```
## Command:
```bash
$ ./disk_usage_fixed.py
```
## Code output:
```bash
ERROR: Not enough disk space
```
## File with code 
Change `check_disk_usage("/", 2*2**30, 10)` in previous file to `check_disk_usage("/", 2, 10)`.Because the code `gigabytes_free = du.free / 2**30` changes the value to gigabytes, so don't need to multiply by `2**30`.
```python
#!/usr/bin/env python3

import shutil
import sys

def check_disk_usage(disk, min_absolute, min_percent):
	"""Returns True if there is enough free disk space, false otherwise."""
	du = shutil.disk_usage(disk)
	# Calculate the percentage of free space
	percent_free = 100 * du.free / du.total
	# Calculate how many free gigabytes
	gigabytes_free = du.free / 2**30
	if percent_free < min_percent or gigabytes_free < min_absolute:
		return False
	return True

# Check for at least 2 GB and 10% free
if not check_disk_usage("/", 2, 10):
	print("ERROR: Not enough disk space")
	sys.exit(1)

print("Everything ok")
sys.exit(0)
```
## Command:
```bash
$ ./disk_usage_fixed.py 
```
## Code output:
```bash
Everything ok
```
## Command:
```bash
$ diff -u disk_usage_original.py disk_usage_fixed.py > disk_usage.diff
$ cat disk_usage.diff 
```
## Code output:
```bash
--- disk_usage_original.py	2023-06-22 15:13:38.591579963 -0700

+++ disk_usage_fixed.py	2023-06-22 15:41:35.013023839 -0700

@@ -1,6 +1,7 @@

#!/usr/bin/env python3



import shutil

+import sys



def check_disk_usage(disk, min_absolute, min_percent):

	"""Returns True if there is enough free disk space, false otherwise."""

@@ -14,9 +15,9 @@

	return True



# Check for at least 2 GB and 10% free

-if not check_disk_usage("/", 2*2**30, 10):

+if not check_disk_usage("/", 2, 10):

	print("ERROR: Not enough disk space")

-    return 1

+    sys.exit(1)



print("Everything ok")

-return 0

+sys.exit(0)
```
## Command:
```bash
$ patch disk_usage.py < disk_usage.diff 
```
## Code output:
```bash
patching file disk_usage.py
```
## Command:
```bash
$ ./disk_usage.py 
```
## Code output:
```bash
Everything ok
```
