---
name: mend-subagents
description: Synchronizes Subagents with available Agent Skills, suggesting bindings and removing broken links.
---

# Mend Subagents

## Purpose

This skill ensures that all Subagents have accurate references to the available Agent Skills. It manages the binding between agents and skills, ensuring they remain consistent as the ecosystem grows or changes.

## When to Use

- After creating new Agent Skills.
- After deleting or renaming skills.
- When an agent seems to lack the capabilities it needs to perform its role.

## Instructions

### 1. Index Available Skills

- Scan the platform-specific `skills/` directory and the root `skills/` directory.
- For each `SKILL.md`, extract the `name` and `description` from the YAML frontmatter.

### 2. Audit Subagents

- Iterate through each agent definition (e.g., in `.claude/agents/` or root `agents/`).
- Parse the YAML frontmatter `skills` list and the `## Capabilities` section.

### 3. Synchronize Bindings

- **Remove Dead Links**: If an agent references a skill that no longer exists, remove it from the frontmatter and the Capabilities section.
- **Update Links**: Ensure all links point to the correct relative path for the current platform.
  - **Claude Code**: `[skill-name](../skills/skill-name/SKILL.md)`
  - **Cursor**: `[skill-name](../../skills/meta-agent-skills/skill-name/SKILL.md)`
- **Capabilities Section**: Use the `<!-- SKILLS_START -->` and `<!-- SKILLS_END -->` markers to synchronize the table of skills in the agent's body.

### 4. Suggestive Mending (AI Heuristic)

- Compare the Agent's `description` with the descriptions of all available skills.
- If a skill appears relevant but is not bound to the agent:
  - **Interactive**: Suggest the binding to the user via `AskQuestion`.
  - **Proactive**: If confidence is high, add the binding and report it.

### 5. Final Report

- List all agents updated.
- List all new bindings suggested or added.
- Highlight any broken links that were removed.
