---
layout: post
title: Merging Multiple PDFs into One PDF on Linux
date: 2021-03-23 15:06:00
description: Combine several PDF files into a single PDF using command line tools like convert or pdfunite.
tags: linux
categories: linux
---

**Command Line:**

1. Using `convert`:
   ```bash
   convert file1.pdf file2.pdf merged.pdf
   ```

2. Or using `pdfunite`:
   ```bash
   pdfunite in-1.pdf in-2.pdf in-n.pdf out.pdf
   ```