---
layout: post
title: Konfigurasi doom emacs untuk pemrograman python
date: 2024-12-07 09:00:00
description: Tulisan ini berisikan cara untuk melakukan konfigurasi pada doom emacs untuk pemrograman python
tags: ["linux", "doom emacs", "python"]
categories: linux
---

1. Modifikasi `:lang` di `init.el`

    ```
    (doom! 
        ...
        :lang 
        (python +lsp +pyright +conda)
        ...)
    ```

2. Modifikasi `:tools` di `init.el`

    ```
    (doom! 
        ...
        :tools
        (lsp +peek)
        ...)
    ```

3. Tambahkan baris kode berikut ke `config.el`. Di sini saya menggunakan miniconda[^1].

    ```
    (use-package! conda
      :config
      (setq conda-anaconda-home (expand-file-name  "~/miniconda3"))
      (conda-env-initialize-interactive-shells)
      (conda-env-initialize-eshell)
      (conda-env-autoactivate-mode t)
      (add-hook 'find-file-hook (lambda () (when (bound-and-true-p conda-project-env-path)
                                        (conda-env-activate-for-buffer)))))
    
    ```

4. Lakukan `.emacs.d/bin/doom sync`

5. Mengaktifkan python environment dengan cara `M-x conda-env-activate ...`

[^1]: Tautan: https://docs.anaconda.com/miniconda/install/#quick-command-line-install
