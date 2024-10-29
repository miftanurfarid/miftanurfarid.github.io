---
layout: post
title: Using Personal Access Tokens on GitHub
date: 2021-08-16 15:06:00
description: Learn how to replace password authentication with personal access tokens for pushing changes to your GitHub repositories.
tags: linux github
categories: linux
---

When I attempted to push to one of my repositories on GitHub, I encountered the error message, **"Support for password authentication was removed. Please use a personal access token instead."** After researching the issue, I discovered that GitHub no longer supports password authentication and only supports personal access tokens.

How do you use a personal access token? I found the steps on Stack Overflow (link provided below).

1. Go to your GitHub account page and select:
   - **Settings**
   - **Developer Settings**
   - **Personal Access Token**
   - **Generate New Token** (then enter your password)
   - Check the boxes for the permissions you want on the form displayed on that page.
   - Click **Generate Token** and copy the token. It will look something like this: `ghp_sFhFsSHhTzMDreGRLjkdhbtzuzgthdvfsrta`. Note that this token is only displayed once, so make sure to save it.
2. Next, open your repository directory and type:
   ```
   git remote set-url origin https://token@github.com/username/repo.git
   ```
   where `token` is your personal access token, `username` is your GitHub username, and `repo` is the name of your repository.
3. Done. You can now push your repository to GitHub without password authentication.

Source: [Stack Overflow](https://stackoverflow.com/questions/68775869/support-for-password-authentication-was-removed-please-use-a-personal-access-to)
