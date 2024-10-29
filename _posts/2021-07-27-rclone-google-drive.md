---
layout: post
title: Backing Up Data to Google Drive with Rclone
date: 2021-07-27 15:06:00
description: A step-by-step guide on configuring and using Rclone to back up data to Google Drive.
tags: linux rclone google-drive
categories: linux
---

**A. Preparation**

1. **Install Rclone**

   Since I am using Manjaro, which is Arch-based, to install Rclone:

   ```bash
   sudo pacman -S rclone
   ```

2. **Create a Folder for Mounting the Drive**

   Here, I create a folder in my home directory named `mydrive`:
   
   ```bash
   mkdir ~/mydrive
   ```
   Thus, the directory will be `~/mydrive`.

**B. Configuring Rclone**

1. **Open Terminal and Type:**
   ```bash
   rclone config
   ```

2. **Type 'n' for New Remote.**
   ```
   n/s/q> n
   ```

3. **Type the Remote Name.** Here, I will use the name `ITK_drive`.
   ```
   name> ITK_drive
   ```
   A list of drives supported by Rclone will appear.

4. **Since I will use Google Drive, type 15 or select 'drive'.**
   ```
   Storage> 15
   ```

5. **Leave the following command lines blank or press Enter:**
   ```
   client_id> 
   client_secret> 
   ```

6. **Choose 1 for Full access to all files, excluding Application Data Folder.**
   ```
   scope> 1
   ```

7. **Leave the following command lines blank or press Enter:**
   ```
   root_folder_id> 
   ```

8. **Leave the following command lines blank or press Enter:**
   ```
   service_account_file> 
   ```

9. **Choose 'n' or press Enter for Edit advanced config?**
   ```
   y/n> n
   ```

10. **Choose 'y' or press Enter to Use auto config?**
    ```
    y/n> y
    ```

11. **An authentication window will appear in your browser. Choose Allow, and you will see:**
    ```
    'Success!
    All done. Please go back to rclone.
    ```

12. **Return to the terminal. Choose 'n' or press Enter for Configure this as a Shared Drive (Team Drive)?**
    ```
    y/n> n
    ```

13. **The overall configuration will appear. Choose 'y'.**
    ```
    y/e/d> y
    ```

14. **Then exit the Rclone configuration by choosing 'q'.**
    ```
    e/n/d/r/c/s/q> q
    ```

Now, the Rclone configuration is complete. Next is how to use it.

**C. Using Rclone**

1. **If you forget the name of the remote you created earlier, run:**
   ```bash
   rclone listremotes
   ```
   A list of the remotes you have created will appear:
   ```
   > rclone listremotes
   ITK_drive:
   ```

2. **Mount the remote to the folder created earlier.**
   ```bash
   rclone mount ITK_drive: ~/mydrive
   ```

3. **Open a new terminal/tab to perform the data backup.**

4. **The backup command I will use is rsync:**
   ```bash
   rsync -Pruv /folder/yang/akan/dibackup ~/mydrive/folder/tujuan
   ```
