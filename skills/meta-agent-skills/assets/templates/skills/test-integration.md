---
name: test-integration
description: Run integration tests for the project.
---

# Test Integration

## Purpose

This skill executes integration tests to verify that different parts of the system work together correctly.

## Commands

| Project            | Working Directory | Command                          |
| :----------------- | :---------------- | :------------------------------- |
| {{ project_name }} | `{{ cwd }}`       | `{{ test_integration_command }}` |

## Instructions

1.  **Run Integration Tests**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Working Directory**.
3.  **Analyze Results**:
    - If all tests pass, proceed.
    - If any tests fail, analyze the failure and report it.
