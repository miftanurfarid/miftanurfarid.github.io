---
layout: post
title: GLIBCXX not found
date: 2024-11-13 13:10:00
description: Saat kita menggunakan Miniconda sebagai Python environment, maka standard library yang kita gunakan sesuai dengan environment tersebut. Oleh karena itu, terkadang kita mengalami beberapa ABI version yang tidak terdapat di standard library. Tulisan ini membahas solusi untuk permasalahan ABI version yang tidak ada di standard library.
tags: python standard library miniconda conda environment
categories: python
thumbnail: assets/img/2024/20241113_141136.png
---

Saat saya menggunakan python library **dlib**, terjadi permasalahan berupa **GLIBCXX_3.4.32 not found**. Permasalahan ABI version tidak terdapat di standard library yang saya alami ini disebabkan oleh penggunaan miniconda. Saat saya menggunakan miniconda, maka standard library yang digunakan merujuk pada directory `/home/<username>/miniconda3/envs/<environment_name>/lib/`. Sedangkan standard library dari sistem operasi saya, yaitu Arch Linux, berada di `/usr/lib/`.

Saya coba menelaah apakah ABI version **GLIBCXX_3.4.32** ada di dalam standard library **libstdc++.so.6** miniconda. Command line yang saya gunakan adalah:

`strings /home/<username>/miniconda3/envs/<environment_name>/lib/libstdc++.so.6 | grep GLIBCXX_3.4.32`

Jika command line tersebut tidak menghasilkan apa pun, maka **GLIBCXX_3.4.32** tidak ada di dalam **libstdc++.so.6**

Kemudian saya coba menelaahnya kembali namun di standard library sistem operasi saya, yaitu di `/usr/lib`, dengan command line yang serupa, yaitu:

`strings /usr/lib/libstdc++.so.6 | grep GLIBCXX_3.4.32`

Hasil yang ditunjukkan adalah **GLIBCXX_3.4.32** berada di standard library sistem operasi saya.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024/20241113_135902.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Solusi untuk permasalahan ini adalah menyalin standard library dari `/usr/lib/` ke `/home/<username>/miniconda3/envs/<environment_name>/lib/`. Namun sebelum itu, saya perlu membuat *backup* terhadap standard library di miniconda. Saya menggunakan command line berikut ini untuk membuat backnya:

`mv /home/<username>/miniconda3/envs/<environment_name>/lib/libstdc++.so.6 /home/<username>/miniconda3/envs/<environment_name>/lib/libstdc++.so.6.BAK`

lalu menyalin menggunakan command line:

`cp /usr/lib/libstdc++.so.6 /home/<username>/miniconda3/envs/<environment_name>/lib/`

Sekarang jika saya melakukan penelaahan kembali ABI Version-nya maka **GLIBCXX_3.4.32** sudah ada di dalam standard library miniconda.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2024/20241113_140949.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

**Catatan**:
- Ganti `<username` sesuai dengan username sistem operasi linux anda.
- Ganti juga `<environment_name>` dengan nama python environment yang anda buat melalui miniconda atau conda.