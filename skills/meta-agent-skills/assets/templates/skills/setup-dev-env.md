---
name: setup-dev-env
description: Set up the local development environment (dependencies, hooks, configuration).
---

# Setup Dev Env

## Purpose

This skill bootstraps the local development environment for a new developer or agent. It ensures all dependencies, hooks, and configurations are correctly installed.

## Instructions

1.  **Install Dependencies**: Execute the command to install project dependencies.

    ```bash
    {{ install_command }}
    ```

2.  **Setup Hooks**: If pre-commit hooks are configured, install them.

    ```bash
    # Example: pre-commit install
    # Check for .pre-commit-config.yaml or similar
    ```

3.  **Verify Environment**: Run a quick smoke test to ensure the environment is ready.
    ```bash
    {{ run_command }} --help # or similar verification
    ```
