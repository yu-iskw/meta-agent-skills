---
name: mend-agent-skills
description: Verifies and updates the commands within existing Agent Skills to ensure they match the current codebase state.
---

# Mend Agent Skills

## Purpose

This skill iterates through existing agent skills, verifies that their embedded commands (e.g., `make lint`, `npm test`) are still valid in the current codebase, and updates them if they are broken or outdated.

## When to Use

- When the `Makefile` or task runner configuration (e.g., `package.json`, `pyproject.toml`) has changed.
- When an agent reports that a command in a skill failed to execute.
- As a periodic health check to prevent "bit rot" in the agentic layer.

## Instructions

### 1. Identify Target Platform

- Check for existing configuration directories:
  - `.claude/` -> **Claude Code**
  - `.cursor/` -> **Cursor**
  - `.gemini/` -> **Gemini CLI**
  - `.codex/` -> **Codex**
- If multiple or none are found, or if you are unsure, use `AskQuestion` to ask the user which platform to prioritize.

### 2. Audit Skills

- Iterate through each `SKILL.md` file in the platform's skills directory (e.g., `.claude/skills/`).
- Identify commands defined in tables or instruction blocks. Look for keywords like `Command`, `Step`, or code blocks containing shell commands.

### 3. Verify and Mend Commands

- For each extracted command:
  - Determine its intended working directory.
  - **Verify**: Check if the command/target is still valid.
    - If it's a `make` command, check the `Makefile`.
    - If it's an `npm`/`pnpm`/`yarn` command, check `package.json`.
    - If it's a language-specific tool (e.g., `pytest`, `ruff`), verify the tool is configured.
  - **Mend**:
    - If the command is invalid, search for a replacement (e.g., if `make test` became `make unit-test`).
    - If a replacement is found, update the `SKILL.md` file using `StrReplace`.
    - If no replacement is found, mark the skill as "Broken" and report it.

### 4. Final Report

- Summarize:
  - Total skills audited.
  - Commands successfully mended.
  - Skills requiring manual intervention (no replacement found).
