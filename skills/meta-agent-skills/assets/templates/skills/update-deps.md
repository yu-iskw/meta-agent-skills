---
name: update-deps
description: Update project dependencies to their latest compatible versions.
---

# Update Dependencies

## Purpose

This skill updates the project's dependencies to ensure the codebase is using the latest features and security patches.

## Commands

| Order       | Component       | Path         | Layer       | Command         | Description       |
| :---------- | :-------------- | :----------- | :---------- | :-------------- | :---------------- |
| {{ order }} | {{ component }} | `{{ path }}` | {{ layer }} | `{{ command }}` | {{ description }} |

## Guidance

{{ guidance }}

## Instructions

1.  **Update Dependencies**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Path**.
3.  **Verify**: Check that the lock file has been updated for each project and ensure no breaking changes were introduced (run tests if possible).
