---
name: build-project
description: Build the project and check for compilation errors.
---

# Build Project

## Purpose

This skill compiles or builds the project to ensure there are no syntax or build-time errors.

## Commands

| Project            | Working Directory | Command               |
| :----------------- | :---------------- | :-------------------- |
| {{ project_name }} | `{{ cwd }}`       | `{{ build_command }}` |

## Instructions

1.  **Execute Build**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Working Directory**.
3.  **Check Output**: Verify that each build step completed successfully.
