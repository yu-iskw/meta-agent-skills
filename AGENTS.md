# AGENTS.md

This file provides guidance to AI coding agents (Claude Code, Cursor, Copilot, etc.) when working with code in this repository.

## Available Skills

<!-- AVAILABLE_SKILLS_START -->

| Name             | Description                                                                                | Link                                                                                 |
| :--------------- | :----------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------- |
| lint-fix         | Iteratively run linters, apply auto-fixes, and resolve remaining issues using Trunk.       | [.claude/skills/lint-fix/SKILL.md](.claude/skills/lint-fix/SKILL.md)                 |
| mend-agent-rules | Synchronize CLAUDE.md and AGENTS.md with available agents and skills.                      | [.claude/skills/mend-agent-rules/SKILL.md](.claude/skills/mend-agent-rules/SKILL.md) |
| mend-docs        | Maintain and synchronize documentation files with the actual codebase (agents and skills). | [.claude/skills/mend-docs/SKILL.md](.claude/skills/mend-docs/SKILL.md)               |
| meta-agent-skills | Proactively analyzes the codebase and generates specialized subagents and skills to standardize agentic workflows. | [skills/meta-agent-skills/SKILL.md](skills/meta-agent-skills/SKILL.md)               |

<!-- AVAILABLE_SKILLS_END -->

## Available Agents

<!-- AVAILABLE_AGENTS_START -->

| Name             | Description                                                                                                                                  | Link                                                                     |
| :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------- |
| maintainer-agent | Expert codebase maintainer. Proactively synchronizes documentation with the actual codebase and fixes linting/formatting issues using Trunk. | [.claude/agents/maintainer-agent.md](.claude/agents/maintainer-agent.md) |

<!-- AVAILABLE_AGENTS_END -->

<!-- FRAMEWORK_DOCS_START -->

## Agent Skills

This repository uses the [Agent Skills](https://agentskills.io) framework to extend AI agent capabilities with specialized knowledge and workflows.

### What are Agent Skills?

Agent Skills are a lightweight, open format for defining specialized tasks that an AI agent can perform. Each skill is contained in a directory within the `skills/` folder and includes a `SKILL.md` file with metadata and instructions.

### Directory Structure

Skills are organized as follows:

```
skills/
  <skill-name>/
    SKILL.md       # Required: instructions + metadata
    scripts/       # Optional: executable code
    references/    # Optional: documentation
    assets/        # Optional: templates, resources
```

### Guidelines for Agents

- **Read Skills Proactively**: When you identify a relevant skill, read and follow it IMMEDIATELY as your first action.
- **Progressive Disclosure**: Only read the full `SKILL.md` or referenced files when the skill is actually needed to save context.
- **Follow the Specification**: Ensure any new skills you create follow the [Agent Skills Specification](https://agentskills.io/specification).
- **Python Scripts**:
  - **Minimize Usage**: Avoid implementing Python scripts as much as possible. Prefer implementing logic directly in `SKILL.md` instructions.
  - **Dependency Management**: If a Python script is necessary, use `uv`'s script dependency management (PEP 723) to declare dependencies inline. Refer to [uv documentation](https://docs.astral.sh/uv/guides/scripts/#running-a-script-with-dependencies) for details.

<!-- FRAMEWORK_DOCS_END -->
