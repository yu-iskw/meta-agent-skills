# Gemini CLI

- [Agent Skills | Gemini CLI](https://geminicli.com/docs/cli/skills/)

## Agent Skills in Gemini CLI

Gemini CLI uses Agent Skills to represent **on-demand expertise**. Unlike `GEMINI.md` context files, skills are only loaded when explicitly activated by the model.

### Skill Discovery Tiers

Gemini CLI discovers skills in the following order of precedence (higher overrides lower):

1.  **Workspace Skills** (`.gemini/skills/`): Project-specific, version-controlled.
2.  **User Skills** (`~/.gemini/skills/`): Personal, global.
3.  **Extension Skills**: Bundled within installed extensions.

### Managing Skills

**Interactive Session (`/skills` command):**

- `/skills list`: Show all discovered skills.
- `/skills disable <name>`: Disable a skill (defaults to user scope).
- `/skills enable <name>`: Enable a skill.
- `/skills reload`: Refresh skill list.

**Terminal (`gemini skills` command):**

- `gemini skills list`
- `gemini skills install <url/path>`
- `gemini skills uninstall <name>`

### Creating a Skill

A skill is a directory with a `SKILL.md` file.

**Structure:**

```
my-skill/
├── SKILL.md      # Instructions and metadata
├── scripts/      # Executable scripts (bash, python, node)
├── references/   # Static documentation
└── assets/       # Templates/binary resources
```

**SKILL.md Example:**

```yaml
---
name: code-reviewer
description: Expertise in reviewing code for style, security, and performance.
---
# Code Reviewer
You are an expert code reviewer...
```

### Security & Privacy

1.  **Discovery**: Metadata injected into system prompt.
2.  **Activation**: Model calls `activate_skill` tool when relevant.
3.  **Consent**: User sees a confirmation prompt (Name, Purpose, Path).
4.  **Injection**: Upon approval, instructions and directory access are granted.
