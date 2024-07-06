---
title: 8 Study guide Git  
date: 2024-07-06 21:27:00 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
## Study Guide: Git 

In any Git project, there are three sections: **the Git directory, the working tree, and the staging area.** 
This study guide provides some basic concepts and commands that can help you **get started with Git** as well as guidelines to help you **write an effective commit message**.

### Git config command

The Git config command is used to set the values to identify who made changes to Git repositories. To set the values of user.email and user.name to your email and name, type: 

```bash
: ~$ git config  - -global user.email “artwalker@artist.com”
: ~$ git config  - -global user.name “My name”
```

### Git init command

```bash
: ~/projects$ git init
```
The `git init` command can create a new empty repository in a current directory or re-initialize an existing one. 

### Git ls -la command

```bash
: ~/projects$ ls -la
```
The Git `ls - la` command checks that an identified directory exists.
```bash
: ~/projects$ ls -l .git/
```
The `ls-l .git` command checks inside the directory to see the different things that it contains. This is called the Git directory. The Git directory is a database for your Git project that stores the changes and the change history.

### Git add command
```bash
:~/projects$ git add ram_usage.py
```

Using the `git add` command allows Git to track your file and uses the selected file as a parameter when adding it to the staging area. The staging area is a file maintained by Git that contains all the information about what files and changes are going to go into your next commit.

### Git status command

```bash
:~/projects$ git status
```
The `git status` command is used to get some information about the current working tree and pending changes.

### Git commit command

```bash
:~/projects$ git commit
```
The `git commit` command is run to remove changes made from the staging area to the .git directory. When this command is run, it tells Git to save changes. A text editor is opened that allows a commit message to be entered.

### Guidelines for writing commit messages
A commit message is generally broken into two sections: **a short summary** and **a description of the changes**. When the `git commit` command is run, Git will open a text editor to write your commit message. A good commit message includes the following:

#### Summary
The first line contains the summary, formatted as a header, containing 50 characters or less. 

#### Description
The description is usually kept under 72 characters and provides detailed information about the change. It can include references to bugs or issues that will be fixed with the change. It also can include links to more information when relevant. 

#### An example of a commit message
```vim
Commit message style guide for Git

The first line of a commit message serves as a summary.  When displayed
on the web, it's often styled as a heading, and in emails, it's
typically used as the subject.  As such, you should capitalize it and
omit any trailing punctuation.  Aim for about 50 characters, give or
take, otherwise it may be painfully truncated in some contexts.  Write
it, along with the rest of your message, in the imperative tense: "Fix
bug" and not "Fixed bug" or "Fixes bug".  Consistent wording makes it
easier to mentally process a list of commits.

Oftentimes a subject by itself is sufficient.  When it's not, add a
blank line (this is important) followed by one or more paragraphs hard
wrapped to 72 characters.  Git is strongly opinionated that the author
is responsible for line breaks; if you omit them, command line tooling
will show it as one extremely long unwrapped line.  Fortunately, most
text editors are capable of automating this.

:q
```

### Key takeaways
Knowing basic Git commands and guidelines for writing better messages can help you get started with Git as well as better communicate with others.
