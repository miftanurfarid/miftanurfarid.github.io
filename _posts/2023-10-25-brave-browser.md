---
layout: post
title: Fixing Text and Image Rendering Issues in Brave Browser After Linux Update
date: 2023-10-25 08:06:00
description: Learn how to resolve text and image rendering problems in Brave browser, often caused by kernel updates, by deleting the GPUCache folder.
tags: brave browser linux 
categories: linux software
---

Text and image rendering issues in the Brave browser often occur following a kernel update. This problem is not exclusive to Brave; Google Chrome typically experiences similar issues.

The solution to this problem is to delete the GPUCache:

```bash
rm -fr .config/BraveSoftware/Brave-Browser/Default/GPUCache/
```

For more information, visit: [Brave Community Discussion](https://community.brave.com/t/text-and-images-stopped-rendering-after-ubuntu-22-04-update/488953/2)
