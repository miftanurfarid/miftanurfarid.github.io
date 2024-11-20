---
layout: post
title: Membuat Python Environment di JupyterHub
date: 2024-11-02 09:00:00
description: Tulisan ini menjelaskan tentang cara membuat Python Environment di JupyterHub yang memiliki akses terbatas pada sistem operasinya
tags: python environment jupyterhub
categories: python
thumbnail: assets/img/2024/20241108_094801.png
images:
  slider: true
---
---

JupyterHub umumnya memberikan akses terbatas pada sistem operasinya. Sehingga untuk melakukan instalasi python versi tertentu cukup rumit. Berikut ini adalah cara yang saya gunakan untuk membuat python environment di jupyterhub dengan versi python tertentu.

1. Misalkan saya ingin menggunakan Python 3.11

    `conda create -n py311 python=3.11`

    `py311` adalah nama python environment yang akan kita buat. kalian bebas menggunakan nama apa pun.

2. Cara untuk mengaktifkan python environment tersebut di terminal adalah `conda activate py311` sedangkan untuk menonaktifkan adalah `conda deactivate`

3. Jika kita membuka tab baru, maka python environment kita tidak akan muncul di halaman launcher

    <div class="row mt-3">
        <div class="col-sm mt-3 mt-md-0">
            {% include figure.liquid loading="eager" path="assets/img/2024/20241108_093704.png" class="img-fluid rounded z-depth-1" %}
        </div>
    </div>

    Lalu, bagaimana cara kita membuat python environment yang sudah kita buat tadi ada di halaman launcher?

4. Kita kembali ke terminal, kemudian aktifkan python environment yang sudah kita buat

    `conda activate py311`

5. install ipykernel

    `conda install ipykernel`

6. Memasang kernel baru untuk IPython, yang memungkinkan kita menjalankan kode Python dalam Jupyter Notebook atau JupyterLab.

    `ipython kernel install --user --name=py311`

7. Nonaktifkan python environment

    `conda deactivate`

8. Matikan server dengan cara pilih **File**, **Hub Control Panel**, **Stop My Server**

9. Kemudian nyalakan **Start My Server**

10. Jika kita melihat *Launcher*, maka python environment kita sudah muncul.
<swiper-container keyboard="true" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" rewind="true">
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/2024/20241108_094801.png" class="img-fluid rounded z-depth-1" %}</swiper-slide>
  <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/2024/20241108_094824.png" class="img-fluid rounded z-depth-1" %}</swiper-slide>
</swiper-container>


Referensi:
- https://stackoverflow.com/questions/56713744/how-to-create-conda-environment-with-specific-python-version
- https://stackoverflow.com/questions/53004311/how-to-add-conda-environment-to-jupyter-lab