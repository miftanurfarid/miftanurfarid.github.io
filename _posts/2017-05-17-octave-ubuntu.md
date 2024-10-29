---
layout: post
title: Installing Octave 4.2.0 on Ubuntu 16.04
date: 2017-05-17 15:06:00
description: This post provides a step-by-step guide on how to install Octave 4.2.0 on Ubuntu 16.04, including downloading the source, installing dependencies, and configuring the environment.
tags: linux octave ubuntu
categories: linux octave
---

**Installing Octave 4.2.0 on Ubuntu 16.04**

1. **Download Octave 4.2.0 source:**
   - Through terminal emulator:
     ```bash
     wget https://ftp.gnu.org/gnu/octave/octave-4.2.0.tar.gz
     ```
   - Extract Octave:
     ```bash
     tar -xvf octave-4.2.0.tar.gz
     ```
   - Or download via browser.

2. **Install dependencies:**
   ```bash
   sudo apt-get install gcc g++ gfortran make libblas-dev liblapack-dev libpcre3-dev libarpack2-dev libcurl4-gnutls-dev epstool libfftw3-dev transfig libfltk1.3-dev libfontconfig1-dev libfreetype6-dev libgl2ps-dev libglpk-dev libreadline-dev gnuplot-x11 libgraphicsmagick++1-dev libhdf5-serial-dev openjdk-8-jdk libsndfile1-dev llvm-dev lpr texinfo libgl1-mesa-dev libosmesa6-dev pstoedit portaudio19-dev libqhull-dev libqrupdate-dev libqscintilla2-dev libqt4-dev libqtcore4 libqtwebkit4 libqt4-network libqtgui4 libqt4-opengl-dev libsuitesparse-dev texlive libxft-dev zlib1g-dev autoconf automake bison flex gperf gzip icoutils librsvg2-bin libtool perl rsync tar
   ```

3. **To ensure all linked libraries support 64-bit variables, download OpenBLAS here:**
   - [OpenBLAS GitHub Repository](https://github.com/xianyi/OpenBLAS.git)
   - Extract it, go to the OpenBLAS directory, then open the `Makefile.rule` file.
   - Remove the `#` from `BINARY=64` and `INTERFACE64=1`, then save.

4. **In the terminal emulator:**
   ```bash
   make
   sudo make install
   sudo apt-get install libopenblas-base
   ```

5. **Navigate to the extracted Octave folder:**
   ```bash
   ./configure JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64 LD_LIBRARY_PATH=/opt/OpenBLAS/lib CPPFLAGS=-I/opt/OpenBLAS/include LDFLAGS=-L/opt/OpenBLAS/lib --enable-64
   make
   sudo make install
   ```

**If the following error appears:**
```
octave-cli: error while loading shared libraries: libopenblas.so.0: cannot open shared object file: No such file or directory
```

**Solution:**
```bash
sudo apt-get install libopenblas-base
octave --force-gui
```

Then set it to the launcher.

**If an error occurs when running the command above, the solution is to change the owner from root to user:**
```bash
sudo chown -R user:user /home/username/.config/octave/
```

**If `ctrl + c` causes a crash, run this in the terminal:**
```bash
export OMP_NUM_THREADS=1
```

**Sources:**
- [Octave for Debian systems](http://wiki.octave.org/Octave_for_Debian_systems)
- [OpenBLAS GitHub Repository](https://github.com/xianyi/OpenBLAS)
- [OpenBLAS Installation Guide](https://github.com/xianyi/OpenBLAS/wiki/Installation-Guide)
