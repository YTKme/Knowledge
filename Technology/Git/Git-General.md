# Git

## Table of Content
* [Overview](#overview)
* [Basic](#basic)
    * [Command](#command)
        * [Configure](#configure)
        * [Create](#create)
        * [Branch](#branch)
        * [Change](#change)
        * [Synchronize](#synchronize)
        * [Redo](#redo)
* [Reference](#reference)
    * [General](#general)
    * [Advance](#advance)
    * [Secure SHell (SSH)](#secure-shell-ssh)

## Overview

Git is a free and open source distributed version control system
designed to handle everything from small to very large projects with
speed and efficiency.

## Basic

### Command

#### Configure

Configure user information for all local repositories.

```bash
git config [--global] user.name "[name]"
```

Sets the name you want attached to your commit transactions.

```bash
git config [--global] user.email "[email address]"
```

Sets the email you want attached to your commit transactions.

#### Create

A new repository can either be created locally, or an existing
repository can be cloned. When a repository was initialized locally, you
have to push it to GitHub afterwards.

```bash
git init
```

The git init command turns an existing directory into a new Git
repository inside the folder you are running this command. After using
the `git init` command, link the local repository to an empty GitHub
repository using the following command:

```bash
git remote add origin [url]
```

Specifies the remote repository for your local repository. The url
points to a repository on GitHub.

```bash
git clone [url]
```

Clone (download) a repository that already exists on GitHub, including
all of the files, branches, and commits.

#### Branch

Branches are an important part of working with Git. Any commits you make
will be made on the branch you're currently "checked out" to. Use
`git status` to see which branch that is.

```bash
git branch [branch-name]
```

Creates a new branch.

```bash
git switch -c [branch-name]
```

Switches to the specified branch and updates the working directory

```bash
git merge [branch]
```

Combines the specified branch’s history into the current branch. This is
usually done in pull requests, but is an important Git operation.

```bash
git branch -d [branch-name]
```

Deletes the specified branch.

#### Change

Browse and inspect the evolution of project files.

```bash
git log
```

Lists version history for the current branch.

```bash
git log --follow [file]
```

Lists version history for a file, beyond renames (works only for a
single file).

```bash
git diff [first-branch]...[second-branch]
```

Shows content differences between two branches.

```bash
git show [commit]
```

Outputs metadata and content changes of the specified commit.

```bash
git add [file]
```

Snapshots the file in preparation for versioning.

```bash
git commit -m "[descriptive message]"
```

Records file snapshots permanently in version history.

#### Synchronize

Synchronize your local repository with the remote repository on remote
(GitHub).

```bash
git fetch
```

Downloads all history from the remote tracking branches.

```bash
git merge
```

Combines remote tracking branches into current local branch.

```bash
git push
```

Uploads all local branch commits to GitHub.


```bash
git pull
```

Updates your current local working branch with all new commits from the
corresponding remote branch on GitHub. `git pull` is a combination of
`git fetch` and `git merge`.

#### Redo

Erase mistakes and craft replacement history.

```bash
git reset [commit]
```

Undoes all commits after `[commit]`, preserving changes locally.

```bash
git reset --hard [commit]
```

Discards all history and changes back to the specified commit.

> CAUTION! Changing history can have nasty side effects.

## Reference

### General

* [Git (Wikipedia)](https://en.wikipedia.org/wiki/Git)
* [git (Software)](https://git-scm.com/)
* [Getting Git Right](https://www.atlassian.com/git)
* [GitHub Cheatsheet](https://github.github.com/training-kit/)
* [Visual Git Cheatsheet](https://ndpsoftware.com/git-cheatsheet.html)
* [Difference between "git add -A" and "git add ."](https://stackoverflow.com/questions/572549/difference-between-git-add-a-and-git-add)

### Advance

* [So You Think You Know Git - FOSDEM 2024](https://www.youtube.com/watch?v=aolI_Rz0ZqY)
* [So You Think You Know Git Part 2 - DevWorld 2024](https://www.youtube.com/watch?v=Md44rcw13k4)

### Secure SHell (SSH)

* [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent){:target="_blank"}
