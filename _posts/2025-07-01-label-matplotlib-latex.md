---
layout: post
title: Menampilkan Label LaTeX di Matplotlib
date: 2025-07-01 09:00:00
description: Cara mudah menampilkan simbol atau persamaan matematika LaTeX pada label plot matplotlib dengan dukungan usetex.
tags: ["python", "matplotlib", "latex"]
categories: linux
---

Apakah kamu pernah membuat grafik di Python menggunakan matplotlib dan ingin menampilkan simbol matematika seperti \( x \), \( f(x) \), atau integral seperti \( \int_a^b f(x)\,dx \)? 

Secara default, matplotlib mendukung sintaks LaTeX secara internal untuk membuat label terlihat seperti dalam dokumen matematika profesional. Kamu hanya perlu membungkus ekspresi matematika dengan tanda dolar (`$...$`), dan jika ingin hasil yang **benar-benar mirip LaTeX asli**, kamu bisa mengaktifkan dukungan LaTeX penuh dengan `usetex=True`.

## Cara Mengaktifkan LaTeX di Matplotlib

Langkah pertama adalah mengatur konfigurasi matplotlib agar menggunakan LaTeX untuk merender teks:

```python
import matplotlib as mpl
mpl.rcParams['text.usetex'] = True
```
