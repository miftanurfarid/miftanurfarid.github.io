---
layout: post
title: Resolving Installation Issues with Arch Linux Using Archinstall
date: 2024-03-13 09:06:00
description: Learn how to fix installation errors related to plasma-wayland-session in Arch Linux when using archinstall by updating the keyring and the archinstall package.
tags: linux arch plasma wayland archinstall opensuse tumbleweed
categories: linux
---

OpenSUSE Tumbleweed is the rolling release Linux distribution I usually use. However, since Plasma 6 won't be released soon in Tumbleweed, I decided to switch to Arch Linux. The installation process for Arch Linux is no longer as complicated as it once was; we can use archinstall.

While I was installing Arch Linux using archinstall, I encountered a failure during the installation of the plasma-wayland-session. The error message was `error: target not found plasma-wayland-session`. It turned out that archinstall was still using an outdated package list. The solution I found in the Arch Linux forum is as follows:

1. Update the keyring: `pacman -Sy archlinux-keyring`
2. Update archinstall: `pacman -Sy archinstall`
3. Proceed with the installation of Arch Linux using archinstall.

[Source](https://bbs.archlinux.org/viewtopic.php?id=293529)
