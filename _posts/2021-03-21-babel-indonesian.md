---
layout: post
title: Adding Indonesian Babel to Arch Linux
date: 2021-03-21 15:06:00
description: A quick guide to installing the Indonesian language package for LaTeX on Arch Linux using the command line.
tags: latex arch linux
categories: latex linux
---

**Adding Indonesian Babel to Arch Linux**

Command line:

```bash
sudo pacman -S texlive-langextra
```

In the tex file:

```latex
\usepackage[indonesian]{babel}
```
