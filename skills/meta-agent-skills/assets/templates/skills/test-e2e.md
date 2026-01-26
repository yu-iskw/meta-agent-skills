---
name: test-e2e
description: Run end-to-end (E2E) tests for the project.
---

# Test E2E

## Purpose

This skill executes end-to-end tests to verify the system's behavior from a user's perspective.

## Commands

| Project            | Working Directory | Command                  |
| :----------------- | :---------------- | :----------------------- |
| {{ project_name }} | `{{ cwd }}`       | `{{ test_e2e_command }}` |

## Instructions

1.  **Run E2E Tests**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Working Directory**.
3.  **Analyze Results**:
    - If all tests pass, proceed.
    - If any tests fail, analyze the failure and report it.
