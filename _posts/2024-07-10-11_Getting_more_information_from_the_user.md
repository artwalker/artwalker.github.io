---
title: 11 Getting more information from the user  
date: 2024-07-05 22:28:30 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ git log -p
```
## Code output:
```bash
commit 033f27a8196987d61c4fd42930f2148b23434a03 (HEAD -> master)

Author: My name <artwalker@example.com>

Date:   Mon Jul 15 14:39:18 2023 +0200

    Call check_reboot from main, exit with 1 on error

diff --git a/all_checks.py b/all_checks.py

index 340f1f7..710266a 100644

--- a/all_checks.py

+++ b/all_checks.py

@@ -1,12 +1,15 @@

 #!/usr/bin/env python3

 

 import os

+import sys

 

 def check_reboot():

     """Returns True if the computer has a pending reboot."""

     return os.path.exists("/run/reboot-required")

(...)
```
## Command:
```bash
$ git log
```
## Code output:
```bash
commit 033f27a8196987d61c4fd42930f2148b23434a03 (HEAD -> master)

Author: My name <artwalker@example.com>

Date:   Mon Jul 15 14:39:18 2023 +0200

    Call check_reboot from main, exit with 1 on error

commit cc1acbf10fdea6cc07ebf827697666b6a35b0f36

Author: My name <artwalker@example.com>

Date:   Thu Jul 11 17:19:32 2023 +0200

    Add a check_reboot function

(...)

```
## Command:
```bash
$ git show cc1acbf10fdea6cc07ebf827697666b6a35b0f36
```
## Code output:
```bash
commit cc1acbf10fdea6cc07ebf827697666b6a35b0f36

Author: My name <artwalker@example.com>

Date:   Thu Jul 11 17:19:32 2023 +0200

    Add a check_reboot function

diff --git a/all_checks.py b/all_checks.py

index c0d03b3..340f1f7 100644

--- a/all_checks.py

+++ b/all_checks.py

@@ -1,5 +1,11 @@

 #!/usr/bin/env python3

 

+import os

+

+def check_reboot():

+    """Returns True if the computer has a pending reboot."""

+    return os.path.exists("/run/reboot-required")

+

 def main():

     Pass
```
## Command:
```bash
$ git log --stat
```
## Code output:
```bash
commit 033f27a8196987d61c4fd42930f2148b23434a03 (HEAD -> master)

Author: My name <artwalker@example.com>

Date:   Mon Jul 15 14:39:18 2023 +0200

    Call check_reboot from main, exit with 1 on error

 all_checks.py | 5 ++++-

 1 file changed, 4 insertions(+), 1 deletion(-)

(...)
```
## Command:
```bash
$ vim  all_checks.py
```
## File with code:
```python
#!/usr/bin/env python3
  
import os
import sys

def check_reboot():
    """Returns True if the computer has a pending reboot."""
    return os.path.exists("/run/reboot-required")

def main():
    if check_reboot():
        print("Pending Reboot.")
        sys.exit(1)

    print("Everything ok.")
    sys.exit(0)

main()
```
## Command:
```bash
$ git diff
```
## Code output:
```bash
diff --git a/all_checks.py b/all_checks.py

index 710266a..fdc4476 100644

--- a/all_checks.py

+++ b/all_checks.py

@@ -12,4 +12,7 @@ def main():

         print("Pending Reboot.")

         sys.exit(1)

 

+    print("Everything ok.")

+    sys.exit(0)

+

 main()
```
## Command:
```bash
$ git add -p
```
## Code output:
```bash
diff --git a/all_checks.py b/all_checks.py

index 710266a..fdc4476 100644

--- a/all_checks.py

+++ b/all_checks.py

@@ -12,4 +12,7 @@ def main():

         print("Pending Reboot.")

         sys.exit(1)

 

+    print("Everything ok.")

+    sys.exit(0)

+

 main()

Stage this hunk [y,n,q,a,d,e,?]? y
```
## Command:
```bash
$ git diff
# Only show the staged changes
$ git diff --staged
```
## Code output:
```bash
diff --git a/all_checks.py b/all_checks.py

index 710266a..fdc4476 100644

--- a/all_checks.py

+++ b/all_checks.py

@@ -12,4 +12,7 @@ def main():

         print("Pending Reboot.")

         sys.exit(1)

 

+    print("Everything ok.")

+    sys.exit(0)

+

 main()
```
## Command:
```bash
$ git commit -m 'Add a message when everything is ok'
```
## Code output:
```bash
[master 49d610b] Add a message when everything is ok

 1 file changed, 3 insertions(+)
```
