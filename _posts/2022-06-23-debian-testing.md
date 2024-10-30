---
layout: post
title: Switching from Debian Stable to Debian Testing with Indonesian Repository
date: 2022-06-23 20:06:00
description: Steps to switch a Debian installation from Stable to Testing using a local Indonesian repository.
tags: linux debian stable testing repository
categories: linux
---

To switch from Debian Stable to Debian Testing and utilize an Indonesian repository, follow these steps:

1. **Backup the current `sources.list` file:**
   ```
   sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
   ```
   This creates a backup of your current sources list in case you need to revert to the Stable release.

2. **Create a new `sources.list`:**
   ```
   sudo echo "deb http://kartolo.sby.datautama.net.id/debian/ testing main contrib non-free" > /etc/apt/sources.list
   ```
   This command replaces the sources to point to the Testing repository at an Indonesian mirror.

3. **Update and upgrade packages:**
   ```
   sudo apt update && sudo apt upgrade -y && sudo apt dist-upgrade -y
   ```
   This will update the package list and upgrade your system to Debian Testing. The `dist-upgrade` command ensures that all dependencies are managed correctly for the Testing branch.

Switching to Testing allows access to newer packages than those in Debian Stable, while using a local repository can improve download speeds and reliability.