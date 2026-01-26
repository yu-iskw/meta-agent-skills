---
name: docs-gen-readme
description: Generate or update the project's README.md.
---

# Docs Gen README

## Purpose

This skill updates the `README.md` file to reflect the current state of the project, including installation instructions, usage, and architecture.

## Instructions

1.  **Analyze Project**: Read the codebase to understand the current features and structure.
2.  **Update README**: Edit `README.md` with the following sections (if missing or outdated):
    - **Project Name & Description**
    - **Installation**: `{{ install_command }}`
    - **Usage**: `{{ run_command }}`
    - **Testing**: `{{ test_command }}`
