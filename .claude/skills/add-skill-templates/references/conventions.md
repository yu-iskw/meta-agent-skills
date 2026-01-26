# Meta-Agent Skill Template Conventions

This document outlines the conventions for creating skill templates that the `meta-agent-skills` framework can instantiate.

## Placeholders

The following placeholders are used in the **Commands** table and are populated by the Meta-Agent during instantiation:

- `{{ order }}`: The sequential order of execution (starting from 1).
- `{{ component }}`: The name of the sub-project or component (e.g., "Frontend", "Backend", "Auth Service").
- `{{ path }}`: The relative path from the workspace root to the component's directory.
- `{{ layer }}`: The logical layer the command belongs to. Common values:
  - `App`: Application-level commands (build, lint, test).
  - `Docker`: Containerization commands (docker build).
  - `Infra`: Infrastructure/deployment commands (terraform, k8s).
- `{{ command }}`: The actual shell command to execute.
- `{{ description }}`: A brief description of what the command does.

## Frontmatter

- `name`: The machine-friendly name of the skill (used for directory naming).
- `description`: A short summary of the skill's purpose.

## Directory Structure

Templates should be placed in `skills/meta-agent-skills/assets/templates/skills/`.
The filename should be `<skill-name>.md`.
