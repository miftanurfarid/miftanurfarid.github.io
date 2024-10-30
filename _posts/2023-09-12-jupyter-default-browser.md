---
layout: post
title: Setting the Default Browser for JupyterLab on Linux
date: 2023-09-12 09:06:00
description: Learn how to configure JupyterLab to open in your preferred browser by adjusting the jupyter_lab_config.py file.
tags: linux git branch
categories: linux git
---

To change the default browser for JupyterLab on Linux, follow these steps:

1. Open a terminal and run the following command to generate a configuration file for JupyterLab:
   ```
   jupyter-lab --generate-config
   ```

   This will create a `jupyter_lab_config.py` file in `$HOME/.jupyter`. 

2. Open this file in your preferred text editor.

3. Find the line:
   ```python
   #c.ServerApp.browser = ''
   ```
   Remove the `#` to uncomment it.

4. Replace the empty string `''` with the path to your desired browser. For instance, if you want to use Microsoft Edge, update the line to:
   ```python
   c.ServerApp.browser = '/opt/microsoft/msedge/msedge %s'
   ```

5. Save the changes.

Now, when you launch JupyterLab, it should open in your chosen browser by default.
