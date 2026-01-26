---
name: update-deps
description: Update project dependencies to their latest compatible versions.
---

# Update Dependencies

## Purpose

This skill updates the project's dependencies to ensure the codebase is using the latest features and security patches.

## Instructions

1.  **Update Dependencies**: Run the package manager's update command.

    ```bash
    {{ update_deps_command }}
    ```

2.  **Verify**: Check that the lock file has been updated and no breaking changes were introduced (run tests if possible).
