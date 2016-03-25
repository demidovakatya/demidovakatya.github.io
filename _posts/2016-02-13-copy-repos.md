---
layout: post
title:  "How to copy github repos"
published: true

---

This is a quick note to myself.

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
