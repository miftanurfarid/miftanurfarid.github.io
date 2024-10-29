---
layout: post
title: Install Jekyll on OpenSuse
date: 2021-08-04 15:06:00
description: A step-by-step guide to installing Jekyll, a popular static site generator, on OpenSuse using rbenv.
tags: linux opensuse jekyll
categories: linux
---

1. **Install required dependencies** (for example, nokogiri):

   Replace the version `libgdbm4` with whatever version your release provides.
   ```bash
   sudo zypper in autoconf libopenssl-devel libyaml-devel readline-devel libxslt-devel ncurses-devel libffi-devel zlib-devel gdbm-devel libgdbm4
   ```

2. **Clone rbenv to your home folder**: `~/.rbenv`
   ```bash
   git clone https://github.com/rbenv/rbenv.git ~/.rbenv
   ```

3. **Add `~/.rbenv/bin` to your `$PATH`** so that you can use rbenv’s command-line utility. Also, adding `~/.rbenv/bin/rbenv init` to your `~/.bashrc` file will let you load rbenv automatically.
   ```bash
   echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
   echo 'eval "$(rbenv init -)"' >> ~/.bashrc
   ```

4. **Source your `.bashrc` to load config changes.**
   ```bash
   source ~/.bashrc
   ```

5. **Type `rbenv` to ensure it’s working:**
   ```bash
   rbenv
   ```

6. **To use the `rbenv install` command**, which simplifies the installation process for new versions of Ruby, you should install `ruby-build`, which we will install as a plugin for rbenv through git:
   ```bash
   git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
   ```

7. **List available Ruby versions for installation:**
   ```bash
   rbenv install -l
   ```

   This will output a long list of Ruby versions; pick one to install, for example, `2.5.0`.

   **Note**: Do not use `sudo` as it is not required from your own home directory. 

   ```bash
   rbenv install 2.5.0
   ```

   Wait for the installation to finish.

8. **Set the new installation of Ruby as your global Ruby version.**
   ```bash
   rbenv global 2.5.0
   ```

9. **Check your reported Ruby version:**
   ```bash
   ruby -v
   ```

10. **Install Jekyll.**
    ```bash
    gem install jekyll
    ```

**Source:**  
[GitHub Jekyll Issue #6852](https://github.com/jekyll/jekyll/issues/6852)
