---
layout: post
title: Creating a Question Bank for Moodle from LaTeX
date: 2024-10-04 09:06:00
description: Use LaTeX to generate Moodle-compatible quiz questions, including multiple-choice with code snippets and external files, for efficient course content setup.
tags: latex moodle 
categories: software
---

The LaTeX example below is for a multiple-choice quiz question. Since this question includes an external file (`soal1.py`), there are two key considerations:

- The `minted` package is required. If using this package, you need to compile with the `-shell-escape` option.
- The external file must be in the same directory as the LaTeX file.

My example command for compiling LaTeX with `pdflatex` is as follows:

```bash
pdflatex -shell-escape -synctex=1 -interaction=nonstopmode tugas.tex
```

**Example `tugas.tex` File:**

```latex
\documentclass[12pt]{article}
\usepackage[utf8]{inputenc}
\usepackage{moodle}
\usepackage{graphicx}
\usepackage{amsmath}
\usepackage{geometry}
\usepackage{minted}
 
\geometry{
    a4paper,
    inner=15mm,
    outer=15mm,
    top=15mm,
    bottom=15mm,
}
 
\begin{document}
     
    \begin{quiz}{Percabangan dalam Pemrograman Python}
 
        % Soal 1: Penggunaan IF
        \begin{multi}[points=10]{Penggunaan IF}
            Berikut adalah potongan kode Python:
            \inputminted{python}{soal1.py}
            Apa keluaran dari kode tersebut jika input = 10?
            \item Aku tidak suka bilangan itu!
            \item* Aku suka bilangan itu!
            \item Error
            \item Tidak ada output
        \end{multi}
 
    \end{quiz}
     
\end{document}
```

**Note:** The file to be uploaded to Moodle is not the `.tex` file but the `.xml` file.

**Example PDF Output from `pdflatex`:**

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/pdf-from-latex.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Example appearance in Moodle:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/moodle.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

For complete documentation on Moodle LaTeX, see [Moodle LaTeX Guide](https://ctan.math.utah.edu/ctan/tex-archive/macros/latex/contrib/moodle/moodle.pdf).