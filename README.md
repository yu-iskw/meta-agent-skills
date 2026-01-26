# Meta-Agent Skills

This repository provides a framework and set of specialized skills for AI coding agents to standardize and automate software engineering tasks.

## Reusable Skills

<!-- REUSABLE_SKILLS_START -->

| Name              | Description                                                                                                        | Link                                                                   |
| :---------------- | :----------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------- |
| meta-agent-skills | Proactively analyzes the codebase and generates specialized subagents and skills to standardize agentic workflows. | [skills/meta-agent-skills/SKILL.md](skills/meta-agent-skills/SKILL.md) |

<!-- REUSABLE_SKILLS_END -->

## For Users

The `meta-agent-skills` is a "Meta-Skill" designed to bootstrap an "Agentic Makefile" environment for any repository. It proactively analyzes your codebase to detect the technology stack (Python, Node, Go, etc.) and generates specialized, ready-to-use Agent Skills and Subagents.

### Usage

You can invoke this skill by asking your Agent to set up or maintain the environment.

**Triggers:**

- "Setup skills for this repo"
- "Install standard agents"
- "Maintain agent rules"
- "Initialize agent environment"

### Output

The skill generates files in your agent's configuration directory (defaulting to `.claude/skills/meta-agent-skills/` and `.claude/agents/meta-agent-skills/`).

**Generated Skills include:** `lint-fix`, `build-project`, `update-deps`, `test-unit`, `security-scan`, `setup-dev-env`, and `docs-gen-readme`.

## For Developers

This section is for contributors who want to extend or modify the `meta-agent-skills` itself.

### Architecture

This skill uses a **Prompt-Driven Generation** approach. It relies on the Agent's semantic understanding rather than rigid scripts:

1.  **Instruction**: `SKILL.md` instructs the Agent to analyze the codebase.
2.  **Templates**: Markdown templates in `assets/templates/` provide the structure.
3.  **Generation**: The Agent reads the templates, infers the correct commands for the active repo, and writes the final files.

### Directory Structure

```text
meta-agent-skills/
├── SKILL.md                 # The brain: instructions for the Agent
└── assets/
    └── templates/
        ├── skills/          # Templates for atomic skills
        └── agents/          # Templates for subagents
```

### Adding New Skills

To add a new standard skill:

1.  Add a new template to `assets/templates/skills/` using `{{ placeholders }}` for dynamic commands.
2.  Update `SKILL.md` to make the Agent aware of the new template.
