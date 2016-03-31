---
layout: post
title: Introduction to git rebase
date: 2016-03-31
author: Ishan Khare
categories: Tutorial
---

{% assign icons = site.data.icons %}

Recently there have been lots of new developments in the imapfw community. Lots of new people coming in for contributing under GSoC. One of the trickiest thing newcomers encounter when starting to contribute is with some *git operations* particularly with **squashing**.

This blog will guide through the basics of `how to squash` and also highlight **other useful** options provided by the `git rebase` command.

## Setting up the playground
For the purpose of this tutorial we will be working with a simple gist. Keep in mind *gists are full-blown git repositories*, but they **DO NOT** support folders.

1. Go ahead and clone the following:  
    ``` shell
    git clone git@gist.github.com:10ef9336a6b9c7572ada9ec6229fe9b7.git
    ```

2. See what's in the repo:
    ``` shell
    cd 10ef9336a6b9c7572ada9ec6229fe9b7
    git log --graph --oneline
    ```

## Current state
By running the last command, what we get is this:
```
* b68977f fix another typo word
* ac573c6 fixed a typo word
* 6102ded
```

As we can see, we have 2 trivial commits, that we can group as one, with the following constraints:

1. Keeping changes from both the commits.
2. Only show either one of the commit message, or a completely new commit message

And that's what we call __squashing__

## Enters `git rebase`
We will be using the `-i` option, which translates to `interactive`. The command has roughly the following syntax for squashing:
``` shell
git rebase -i HEAD~<number-of-commits-to-squash>
```
Since want to `squash` __previous 2 commits__, our command should be:

``` shell
git rebase -i HEAD~2
```
What this yields is something like this:
```
pick ac573c6 fixed a typo word
pick b68977f fix another typo word

# Rebase 6102ded..b68977f onto 6102ded (2 command(s))
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out

```

### The above output can roughly be divided into 2 categories:
1. The __un-commented__ lines (1-2)
    ``` shell
    pick ac573c6 fixed a typo word
pick b68977f fix another typo word
    ```
are exactly the commits we need to squash, so our `HEAD~2` part was correct.

2. The __commented__ lines (ones starting with `#`). This basically is a _short documentation_ of what options can we use here and what they mean.

For the purpose of `squashing` we can see the line:
```
# s, squash = use commit, but meld into previous commit
```

That's exactly the behavior we need.

### The Squash

1. We now do the necessary changes, and they should look something like this  
    ``` shell
    pick ac573c6 fixed a typo word
    squash b68977f fix another typo word

    # Rebase 6102ded..b68977f onto 6102ded (2 command(s))
    #
    # Commands:
    # p, pick = use commit
    # r, reword = use commit, but edit the commit message
    # e, edit = use commit, but stop for amending
    # s, squash = use commit, but meld into previous commit
    # f, fixup = like "squash", but discard this commit's log message
    # x, exec = run command (the rest of the line) using shell
    #
    # These lines can be re-ordered; they are executed from top to bottom.
    #
    # If you remove a line here THAT COMMIT WILL BE LOST.
    #
    # However, if you remove everything, the rebase will be aborted.
    #
    # Note that empty commits are commented out
    ```

2. As soon as we write this to the disk and exit, a new window editor will open with the following:  
    ``` shell
    # This is a combination of 2 commits.
    # The first commit's message is:

    fixed a typo word

    Signed-off-by: Ishan Khare <ishankhare07@gmail.com>

    # This is the 2nd commit message:

    fix another typo word

    Signed-off-by: Ishan Khare <ishankhare07@gmail.com>

    # Please enter the commit message for your changes. Lines starting
    # with '#' will be ignored, and an empty message aborts the commit.
    #
    # Date:      Thu Mar 31 19:00:41 2016 +0530
    #
    # rebase in progress; onto 6102ded
    # You are currently editing a commit while rebasing branch 'master' on '6102ded'.
    #
    # Changes to be committed:
    #	modified:   zen.txt
    #
    # Untracked files:
    #	output.txt
    #
    ```

3. We can see the 2 commits, go ahead and remove 1, edit the other one. There is __NO NEED__ to do any changes with comments, they won't matter. It should finally look something like this:  
    ``` shell
    # This is a combination of 2 commits.
    # The first commit's message is:

    fix word typos

    Signed-off-by: Ishan Khare <ishankhare07@gmail.com>

    # This is the 2nd commit message:

    # Please enter the commit message for your changes. Lines starting
    # with '#' will be ignored, and an empty message aborts the commit.
    #
    # Date:      Thu Mar 31 19:00:41 2016 +0530
    #
    # rebase in progress; onto 6102ded
    # You are currently editing a commit while rebasing branch 'master' on '6102ded'.
    #
    # Changes to be committed:
    #	modified:   zen.txt
    #
    # Untracked files:
    #	output.txt
    #
    ```

We removed the __second commit message__ and the `sign-off` which finally gives us a single _squashed_ commit.
