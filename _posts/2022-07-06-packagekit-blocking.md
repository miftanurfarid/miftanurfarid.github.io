---
layout: post
title: Resolving PackageKit Blocking Zypper in OpenSUSE
date: 2022-07-06 20:06:00
description: Steps to stop PackageKit from interfering with Zypper package management in OpenSUSE.
tags: linux packagekit opensuse service
categories: linux
---

If PackageKit is blocking Zypper, you can disable and mask the PackageKit service to prevent it from running:

1. **Disable and stop PackageKit:**
   ```bash
   sudo systemctl disable --now packagekit.service
   ```
   This command stops the service immediately and disables it from starting on boot.

2. **Mask the PackageKit service:**
   ```bash
   sudo systemctl mask packagekit.service
   ```
   Masking the service prevents it from being started by any means, ensuring it won’t interfere with Zypper.

By disabling and masking PackageKit, you can freely use Zypper for package management without interruptions.