# Codex

- [Agent Skills | Codex](https://developers.openai.com/codex/skills)

## Agent Skills in Codex

Skills package instructions, resources, and optional scripts so Codex can follow a workflow reliably.

### Invocation Methods

1.  **Explicit Invocation**: Include skills in prompt, use `/skills` slash command, or type `$` to mention a skill.
2.  **Implicit Invocation**: Codex activates a skill when the task matches the skill's description.

### Skill Locations (Precedence High to Low)

| Scope    | Location                   | Suggested Use                                |
| :------- | :------------------------- | :------------------------------------------- |
| `REPO`   | `$CWD/.codex/skills`       | Skills relevant to current working folder.   |
| `REPO`   | `$CWD/../.codex/skills`    | Skills relevant to parent folder (monorepo). |
| `REPO`   | `$REPO_ROOT/.codex/skills` | Root repo skills.                            |
| `USER`   | `$CODEX_HOME/skills`       | Personal user skills.                        |
| `ADMIN`  | `/etc/codex/skills`        | System-wide admin skills.                    |
| `SYSTEM` | Bundled with Codex         | Built-in skills.                             |

### Creating & Installing Skills

- **Create**: Use the built-in `$skill-creator` skill to bootstrap new skills.
- **Install**: Use the `$skill-installer` skill to download skills from GitHub (e.g., `openai/skills`).

### Experimental Skills

- `$create-plan`: Research and create a plan for complex problems.
- `$skill-installer`: Install external skills.
