---
layout: post
title: Gagal Push ke GitHub karena File Terlalu Besar? Begini Cara Mengatasinya Tanpa Git LFS
date: 2025-21-05 09:00:00
description: Panduan singkat untuk mengatasi error push GitHub karena file terlalu besar, tanpa perlu menggunakan Git LFS atau menghapus file dari komputer.
tags: ["linux", "git", "github"]
categories: git
---

Pernahkah kamu mengalami error saat melakukan `git push` ke GitHub seperti ini?

```bash
remote: error: File <nama_file> is 478.79 MB; this exceeds GitHub's file size limit of 100.00 MB
remote: error: GH001: Large files detected. You may want to try Git Large File Storage - https://git-lfs.github.com.
To github.com:username/repo.git
! [remote rejected] main -> main (pre-receive hook declined)
error: failed to push some refs to 'github.com:username/repo.git'
```

Saya sendiri mengalami ini ketika mencoba mengunggah file `.mp4` berukuran hampir 500 MB ke repositori GitHub pribadi saya. Padahal, saya **tidak ingin menggunakan Git LFS** maupun **mengupload file besar tersebut ke GitHub**. Lalu bagaimana solusinya?


1. **Batalkan commit terakhir yang berisi file besar (tanpa menghapus file-nya dari harddisk):**

   ```bash
   git reset --soft HEAD~1
   ```

2. **Hapus file dari staging area (tapi tetap ada di lokal):**

   ```bash
   git rm --cached path/to/file.mp4
   ```

3. **Commit ulang tanpa file besar:**

   ```bash
   git commit -m "Remove large video file to comply with GitHub size limits"
   ```

4. **Ignore file besar agar tidak ikut ke commit selanjutnya:**

   ```bash
   echo "*.mp4" >> .gitignore
   git add .gitignore
   git commit -m "Update .gitignore to exclude large files"
   ```

5. **Push ulang ke GitHub:**

   ```bash
   git push origin main
   ```
