---
layout: post
title: Membuat folder Downloads dapat menghapus file secara periodik
date: 2024-11-18 09:00:00
description: Sistem operasi Linux memiliki folder bernama Downloads. Sesuai dengan namanya, folder ini berisi semua file yang telah kita unduh. Terkadang, kita merasa repot karena harus menghapus isi folder tersebut secara berkala. Tulisan ini akan membahas cara membuat folder tersebut secara otomatis menghapus isinya dalam interval waktu tertentu.
tags: linux kde 
categories: linux
thumbnail: assets/img/2024/20241113_141136.png
images:
  slider: true
---

Berikut ini adalah cara untuk membuat folder Downloads secara otomatis menghapus isinya dalam interval waktu tertentu.

1. Hapus folder Downloads.

```bash
rm rf ~/Downloads
```

2. Membuat symbolic link dari folder Trash ke folder Downloads

```bash
ln -s /home/fafa/.local/share/Trash/files ~/Downloads
```

3. Mengatur folder Trash untuk menghapus isinya secara berkala. Pada tulisan ini, saya menggunakan desktop environment berupa KDE

<swiper-container keyboard="true" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" rewind="true">
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/2024/20241120_114216.png" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/2024/20241120_114241.png" class="img-fluid rounded z-depth-1" %}</swiper-slide>
</swiper-container>