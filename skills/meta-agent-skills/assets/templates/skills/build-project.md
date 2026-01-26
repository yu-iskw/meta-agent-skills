---
name: build-project
description: Compile or build the project and check for compilation errors.
---

# Build Project

## Purpose

This skill compiles or builds the project (e.g., App layer) to ensure there are no syntax or build-time errors. Note: For building container images, use the `build-container-image` skill.

## Commands

| Order       | Component       | Path         | Layer       | Command         | Description       |
| :---------- | :-------------- | :----------- | :---------- | :-------------- | :---------------- |
| {{ order }} | {{ component }} | `{{ path }}` | {{ layer }} | `{{ command }}` | {{ description }} |

## Guidance

{{ guidance }}

## Instructions

1.  **Execute Build**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Path**.
3.  **Check Output**: Verify that each build step completed successfully.
