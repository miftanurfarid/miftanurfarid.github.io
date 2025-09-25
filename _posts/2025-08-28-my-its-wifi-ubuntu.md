---
layout: post
title: Akses internet ITS melalui myITS-WiFi di Ubuntu
date: 2025-08-28 09:00:00
description: Panduan singkat untuk mengakses internet di dalam kampus ITS melalui myITS-WiFi
tags: ["linux"]
categories: linux
---

Semua teman saya yang menggunakan OS Windows tidak menghadapi masalah saat mengakses my-ITS-WiFi. Connect ke myITS-WiFi, muncul pop-up username dan password, isi dengan email ITS dan passwordnya, selesai. Berbeda untuk saya yang menggunakan linux, entah mengapa tidak sesederhana itu. Seperti ini tampilan awalnya.

<div class="row mt-3">
    <div class="col-sm-3 mt-3 mt-md-0"></div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2025/wifi_auth.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-3 mt-3 mt-md-0"></div>
</div>

Poin-poin yang perlu diatur:
- **Authentication** ganti **Protected EAP (PEAP)**.
- Pilih (centang) **No CA certificate is required**.
- **PEAP version** pilih **Automatic**.
- **Inner authentication** pilih **MSCHAPv2**.
- **Username** diisi email ITS
- **Password** diisi password email ITS

<div class="row mt-3">
    <div class="col-sm-3 mt-3 mt-md-0"></div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2025/myITS-WiFi.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-3 mt-3 mt-md-0"></div>
</div>
