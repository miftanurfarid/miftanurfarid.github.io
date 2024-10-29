---
layout: post
title: Fixing Git File Mode Changes from 100644 to 100755
date: 2021-09-18 08:06:00
description: Learn how to resolve issues with unexpected file mode changes in Git that can disrupt your version control workflow.
tags: git
categories: git
---

When working with Git, you may encounter issues where file mode changes unexpectedly occur, specifically changing from `100644` (regular file) to `100755` (executable file). This can be particularly frustrating, especially if these changes are not intended and lead to unnecessary modifications in your commits. 

### Understanding File Modes in Git

In Git, file modes are used to determine the type and permissions of files in the repository:

- **100644**: This mode indicates a regular file that is not executable.
- **100755**: This mode indicates a regular file that is executable.

When files change from `100644` to `100755`, it usually means that the executable bit has been set on the file. This can happen due to various reasons, such as:

- Running a script or program that modifies file permissions.
- Cloning a repository from a different operating system where file permissions are handled differently.
- Accidental changes made to file permissions locally.

### Fixing the Mode Change

To fix this mode change issue and prevent Git from tracking these modifications, you can configure Git to ignore changes in file modes by following these steps:

1. **Disable File Mode Tracking**:
   Run the following command in your terminal:

   ```bash
   git config core.filemode false
   ```

   This command tells Git to ignore changes in the executable bit of files, preventing it from recognizing changes between `100644` and `100755`. After executing this command, Git will no longer report changes to the executable bit in your working directory.

2. **Verify the Change**:
   To ensure that the configuration has been applied correctly, you can check the current Git configuration by running:

   ```bash
   git config --get core.filemode
   ```

   The output should be `false`, indicating that file mode changes are now ignored.

### Additional Considerations

- **Impact on Team Workflow**: When collaborating with others, be cautious when changing Git configurations, as it may affect how others see file changes. Make sure to communicate any changes in configuration that may impact the team.

- **Reverting File Permissions**: If you need to revert the file permissions to the desired mode, you can manually change the file mode using the `chmod` command:

   ```bash
   chmod 644 yourfile
   ```

   This command sets the file back to `100644`, ensuring it is no longer marked as executable.

- **Checking for Other Issues**: If you frequently encounter file mode changes, it may be worth investigating your development environment. Different operating systems and file systems can handle permissions differently, which may lead to these kinds of issues. 

### Conclusion

By disabling Git's tracking of file modes, you can avoid unnecessary changes in your commits and maintain a cleaner history. Understanding file modes and how Git handles them is essential for effective version control, especially in collaborative environments. If you continue to experience issues or have specific cases where file modes affect your workflow, consider reaching out to your team or the Git community for further assistance.
