---
layout: post
title: How to Place a Brace on the Right Side for Grouping Cases in LaTeX
date: 2021-09-20 20:06:00
description: Learn how to effectively use the mathtools package to create right-sided braces for grouping cases in your LaTeX documents.
tags: latex mathtools
categories: latex
---

When working with mathematical expressions in LaTeX, you may find the need to group cases using braces. While it's common to see braces on the left side of expressions, sometimes you might want to place them on the right. This can be particularly useful when you want to align your expressions neatly and maintain a clear visual structure.

### Using the `mathtools` Package

To achieve this, you can utilize the `mathtools` package, which enhances the functionality of LaTeX's math typesetting capabilities. The package provides various tools for displaying mathematical symbols and constructs more elegantly.

One of the environments provided by the `mathtools` package is the `rcases*` environment. This environment allows you to create right-sided braces, which can be particularly useful for cases or piecewise functions.

### Example Usage

Here’s how to implement a right brace for grouping cases in your document:

```latex
\documentclass{article}
\usepackage{mathtools}

\begin{document}
 
\[
\begin{rcases*}
E = mc^2 & \text{foo} \\
\int x-3\, dx & \text{barbaz}
\end{rcases*} y = f(x)
\]

\end{document}
```

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2021-09-27-09-26-41.png" class="img-fluid rounded z-depth-1" style="width: 30%;" %}
    </div>
</div>


In this example, the `rcases*` environment is used to create a brace on the right side of the cases. The `&` symbol is used to align the contents of each case, while the `\\` command separates each case line.

- **Line 1:** `E = mc^2 & \text{foo}` defines the first case, where `E = mc^2` is grouped with the label "foo."
- **Line 2:** `\int x-3\, dx & \text{barbaz}` defines the second case, grouping the integral expression with the label "barbaz."
- The brace will appear on the right side of the cases, with the variable `y = f(x)` positioned alongside it.

This approach provides a clean and organized way to present multiple cases while allowing for right-aligned grouping. 

For more complex cases or additional formatting options, refer to the `mathtools` documentation or explore resources available on the LaTeX community forums.
