# Contributing

Thank you for contributing to Meta-Agent Skills!

## Project Skills

These skills are used to maintain this repository itself.

<!-- PROJECT_SKILLS_START -->

| Name             | Description                                                                                | Link                                                                                 |
| :--------------- | :----------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------- |
| lint-fix         | Iteratively run linters, apply auto-fixes, and resolve remaining issues using Trunk.       | [.claude/skills/lint-fix/SKILL.md](.claude/skills/lint-fix/SKILL.md)                 |
| mend-agent-rules | Synchronize CLAUDE.md and AGENTS.md with available agents and skills.                      | [.claude/skills/mend-agent-rules/SKILL.md](.claude/skills/mend-agent-rules/SKILL.md) |
| mend-docs        | Maintain and synchronize documentation files with the actual codebase (agents and skills). | [.claude/skills/mend-docs/SKILL.md](.claude/skills/mend-docs/SKILL.md)               |

<!-- PROJECT_SKILLS_END -->

## For Framework Extenders

This repository is designed to be a **Template Repository**. You can fork or use this template to build your own specialized organization-wide or project-specific Agent Skills and Subagents.

### Customizing the Bootstrap Logic

If you want to create a different set of standard skills (e.g., specific to a proprietary framework), follow these steps:

1.  **Fork this Repository**: Use the "Use this template" button on GitHub.
2.  **Modify Templates**: Update or replace the files in `skills/meta-agent-skills/assets/templates/` with your own skill and agent definitions.
3.  **Update the Meta-Skill**: Edit `skills/meta-agent-skills/SKILL.md` to change how the Agent detects your specific stack and which templates it chooses to instantiate.
4.  **Standardize Your Org**: Point your organization's AI agents to your fork to ensure all your repositories are bootstrapped with your custom standards.

### Following the Specification

All skills created within this framework should follow the [Agent Skills Specification](https://agentskills.io/specification). This ensures compatibility across different AI environments (Claude Code, Cursor, etc.).

Key principles to maintain:

- **Lightweight**: Minimize external scripts; prefer instruction-based logic.
- **Progressive Disclosure**: Keep `SKILL.md` focused and use `references/` for deep-dive documentation.
- **Portability**: Avoid hardcoding paths; use detection logic to find tools and configuration files.
