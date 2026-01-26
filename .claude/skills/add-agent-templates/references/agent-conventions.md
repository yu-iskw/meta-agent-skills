# Meta-Agent Agent Template Conventions

This document outlines the conventions for creating agent templates that the `meta-agent-skills` framework can instantiate.

## Frontmatter

- `name`: The machine-friendly name of the agent (e.g., `security-auditor-agent`).
- `description`: A brief summary of the agent's role.
- `skills`: A list of skill names (matching the `name` field in skill templates) that this agent uses.

## Capabilities Section

The `## Capabilities` section MUST use the following markers for automatic skill binding:

```markdown
<!-- SKILLS_START -->

- **Skill Name**: description of how the agent uses it.
<!-- SKILLS_END -->
```

The Meta-Agent will synchronize these markers with the actual skills and their paths during instantiation.

## Directory Structure

Agent templates should be placed in `skills/meta-agent-skills/assets/templates/agents/`.
The filename should be `<agent-name>.md`.

## Instruction Style

Instructions should be clear, sequential, and focus on how the agent utilizes its assigned skills to achieve its purpose.
