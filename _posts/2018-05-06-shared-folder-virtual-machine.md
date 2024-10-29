---
layout: post
title: Creating a Shared Folder from Ubuntu to Manjaro in VirtualBox
date: 2018-05-06 15:06:00
description: This guide explains how to set up a shared folder between an Ubuntu host and a Manjaro guest in VirtualBox, including steps for configuring shared folder settings and mounting the folder in the guest system.
tags: linux ubuntu manjaro virtualbox
categories: linux software
---

Here’s how to create a shared folder from an Ubuntu host to a Manjaro guest. Yes, both are Linux—I'm just trying out Manjaro in VirtualBox before migrating from Ubuntu. 😄

1. **Select settings on the virtual machine.**

2. **Choose Shared Folders** and click the icon to add a new shared folder. 
   - In the "Add Share" window, enter the directory path of the folder you want to share with the guest in the "Folder Path" field, and provide a name for the folder in the "Folder Name" field. 
   - Check **Auto-mount** and **Make Permanent**, then click **OK**.

3. **Optional Settings:**
   - Check **Read-only** if you want the guest to have read-only permission, without write or edit access to the content in the folder.
   - Check **Auto-mount** to automatically mount the folder (in this case, the Manjaro guest might not auto-mount).
   - Check **Make Permanent** so that the auto-mount will persist even after the guest is restarted.

4. **Next, open a terminal in the guest (Manjaro), and type:**
   ```bash
   sudo mount -t vboxsf Shared /home/abudzar/Shared -o uid=1000,gid=1000
   ```
   - `Shared` is the name of the folder shared from the host (Ubuntu), and `/home/abudzar/Shared` is the directory where the `Shared` folder will be mounted in the guest (Manjaro).
   - `uid=1000` and `gid=1000` represent the current user ID and group ID of the guest. If you don't enter this command, the owner of the shared folder and files will be root.