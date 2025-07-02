---
layout: post
title: Menampilkan Label LaTeX di Matplotlib
date: 2025-07-01 09:00:00
description: Cara mudah menampilkan simbol atau persamaan matematika LaTeX pada label plot matplotlib dengan dukungan usetex.
tags: ["python", "matplotlib", "latex"]
categories: latex
thumbnail: assets/img/2025/dengan_usetex.png
---

Apakah kamu pernah membuat grafik di Python menggunakan matplotlib dan ingin menampilkan simbol matematika seperti $$ x $$, $$ f(x) $$, atau integral seperti $$ \int_a^b f(x)\,dx $$? 

Secara bawaan, matplotlib mendukung sintaks LaTeX secara internal untuk membuat label tampak seperti dalam dokumen matematika profesional. Kamu hanya perlu membungkus ekspresi matematika dengan tanda dolar (`$...$`). Jika ingin hasil yang **benar-benar menyerupai LaTeX asli**, kamu dapat mengaktifkan dukungan LaTeX penuh dengan `usetex=True`.

Apa perbedaan antara hanya menggunakan tanda dolar dan mengaktifkan dukungan LaTeX penuh dengan `usetex=True`?

<div class="row mt-3">
  <div class="col-md-6">
    <p class="text-center"><strong>Tanpa usetex</strong></p>
    {% include figure.liquid loading="eager" path="assets/img/2025/tanpa_usetex.png" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-md-6">
    <p class="text-center"><strong>Dengan usetex</strong></p>
    {% include figure.liquid loading="eager" path="assets/img/2025/dengan_usetex.png" class="img-fluid rounded z-depth-1" %}
  </div>
</div>

Kode Python tanpa menggunakan `usetex`

```python
import matplotlib.pyplot as plt

plt.plot([0, 1], [0, 1])

plt.xlabel('$x$')
plt.ylabel('$f(x)$')

plt.title('$y = \int_a^b f(x)\,dx$')
plt.grid(True)
plt.show()
```


Kode Python menggunakan `usetex`


```python
import matplotlib.pyplot as plt
import matplotlib as mpl

mpl.rcParams['text.usetex'] = True

plt.plot([0, 1], [0, 1])

plt.xlabel('$x$')
plt.ylabel('$f(x)$')

plt.title(r'$y = \int_a^b f(x)\,dx$')
plt.grid(True)
plt.show()
```