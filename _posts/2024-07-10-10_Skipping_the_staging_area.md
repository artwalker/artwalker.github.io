---
title: 10 Skipping the staging area  
date: 2024-07-05 22:29:00 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Command:
```bash
$ vim all_checks.py
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

main()
```
## Command:
```bash
git commit -a -m "Call check_reboot from main, exit with 1 on error"
```
## Code output:
```bash
[master 033f27a] Call check_reboot from main, exit with 1 on error

 1 file changed, 4 insertions(+), 1 deletion(-)
```
## Command:
```bash
git log
```
## Code output:
```bash
commit 033f27a8196987d61c4fd42930f2148b23434a03 (HEAD -> master)

Author: My name <me@example.com>

Date:   Mon Jul 15 14:39:18 2019 +0200

    Call check_reboot from main, exit with 1 on error

commit cc1acbf10fdea6cc07ebf827697666b6a35b0f36

Author: My name <me@example.com>

Date:   Thu Jul 11 17:19:32 2019 +0200

    Add a check_reboot function

commit 6cfc29966acda8213fcd8ac2735b31f3fdbc6c53

Author: My name <me@example.com>

Date:   Thu Jul 11 12:08:46 2019 +0200

    Create and empty all_checks.py
```
