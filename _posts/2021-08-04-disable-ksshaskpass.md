---
layout: post
title: Disabling KSSHASKPASS in Linux
date: 2021-08-04 20:06:00
description: Learn how to disable KSSHASKPASS to prevent SSH_ASKPASS from being set, either by removing the package or modifying your bashrc file.
tags: linux bashrc
categories: linux
---

There are two ways to address the problem:

1. Remove the package (usually ksshaskpass) associated with `/etc/xdg/plasma-workspace/env/ksshaskpass.sh`, as this is where `SSH_ASKPASS` is being set.
2. Add the line `unset SSH_ASKPASS` to your `.bashrc` file.

**Source:**  
[Unix Stack Exchange](https://unix.stackexchange.com/questions/374729/how-to-not-use-ksshaskpass-with-ssh)
