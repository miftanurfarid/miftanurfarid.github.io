---
layout: post
title: Creating an Example Environment in LaTeX
date: 2021-06-01 15:06:00
description: Learn how to define and use a custom "example" environment in LaTeX documents.
tags: latex
categories: latex
---

Use the preamble:
```latex
\usepackage{amsthm}
\theoremstyle{definition}
\newtheorem{exmp}{Example}[section]
```

In the document section:
```latex
\begin{exmp}
    This is an example problem.
\end{exmp}
```

The output will look like this:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2021-06-01.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>