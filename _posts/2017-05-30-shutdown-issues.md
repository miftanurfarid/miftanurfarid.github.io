---
layout: post
title: Fixing Slow Shutdown Issues on Ubuntu 16.04
date: 2017-05-30 15:06:00
description: This post outlines a solution for speeding up the shutdown process on Ubuntu 16.04 by disabling the cups-browsed service, which can cause delays during shutdown.
tags: linux ubuntu
categories: linux ubuntu
---

### Solution for Slow Shutdown on Ubuntu 16.04

Recently, my laptop running Ubuntu 16.04 has been experiencing a problem where the shutdown process takes an unusually long time.

During the shutdown process, if you press the escape key, it will display the processes that are causing the delay. In my case, it was:

```
Stopping thermal daemon services
```

The solution is to stop this service through the terminal. The service responsible for the thermal daemon is `cups-browsed`, so you can disable it with the following command:

```bash
sudo systemctl disable cups-browsed.service
```