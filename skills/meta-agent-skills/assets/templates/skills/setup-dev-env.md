---
name: setup-dev-env
description: Set up the local development environment (dependencies, hooks, configuration).
---

# Setup Dev Env

## Purpose

This skill bootstraps the local development environment for a new developer or agent. It ensures all dependencies, hooks, and configurations are correctly installed.

## Commands

| Project            | Working Directory | Command                 |
| :----------------- | :---------------- | :---------------------- |
| {{ project_name }} | `{{ cwd }}`       | `{{ install_command }}` |

## Instructions

1.  **Install Dependencies**: Run the commands in the **Commands** table sequentially to install project dependencies.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Working Directory**.
3.  **Setup Hooks**: If pre-commit hooks are configured, install them (e.g., `pre-commit install`).
4.  **Verify Environment**: Run a quick smoke test for each project to ensure the environment is ready.
    ```bash
    {{ verify_command }} --help # or similar verification
    ```
