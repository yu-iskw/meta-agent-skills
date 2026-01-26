---
name: lint-fix
description: Iteratively run linters and type checkers, apply auto-fixes, and resolve remaining issues.
---

# Lint Fix

## Purpose

This skill runs the configured linters and type checkers for this codebase and automatically applies fixes where possible. It ensures code quality and consistency.

## Instructions

1.  **Run Linter with Fix**: Execute the following command to lint and fix issues.

    ```bash
    {{ lint_fix_command }}
    ```

2.  **Run Type Checker**: Execute the following command to check for type errors.

    ```bash
    {{ type_check_command }}
    ```

3.  **Verify**: Check if any issues remain. If issues persist, attempt to fix them manually or report them.
