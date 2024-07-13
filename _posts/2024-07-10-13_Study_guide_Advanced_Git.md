---
title: 13 Study guide Advanced Git  
date: 2024-07-05 22:28:27 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
| Command | Explanation |
| -------- | -------- |
| [git commit -a](https://git-scm.com/docs/git-commit#Documentation/git-commit.txt---all)  | automatically stages the files that have been locally modified. New files which have not been published yet are not affected.  |
| [git log -p](https://git-scm.com/docs/git-log#generate_patch_text_with_p)  | produces patch text. A patch file is used to share your local changes with others without pushing your changes to the main branch of the repo.  |
| [git show](https://git-scm.com/docs/git-show)  | shows you one or more object(s) such as blobs, trees, tags, and commits.  |
| [git diff](https://git-scm.com/docs/git-diff)  | is similar to the Linux `diff` command, and can show the changes between commits, changes between the working tree and index, changes between two trees, changes from a merge, and so on.  |
| [git diff --staged](https://git-scm.com/docs/git-diff)  | is an alias of $ git diff --cached, which  shows all staged files compared to the named commit.  |
| [git add -p](https://git-scm.com/docs/git-add)  | allows a user to interactively review patches before adding to the current commit.  |
| [git mv](https://git-scm.com/docs/git-mv)  | is similar to the Linux `mv` command. This command can move or rename a file, directory, or symlink.  |
| [git rm](https://git-scm.com/docs/git-rm)  | is similar to the Linux `rm` command. This command deletes or removes a file from the working tree.  |
## .gitignore files
.gitignore files are used to tell the git tool to intentionally ignore some files in a given Git repository. For example, this can be useful for configuration files or metadata files that a user may not want to check into the master branch. 

When writing a [.gitignore](https://git-scm.com/docs/gitignore) file, there are some specific formats which help tell Git how to read the text in the file. For example, a line starting with # is a comment; a slash / is a directory separator.

some examples of configurations included in a `.gitignore` file:
```.gitignore
# Compiled source #
###################
*.com
*.class
*.dll
*.exe
*.o
*.so

# Packages #
############
# it's better to unpack these files and commit the raw source
# git has its own built in compression methods
*.7z
*.dmg
*.gz
*.iso
*.jar
*.rar
*.tar
*.zip

# Logs and databases #
######################
*.log
*.sql
*.sqlite

# OS generated files #
######################
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db
```
