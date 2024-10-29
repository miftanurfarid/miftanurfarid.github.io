---
layout: post
title: Add Git Branch Name to Bash Prompt
date: 2021-08-17 15:06:00
description: Learn how to customize your bash prompt to display the current Git branch name for easier version control navigation.
tags: linux git bashrc
categories: linux
---

1. Add the following lines to your `~/.bashrc` file:

   ```bash
   parse_git_branch() {
       git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
   }

   export PS1="\u@\h \[\033[32m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[00m\] $ "
   ```

   Where:

   - `\u@\h \[\033[32m\]` displays the user, host name, and its color.
   - `\w\[\033[33m\]` shows the current working directory and its color.
   - `\$(parse_git_branch)\[\033[00m\]` displays the git branch name and its color.

   Typically, I only display the current working directory and the git branch name without showing the user and hostname.

2. Run the command `source ~/.bashrc` to apply the changes.

**Source:**  
[Coderwall](https://coderwall.com/p/fasnya/add-git-branch-name-to-bash-prompt)
