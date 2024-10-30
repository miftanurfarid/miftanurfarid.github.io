---
layout: post
title: Creating a Windows LiveUSB on Linux with WoeUSB
date: 2023-08-01 09:06:00
description: Easily set up a Windows bootable USB drive on Linux by using WoeUSB to prepare and write the Windows ISO to your flash drive.
tags: linux windows liveusb woeusb
categories: linux windows
---

1. Download WoeUSB from [https://github.com/WoeUSB/WoeUSB/releases/download/v5.2.4/woeusb-5.2.4.bash](https://github.com/WoeUSB/WoeUSB/releases/download/v5.2.4/woeusb-5.2.4.bash).
2. Run the command: `sudo ./woeusb-5.2.4.bash --device Win10_22H2_English_x64.iso /dev/sdb`. Adjust `Win10_22H2_English_x64.iso` to match the name of your Windows ISO file, and `/dev/sdb` to the directory of your flash drive.
3. Wait for the process to complete.
