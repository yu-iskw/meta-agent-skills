---
name: test-unit
description: Run unit tests for the project.
---

# Test Unit

## Purpose

This skill executes unit tests to verify the correctness of individual components in the codebase.

## Commands

| Project            | Working Directory | Command                   |
| :----------------- | :---------------- | :------------------------ |
| {{ project_name }} | `{{ cwd }}`       | `{{ test_unit_command }}` |

## Instructions

1.  **Run Unit Tests**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Working Directory**.
3.  **Analyze Results**:
    - If all tests pass, proceed.
    - If any tests fail, analyze the failure and report it.
