---
layout: post
title: GLIBCXX_3.4.32 not found
date: 2024-11-13 13:10:00
description: Saat kita menggunakan Miniconda sebagai Python environment, maka standard library yang kita gunakan sesuai dengan environment tersebut. Oleh karena itu, terkadang kita mengalami beberapa ABI version yang tidak terdapat di standard library. Tulisan ini membahas solusi untuk permasalahan ABI version yang tidak ada di standard library.
tags: python standard library miniconda conda environment
categories: python
---

Saat saya menggunakan python library `dlib` terjadi permasalahan berupa GLIBCXX_3.4.32 not found. Permasalahan ABI version tidak terdapat di standard library yang saya alami disebabkan oleh penggunaan miniconda. Saat kita menggunakan miniconda, standard library berada di directory `/home/<username>/miniconda3/envs/<environmen_name>/lib/`. Sedangkan standard library dari sistem operasi saya--Arch Linux-- berada di `/usr/lib/`