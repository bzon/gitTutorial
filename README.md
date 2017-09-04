# Git Tutorial Overview

The purpose of this README is to guide a users with zero to minimal knowledge in Git SCM using a Unix Terminal (Git Bash for Windows users).  

The full Git SCM documentation can be found [here](https://git-scm.com/docs).  

## Table of Contents
- [Installation](#installation)
- [Setting up Local Git Configuration](#setting-up-local-git-configuration)
- [Creating a Local Git Repository](#creating-a-local-git-repository)
- [Basic Git usage and commands](#basic-git-usage-and-commands)
	* [Adding files in a Git repository](#adding-files-in-a-git-repository)
	* [Tracking or Staging a file](#tracking-or-staging-a-file)
	* [Commit a Staged file](#commit-a-staged-file)
	* [Untracking or Unstaging a file](#untracking-or-unstaging-a-file)
	* [Interactive Challenge](#interactive-challenge)
- [Git Branches](#git-branches)
- [Gitlab](#gitlab)
	* [Gitlab User Guide](#gitlab-user-guide)

# Installation

For **Windows users**, install Git & Git Bash  
https://git-scm.com/download/win

Online installation and Git Basic guide for Windows user  
https://www.youtube.com/watch?v=Y9XZQO1n_7c

For **Mac OSX users**    
```bash
brew install git
```

# Setting up Local Git Configuration

__Command line__: User & Email setup 
```bash
git config --global user.name "John Bryan Sazon"
git config --global user.email "john.bryan.j.sazon@accenture.com"
```

__Command line__: Storing Git credentials so you don't have to type password everytime
```bash
git config --global credential.helper store
```

__Command line__: View Git configurations  
```bash
git config --list
```

__Command line__: View Git configurations from the .gitconfig file  
```bash
cat ~/.gitconfig
```
Command Standard Output:  
```bash
$ cat ~/.gitconfig 
[credential]
	helper = store
[user]
	name = John Bryan Sazon
	email = john.bryan.j.sazon@accenture.com
```

# Creating a Local Git repository

__Command line__: Create an empty directory && `cd` into it 
```bash
mkdir -p Training/Git/my_repository
cd Training/Git/my_repository
```

__Command line__: Initialize the empty `my_repository` directory as a Git repository  
```bash
git init .
```
`git init` Command Standard Output:     
```bash
Initialized empty Git repository in /Users/bryanguestuser/Training/Git/my_repository/.git/
```

# Basic Git usage and commands

**Current working directory**: `Training/Git/my_repository`

## Creating a new file

__Command line__: Create a file  
```bash
touch readme.md
```

__Command line__: Using `git status` to view repository status 
```bash
git status
```
__Command Output__:
```bash
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	readme.md
```
Git tells you that `readme.md` file is `untracked`  

## Tracking or Staging a file

__Command line__: Using `git add` to track a file  
```bash
git add readme.md
```

__Command line__: Using `git status` to identify repository status
```bash
git status
```
__Command Output__:
```bash
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   readme.md
```

This is called `staging`. Git tells you that you tracked the `readme.md` file and it is ready for a `commit`.

__BUT__ what if we change the content of the `readme.md` file because you are not ready to `commit` your change in the repository for this file?  

### Modifying the file after git add
Before proceeding, try modifying the file as you would normally edit a text file. Once done, run a `git status`.  

__Command line__: Using `git status` to view repository status 
```bash
git status
```
__Command Output__:
```bash
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   readme.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   readme.md
```
Now we see that the `readme.md` file is both tracked and untracked. 

__WHY?__ 

It is because when we run the `git add` command to add a file, git __ONLY__ `stage` the file as it was at the time you executed the command. Remember, we only [executed git add once](#tracking-or-staging-a-file) after creating the file and before any modification, and the `git status` command above tells you that there is an `unstaged` change in the file because we [modified](#modifying-the-file-after-git-add) it just after running `git add readme.md`.  

Run the `git add` command once again, to include the latest revision of the `readme.md` file.  

__Command line__: Using `git add` to track a file  
```bash
git add readme.md
```
__Command Output__:
```bash
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   readme.md
```

## Commit a Staged file

__NOTE__: If you are new to `vim` please see the [vim guide](./VIM.md)

`git commit` lets you save your local revisions into your local git repository.  

__Command line__: Using `git commit`
```bash
git commit
```
You will end up in the `vim` screen where you can enter your `commit message` and view the changes that will be committed.  

![gif](./img/vim_git_commit.gif)

Use `git log` to view the commit history of the current repository. Use `git log --oneline --decorate` to display a decorated output.  

## Untracking or unstaging a file

There will be cases that you may have already `staged` a new revision in the repository by running `git add`,  

Let's first create a file and stage it.  

__Command line__: Create a file 
```bash
touch unwanted_file.txt
```

__Command line__: Use `git add` to track a file  
```bash
git add unwanted_file.txt
```
__Command Output__:
```bash
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   unwanted_file.txt
```

__BUT__ you suddenly want to revert or `unstaged` it for some reason to prevent having that revision to be included in your `git commit`.  

__Command line__: Using `git rm` to untrack a file 
```bash
git rm --cached unwanted_file.txt
```
__Command line__: Using `git status` to view repository status 
```bash
git status
```
__Command Output__:
```bash
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	unwanted_file.txt
```

You can run `rm unwanted_file.txt` to delete the unwanted file.  

## Interactive Challenge

Try to complete the following! https://try.github.io/  

# Git Branches

A branch in Git is simply a lightweight movable pointer to one of these commits. The default branch name in Git is master . As you start making commits, you're given a master branch that points to the last commit you made. Every time you commit, it moves forward automatically.  

https://git-scm.com/book/id/v2/Git-Branching-Branches-in-a-Nutshell

__Command line__: Using `git branch` to view the branches in the local repository
```bash
git branch
```
__Command Output__:  
```
* master
```

## Create a branch

__Command line__: Using `git checkout` to create a branch from the `master` branch  
```bash
git checkout -b feature-branch
```
__Command line__: Using `git branch` to view the branches in the local repository
```bash
git branch
```
```bash
* feature-branch
  master
```

__Command line__: Using `git checkout` to go to a different branch  
```bash
git checkout master # goes to master branch
git checkout feature-branch # goes to feature-branch
git checkout - # goes to the previous branch
```

# Gitlab

__Why Gitlab?__  

Gitlab is basically like Bitbucket and Github but it is the only one that offers an opensource version of their software, the `Community Edition`. You can install in your own computer or host it within your project's infrastructure for __FREE__ unlike Bitbucket and Github.  

From a DevOps project requirement perspective it gives you a nice web user interface, a code review feature and an integration with Jenkins. More Gitlab features can be found [here](https://about.gitlab.com/features/).  

__Disadvantage?__  

It's a heavy weight Git server and there are too many features that aren't necessarily needed.  

__Opensource Alternatives?__

[Gerrit](https://www.gerritcodereview.com) - 
The best Git code review tool ever made. Extending it with more features requires you to compile the plugins and install it by following some documentations. The user is not so intuitive and it takes a while to get a hang of it.  

Another famous opensource Git server is [Gogs](https://gogs.io). It is still in its pre-release 1 phase and it doesn't support Code Reviews yet. 

## Gitlab User Guide

* [Registration](https://gitlab.com/users/sign_in)
* [Gitlab Basics](https://docs.gitlab.com/ce/gitlab-basics/README.html)
	* [Create your SSH Keys](https://docs.gitlab.com/ce/gitlab-basics/create-your-ssh-keys.html)
	* [Create a group](https://docs.gitlab.com/ce/user/group/index.html#create-a-new-group)
	* [Create a project](https://docs.gitlab.com/ce/gitlab-basics/create-project.html)
	* [Adding a file](https://docs.gitlab.com/ce/user/project/repository/web_editor.html#create-a-file)
	* [Creating a branch](https://docs.gitlab.com/ce/user/project/repository/web_editor.html#create-a-new-branch)
	* [Forking a project](https://docs.gitlab.com/ce/gitlab-basics/fork-project.html)
	* [Creating a Merge Request](https://docs.gitlab.com/ce/gitlab-basics/add-merge-request.html)