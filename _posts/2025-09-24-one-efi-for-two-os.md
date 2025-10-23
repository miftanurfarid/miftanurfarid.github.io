---
layout: post
title: Satu EFI untuk Dua Operating System (Ubuntu 24.04 dan Windows 11) pada dua disk yang berbeda
date: 2025-09-24 09:00:00
description: Panduan singkat untuk menginstall dua operating system (OS) atau biasa disebut sebagai Dual Boot namun hanya menggunakan satu partisi EFI.
tags: ["linux", "windows"]
categories: linux
---

Berikut ini adalah panduan singkat untuk meng-install Ubuntu 25.04 dan Windows 11 pada disk SSD yang berbeda namun hanya menggunakan 1 partisi EFI. **Sebagai catatan**, kedua disk yang saya miliki ini sudah dalam kondisi terformat.

Pertama kita install Windows 11 ke Disk pertama

- Saat masuk ke live USB windows, tekan `shift` + `f10` untuk memunculkan terminal command prompt.
- Masuk ke diskpart, `diskpart`.
- Cek semua disk yang ada, `list disk`.
- Misalkan `Disk 0` adalah disk yang akan kita install Windows 11, maka `select disk 0`.
- Hapus semua partisi, `clean`.
- Ubah format menjadi GPT, `convert gpt`
- Buat partisi EFI, `create partition efi size=1024`. Di sini saya menggunakan size 1 GB untuk EFI
- Format partisi EFI ke FAT32, `format quick fs=fat32`
- Keluar diskpart, `exit`
- Lanjutkan proses instalasi Windows 11 hingga pada bagian pemilihan partisi sebagai tempat Windows 11, pilih partisi yang kosong (selain EFI).
- Lanjutkan proses instalasi hingga selesai.

Kita asumsikan Windows 11 sudah berhasil terpasang, lanjut install Ubuntu 25.04.

- Saat masuk ke live USB Ubuntu dan pada bagian Disk Setup, pilih **Manual Installation**
- Di bagian bawah ada pilihan **Device for boot loader installation**, di sini pilih partisi EFI yang sudah ada.
- Lanjutkan proses instalasi Ubuntu hingga selesai.

```mermaid
flowchart TD
    A[Mulai] --> B{Persiapan Disk}
    B -->|Sudah diformat| C[Masuk ke Live USB Windows 11]
    
    %% Bagian Instalasi Windows 11
    C --> D[Buka Command Prompt (Shift + F10)]
    D --> E[Masuk ke DiskPart: ketik 'diskpart']
    E --> F[List Disk: ketik 'list disk']
    F --> G[Pilih disk untuk Windows 11 (misal Disk 0): 'select disk 0']
    G --> H[Hapus semua partisi: 'clean']
    H --> I[Ubah format menjadi GPT: 'convert gpt']
    I --> J[Buat partisi EFI 1GB: 'create partition efi size=1024']
    J --> K[Format partisi EFI: 'format quick fs=fat32']
    K --> L[Keluar dari DiskPart: 'exit']
    L --> M[Lanjutkan instalasi Windows 11]
    M --> N[Pilih partisi kosong (selain EFI) untuk Windows]
    N --> O[Lanjutkan instalasi Windows 11 hingga selesai]
    
    %% Transisi ke Instalasi Ubuntu
    O --> P[Reboot ke Live USB Ubuntu 25.04]
    P --> Q[Pilih Manual Installation pada Disk Setup]
    Q --> R[Pilih partisi kosong di disk kedua untuk Ubuntu]
    R --> S[Pilih partisi EFI yang sudah ada sebagai Device for Boot Loader Installation]
    S --> T[Lanjutkan instalasi Ubuntu hingga selesai]
    T --> U[Selesai – Dual Boot Windows 11 + Ubuntu 25.04 dengan satu partisi EFI]
    
    %% Styling
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style U fill:#bbf,stroke:#333,stroke-width:2px
```