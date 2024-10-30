---
layout: post
title: Removing Packman Packages in openSUSE
date: 2023-10-23 05:06:00
description: Learn how to remove the Packman repository, perform a distribution upgrade, and clean up orphaned packages for a streamlined openSUSE setup.
tags: linux opensuse packman repository
categories: linux
---

1. Remove the Packman repository:
   ```
   sudo zypper removerepo packman
   ```
2. Run a distribution upgrade with vendor change allowed:
   ```
   sudo zypper dup --allow-vendor-change
   ```
3. Use `zypper packages --orphaned` to list unused packages, then remove them if desired:
   ```
   sudo zypper remove <orphaned-package-name>
   ```
