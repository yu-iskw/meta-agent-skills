---
name: docs-gen-readme
description: Generate or update the project's README.md.
---

# Docs Gen README

## Purpose

This skill updates the `README.md` file to reflect the current state of the project, including installation instructions, usage, and architecture.

## Project Context

| Order       | Component       | Path         | Layer       | Install                 | Run                 | Test                 |
| :---------- | :-------------- | :----------- | :---------- | :---------------------- | :------------------ | :------------------- |
| {{ order }} | {{ component }} | `{{ path }}` | {{ layer }} | `{{ install_command }}` | `{{ run_command }}` | `{{ test_command }}` |

## Guidance

{{ guidance }}

## Instructions

1.  **Analyze Project**: Read the codebase to understand the current features and structure.
2.  **Update README**: Edit `README.md` with the following sections (if missing or outdated), using the details from the **Project Context** table:
    - **Project Name & Description**
    - **Installation**
    - **Usage**
    - **Testing**
3.  **Multi-Project Notice**: If there are multiple projects, ensure the README clearly delineates them or points to their respective sub-directory READMEs.
