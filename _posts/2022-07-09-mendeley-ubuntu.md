---
layout: post
title: Installing Mendeley Desktop on Ubuntu 22.04
date: 2022-07-09 20:06:00
description: Guide to resolving dependency issues when installing Mendeley Desktop on Ubuntu 22.04, including steps to download, modify, and configure necessary packages and dependencies to ensure compatibility.
tags: linux mendeley ubuntu
categories: linux
---

**Install Mendeley Desktop on Ubuntu 22.04**

When attempting to install Mendeley Desktop on Ubuntu 22.04, I encountered the following error:

```plaintext
dpkg: dependency problems prevent configuration of mendeleydesktop:
 mendeleydesktop depends on python; however:
  Package python is not installed.
```

Here’s the solution that resolved the issue for me:

1. **Download the Mendeley Desktop `.deb` package**

   ```bash
   axel -a https://desktop-download.mendeley.com/download/apt/pool/main/m/mendeleydesktop/mendeleydesktop_1.19.8-stable_amd64.deb
   ```

2. **Ensure `python` command points to Python**  
   If the `python` command is missing, install the `python-is-python3` package:

   ```bash
   sudo apt install python-is-python3
   ```

3. **Extract the `.deb` file**

   ```bash
   ar x mendeleydesktop_1.19.8-stable_amd64.deb
   ```

4. **Extract the control archive**

   ```bash
   tar xzf control.tar.gz
   ```

5. **Edit dependencies**  
   Open `control` in a text editor and remove `python` from the dependencies list. Then repack the control archive:

   ```bash
   FILES=$(tar zxvf control.tar.gz)
   tar zcf control.tar.gz $FILES
   ```

6. **Repack the `.deb` file**

   ```bash
   ar rcs mendeleydesktop_1.19.8-stable_amd64_modified.deb debian-binary control.tar.gz data.tar.xz
   ```

7. **Install Python 2**

   ```bash
   sudo apt install python2
   ```

8. **Create a symlink for Python 2**  
   Point `/usr/bin/python` to Python 2:

   ```bash
   sudo mv /usr/bin/python /usr/bin/python_old
   sudo ln -s /usr/bin/python2 /usr/bin/python
   ```

9. **Install the modified Mendeley Desktop package**

   ```bash
   sudo dpkg -i mendeleydesktop_1.19.8-stable_amd64_modified.deb
   ```

10. **Restore the original `python` symlink**

    ```bash
    sudo rm /usr/bin/python
    sudo mv /usr/bin/python_old /usr/bin/python
    ```

**References:**

- [Ask Ubuntu: Installing Mendeley on Ubuntu 22.04](https://askubuntu.com/questions/1405042/how-to-install-mendeley-on-ubuntu-22-04)
- [Server Fault: Ignoring Dependencies in apt-get](https://serverfault.com/questions/250224/how-do-i-get-apt-get-to-ignore-some-dependencies)
