---
layout: post
title: Fixing Black Screen with Blinking Cursor Before GRUB in Manjaro
date: 2018-10-16 15:06:00
description: A step-by-step guide to resolve the issue of a blinking cursor on a black screen before accessing GRUB in Manjaro after an abrupt shutdown.
tags: linux manjaro grub
categories: linux
---

### Blinking Cursor on Black Screen Before Entering Manjaro GRUB

It has become a habit of mine to quickly shut down my laptop after a long day of work by using the terminal emulator and running the command:

```bash
shutdown -P 0
```
Boom! The laptop turns off instantly.

I've done this many times without any issues—until one day when I tried to continue working and found that my laptop couldn't access GRUB, getting stuck on a black screen with a blinking cursor. The screen looked something like this:

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Untitled.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

In this situation, I couldn't access either Manjaro or Windows 10. Fortunately, I had installed Windows 10 on a different hard drive from Manjaro, and its GRUB was installed on the hard drive containing Manjaro. So, I could simply select the boot option for the Windows 10 hard drive.

Next, I created a Manjaro Live USB. Initially, I used UNetbootin, but my laptop consistently failed to read the Live USB. The same happened with Rufus. After some research on forums, I found that a good software for creating a Live USB on Windows 10 is Etcher. Sure enough, my laptop could boot into the Manjaro Live USB with UEFI options.

In the Manjaro Live USB environment:

1. Open the terminal emulator.
2. Use root access:
   ```bash
   sudo su
   ```
3. Before fixing the bootloader, install the following packages:
   ```bash
   pacman -S mtools os-prober modprobe efivarfs efibootmgr dosfstools grub
   ```
4. Check the list of partitions to identify where the Manjaro system is installed:
   ```bash
   lsblk -f
   ```
   My Manjaro system is located at `/dev/sdb2`.
5. Mount the system partition to `/mnt`:
   ```bash
   mount /dev/sdb2 /mnt
   ```
   If the boot partition is separate, mount the boot partition to `/boot`:
   ```bash
   mount /dev/sdb1 /boot
   ```
6. Change the directory to `/mnt`:
   ```bash
   cd /mnt
   ```
7. Mount the following systems to the system directory:
   ```bash
   mount -t proc proc /mnt/proc
   mount -t sysfs sys /mnt/sys
   mount -o bind /dev /mnt/dev
   mount -t devpts pts /mnt/dev/pts/
   mount -t efivarfs efivarfs /sys/firmware/efi/efivars
   ```
8. Chroot into the mounted environment:
   ```bash
   chroot /mnt
   ```
9. Create an EFI folder in the boot partition:
   ```bash
   mkdir /boot/efi
   ```
10. Mount the boot partition to the previously created EFI folder:
    ```bash
    mount /dev/sdb1 /boot/efi
    ```
11. Install GRUB with the target directory set to `/boot/efi`:
    ```bash
    grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=manjaro --recheck
    ```
12. Next, update GRUB:
    ```bash
    update-grub
    ```
13. Finally, restart your laptop.

However, after restarting, I found that GRUB didn't display the list of installed operating systems. The screen looked like this:

*grub-prompt*

At the GRUB prompt, execute the following commands:
```bash
grub search.file /etc/manjaro-release root
grub configfile /boot/grub/grub.cfg
```
Next, the GRUB menu for Manjaro will appear. Select Manjaro, open the terminal emulator, and run:
```bash
sudo grub-install /dev/sdb
sudo update-grub
```
Restart the laptop, and the GRUB menu should return to normal, displaying both Manjaro and Windows 10.

### UPDATE
This issue occurred again after a system update:

1. Boot using the Live USB according to the mode in use (UEFI or BIOS-legacy).
2. Press **C** on the main Live USB menu screen. Do not enter the Live OS.
3. At the GRUB prompt:
   ```bash
   grub echo $grub_platform
   ```
   If the output is **pc**, then the mode is BIOS-legacy. If the output is **efi**, then the mode is UEFI. Match the mode selected with the type of Live USB used.
4. Type the following commands:
   ```bash
   grub search.file /etc/manjaro-release root
   grub configfile /boot/grub/grub.cfg
   ```
   After running the above commands, the Manjaro GRUB menu will appear. Select Manjaro to enter the Manjaro OS.
5. Once inside the Manjaro OS, open the terminal emulator and type:
   ```bash
   sudo grub-install /dev/sdb
   sudo update-grub
   ```
   Restart the laptop. Done!

**Sources:**
- [Manjaro Wiki: Restore the GRUB Bootloader](https://wiki.manjaro.org/index.php/Restore_the_GRUB_Bootloader)
- [Manjaro Forum: Using LiveCD v17.0.1 as GRUB to Boot OS with Broken Bootloader](https://forum.manjaro.org/t/using-livecd-v17-0-1-as-grub-to-boot-os-with-broken-bootloader/24916)