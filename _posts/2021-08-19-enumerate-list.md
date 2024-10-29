---
layout: post
title: How to Start an Enumerate List at a Number Other Than 1
date: 2021-08-19 15:06:00
description: Discover how to customize the starting number of an enumerate list in LaTeX by modifying the counter.
tags: latex enumerate
categories: latex
---

You can change the counter named `enumi` like this:

```latex
\begin{enumerate}
    \setcounter{enumi}{4}
    \item fifth element
\end{enumerate}
```

(If you have lists at deeper levels of nesting, the relevant counters are `enumii`, `enumiii`, and `enumiv`.)

**Source:**  
https://tex.stackexchange.com/questions/142/how-can-i-make-an-enumerate-list-start-at-something-other-than-1