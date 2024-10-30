---
layout: post
title: Using Axel to Download Password-Protected Files on Linux
date: 2024-01-24 09:06:00
description: This guide explains how to use Axel in the terminal to download files that require a username and password, including handling special characters in the password.
tags: axel linux password
categories: linux software
---

One way to download files on Linux through the terminal is by using Axel. The problem arises when the file you want to download requires a username and password. Here's how to do it:

1. Use the following command:
   ```
   axel -a -n 2 https://username:password@url_file_to_download
   ```

If the password contains special characters, enclose the password in quotes, as shown in the example below:
   ```
   axel -a -n 2 https://username:'p@ssw0rdun!qu3'@url_file_to_download
   ```

Source: [Stack Overflow](https://stackoverflow.com/questions/16822086/download-files-with-user-name-and-password-using-axel-downloader-not-accepting-s)
