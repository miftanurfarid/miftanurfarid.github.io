---
layout: post
title: Permanently Changing the Theme of MOC Player
date: 2021-09-18 20:06:00
description: Learn how to set a permanent theme for the Music On Console (MOC) player on Linux, enhancing your audio experience with customized aesthetics.
tags: python try-except
categories: python
---

MOC (Music On Console) is a versatile and lightweight music player for Unix-like operating systems. It operates in a terminal environment and is known for its simplicity and ease of use. One of the ways to enhance your experience with MOC is by customizing its appearance, specifically by changing its theme. This post will guide you through the steps to change the MOC theme permanently, ensuring that your preferred aesthetics are maintained across sessions.

### Why Change the Theme?

Changing the theme of MOC can significantly enhance your overall experience while using the player. A well-chosen theme can improve visibility and make navigation through your music collection more enjoyable. Whether you prefer a dark theme for a minimalist look or a bright theme for better visibility, MOC provides options that cater to various preferences.

### Steps to Change the Theme Permanently

1. **Copy the Default Configuration File**:  
   First, you need to create a configuration file for MOC if one does not already exist. You can do this by copying the example configuration file provided by MOC. Open your terminal and run the following command:

   ```bash
   sudo cp /usr/share/doc/moc/examples/config.example ~/.moc/config
   ```

   This command copies the example configuration file to your home directory under `~/.moc/config`. This file will be used to store your personalized settings.

2. **Change Ownership of the Configuration File**:  
   After copying the configuration file, it’s essential to ensure that your user account has ownership of it. This allows you to edit the file without requiring elevated permissions. Use the following command:

   ```bash
   sudo chown $USER:$USER ~/.moc/config
   ```

   This command changes the ownership of the `config` file to your user account, making it easier to modify.

3. **Set Your Preferred Theme**:  
   Now you can specify which theme you want to use. Open the configuration file in your preferred text editor (e.g., `nano`, `vim`, or `gedit`) and add the following lines:

   ```bash
   echo "Theme = /usr/share/moc/themes/green_theme" >> ~/.moc/config
   echo "XTermTheme = /usr/share/moc/themes/green_theme" >> ~/.moc/config
   ```

   These commands append the theme settings to your MOC configuration file. Replace `green_theme` with the name of any other theme available in the `/usr/share/moc/themes/` directory if you want to try different styles.

4. **Restart MOC**:  
   After saving your changes, restart MOC to apply the new theme. Simply exit the player and start it again. You should now see your new theme in effect.

### Additional Resources and Themes

MOC comes with several themes pre-installed, which can be found in the `/usr/share/moc/themes/` directory. You can explore these themes and choose one that suits your style best. If you're interested in customizing themes further, you may also consider creating your own by modifying the existing theme files. Just be sure to back up any files before making changes!

### Conclusion

Changing the theme of MOC permanently allows you to tailor the music player to your liking, enhancing your audio experience. Following the steps outlined above will help you set your preferred theme quickly and easily. For more detailed customization options and features, refer to the MOC documentation or the community forums.

**Source**: [Linux Slaves - Change MOCP Default Theme on Linux](https://www.linuxslaves.com/2016/04/change-mocp-default-theme-on-linux.html)
