---
layout: post
title: Resolving TensorFlow Installation Issues Cannot Uninstall wrapt
date: 2021-09-15 15:06:00
description: Learn how to overcome installation conflicts when TensorFlow fails to uninstall the wrapt package.
tags: linux tensorflow wrapt python
categories: python
---

When trying to install TensorFlow, you might encounter an error message stating that it cannot uninstall the package `wrapt`. This issue arises due to conflicts between the installed version of `wrapt` and the version required by TensorFlow. Fortunately, you can resolve this problem with a couple of simple commands.

### Why the Error Occurs

The `wrapt` package is a Python library that TensorFlow depends on for functionality, especially in relation to decorators and function wrapping. When TensorFlow is installed or upgraded, it requires a specific version of `wrapt`. If an incompatible version is already installed, TensorFlow will attempt to uninstall it but may run into permissions issues or other conflicts.

### Steps to Resolve the Issue

To successfully install TensorFlow while resolving the `wrapt` conflict, follow these steps:

1. **Upgrade wrapt with Ignore Installed Flag:**
   Open your terminal and run the following command. This will force the installation of the latest version of `wrapt`, ignoring any currently installed versions.

   ```bash
   pip install wrapt --upgrade --ignore-installed
   ```

   This command tells `pip` to upgrade `wrapt` and bypass any checks that might prevent it from being updated. By doing this, you ensure that you have the version that is compatible with TensorFlow.

2. **Install TensorFlow:**
   After successfully upgrading `wrapt`, you can now proceed to install TensorFlow:

   ```bash
   pip install tensorflow
   ```

   This command will install TensorFlow along with its dependencies, including the correctly versioned `wrapt` package.
