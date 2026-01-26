---
name: lint-fix
description: Iteratively run linters and type checkers, apply auto-fixes, and resolve remaining issues.
---

# Lint Fix

## Purpose

This skill runs the configured linters and type checkers for this codebase and automatically applies fixes where possible. It ensures code quality and consistency.

## Commands

| Order       | Component       | Path         | Layer       | Command         | Description       |
| :---------- | :-------------- | :----------- | :---------- | :-------------- | :---------------- |
| {{ order }} | {{ component }} | `{{ path }}` | {{ layer }} | `{{ command }}` | {{ description }} |

## Guidance

{{ guidance }}

## Instructions

1.  **Execute Linting & Type Checking**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Path**.
3.  **Verify**: Check if any issues remain after running the fix commands. If issues persist, attempt to fix them manually or report them.
