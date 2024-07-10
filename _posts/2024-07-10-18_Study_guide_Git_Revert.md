---
title: 18 Study guide Git Revert  
date: 2024-07-05 22:31:07 +0800  
categories: [Git&&GitHub]  
tags: [git,github]  
---
When writing and committing code, making mistakes is a common occurrence. Thankfully, there are multiple ways for you to revert or undo your mistakes. Take a look at the helpful commands below.

## command
[git checkout](https://git-scm.com/docs/git-checkout) is used to switch branches. For example, you might want to pull from your main branch. In this case, you would use the command git checkout main. This will switch to your main branch, allowing you to pull. Then you could switch to another branch by using the command  git checkout <branch>.

[git reset](https://git-scm.com/docs/git-reset#_examples) can be somewhat difficult to understand. Say you have just used the command git add. to stage all of your changes, but then you decide that you are not ready to stage those files. You could use the command git reset to undo the staging of your files.

There are some other useful articles online, which discuss more aggressive approaches to [resetting the repo](https://jwiegley.github.io/git-from-the-bottom-up/3-Reset/4-doing-a-hard-reset.html) (Git repository). As discussed in this article, doing a hard reset can be extremely dangerous. With a hard reset, you run the risk of losing your local changes. There are safer ways to achieve the same effect. For example, you could run git stash, which will temporarily shelve or stash your current changes. This way, your current changes are kept safe, and you can come back to them if needed.

[git commit --amend](https://git-scm.com/docs/git-commit#Documentation/git-commit.txt---amend) is used to make changes to your most recent commit after-the-fact, which can be useful for making notes about or adding files to your most recent commit. Be aware that this `git --amend` command rewrites and replaces your previous commit, so it is best not to use this command on a published commit.

[git revert](https://git-scm.com/docs/git-revert) makes a new commit which effectively rolls back a previous commit. Unlike the git reset command which rewrites your commit history, the git revert command creates a new commit which undoes the changes in a specific commit. Therefore, a revert command is generally safer than a reset command.

For more information on these and other methods to undo something in Git, checkout this [Git Basics - Undoing Things](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things) article.

Additionally, there are some interesting considerations about how git object data is stored, such as the usage of SHA-1.

SHA-1 is what’s known as a hash function, a cryptographic function that generates a digital fingerprint of a file. Theoretically, it’s impossible for two different files to have the same SHA-1 hash, which means that SHA-1 can be used for two things:

* Confirming that the contents of a file have not changed (digital signature).

* Serving as an identifier for the file itself (a token or fingerprint).

Feel free to read more here:
* [SHA-1 collision detection on GitHub.com](https://github.blog/2017-03-20-sha-1-collision-detection-on-github-com/)

Even the most accomplished developers make mistakes in Git. It happens to everyone, so don’t stress about it. You have these and other methods to help you revert or undo your mistakes.

---

Writing and committing code often comes with its share of mistakes. Fortunately, there are several commands available to help you revert or correct those missteps. Below are some useful commands for handling these situations.

## Commands Overview
[git checkout](https://git-scm.com/docs/git-checkout) is primarily used to switch between branches. For instance, if you wish to update from your main branch, you would use `git checkout main`. This switches you to the main branch, enabling you to pull updates. Afterwards, you can switch back to a different branch using `git checkout <branch>`.

Understanding [git reset](https://git-scm.com/docs/git-reset#_examples) can be tricky. Suppose you've just staged all your changes with `git add .`, but decide you're not ready to commit them. You can use `git reset` to undo this staging action.

There are additional online articles that delve into more aggressive methods of [resetting the repo](https://jwiegley.github.io/git-from-the-bottom-up/3-Reset/4-doing-a-hard-reset.html) (Git repository). As noted, performing a hard reset can be very risky, as it could lead to loss of your local changes. However, there are safer alternatives to achieve similar results. For example, `git stash` temporarily shelves or stashes your changes, keeping them safe until you’re ready to retrieve them.

[git commit --amend](https://git-scm.com/docs/git-commit#Documentation/git-commit.txt---amend) allows you to modify your most recent commit, which is handy for adding notes or files that were left out of your initial commit. However, be mindful that using `git --amend` rewrites and replaces your last commit, so it’s advisable not to use this on commits that have already been published.

[git revert](https://git-scm.com/docs/git-revert) creates a new commit that effectively undoes a previous commit. Unlike the `git reset` command, which alters your commit history, `git revert` adds a new commit to reverse the changes from a specific commit, making it a safer option than resetting.

For more detailed information on these and other methods to undo actions in Git, you can refer to this guide: [Git Basics - Undoing Things](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things).

In addition, there are interesting aspects regarding how git object data is stored, particularly concerning the use of SHA-1.

SHA-1 is known as a hash function, a cryptographic tool that generates a digital fingerprint of a file. Ideally, it's improbable for two distinct files to share the same SHA-1 hash, meaning SHA-1 serves two purposes:

* Verifying that the contents of a file remain unchanged (digital signature).
* Acting as a unique identifier for the file itself (token or fingerprint).

For further reading:
* [SHA-1 collision detection on GitHub.com](https://github.blog/2017-03-20-sha-1-collision-detection-on-github-com/)

Even the most experienced developers make mistakes in Git—it happens to everyone. Don't stress; you have these and other tools at your disposal to help revert or correct your mistakes.
