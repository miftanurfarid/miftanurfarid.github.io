---
layout: post
title: Menjadikan folder tmp sebagai folder Downloads
date: 2024-11-21 09:00:00
description: Sistem operasi Linux memiliki folder bernama tmp. Folder tmp berfungsi sebagai tempat penyimpanan sementara dan akan dihapus saat OS dinyalakan ulang atau reboot. Tulisan ini akan membahas cara untuk membuat folder tmp sebagai folder Downloads.
tags: linux 
categories: linux
---

Berbeda dengan tulisan sebelumnya, tulisan ini akan menjelaskan cara untuk membuat folder tmp sebagai folder Downloads. Sehingga kita tidak perlu mengatur lagi kapan folder Downloads akan kosong.

1. Hapus folder Downloads.

```bash
rm rf ~/Downloads
```

2. Membuat symbolic link dari folder Trash ke folder Downloads

```bash
ln -s /tmp /home/username/Downloads
```

**Catatan**: `username` perlu diganti dengan username yang anda gunakan