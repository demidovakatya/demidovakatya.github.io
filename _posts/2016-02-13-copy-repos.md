---
layout: post
title:  "How to move Github repos and save commit history"
published: true

---

_This is a quick note to myself._

## The Problem

There are several somehow similar repositories (`project-1`, `project-2` etc) in my Github, and it seems to me that these projects should be moved to a new folder and, as a consequence, to a new repository (`projects`). Sounds easy, right? But wait...

An important note: I want to preserve my commit history. And this is where it gets tough, since git is dark and full of terrors.

However, I've found a decent way to solve the problem.

## The Solution

To begin with, **backup everything**! Right now! Duplicate the folders and hide them somewhere. Otherwise, you may find out in a couple of hours that something important was lost, and this is definitely not a good feeling.

Next, let's **create the target repo** `projects`:

```
~ mkdir projects
~ cd projects
~/projects  git init
Initialized empty Git repository in /Users/~/projects/.git/
```

```
git remote add proj1 https://github.com/you/project-1.git
git fetch proj1
```

```
~ mkdir project-1
~ cd project-1
```

```
git merge project1/master --no-commit
```

# where to copy (folder of the target repo)
$ cd awesome-stuff

# https://github.com/username/whatever.git - remote to be copied 
# whatever - name for the remote
# -f - fetch
$ git remote add -f whatever https://github.com/username/whatever.git

# -s ours - merge strategy
$ git merge -s ours --no-commit whatever/master

# --prefix=something-cool/ - where to copy exactly
$ git read-tree --prefix=something-cool/ -u whatever/master
```

Yay, everything from the `whatever` repo (including history) is copied into `awesome-stuff/something-cool`.
