# Cursor

- [Agent Skills in Cursor](https://cursor.com/docs/context/skills)
- [Cursor Subagents](https://cursor.com/docs/context/subagents)

## Agent Skills in Cursor

Agent Skills is an open standard for extending AI agents with specialized capabilities.

### Skill Directories

Cursor automatically loads skills from these locations:

| Location            | Scope                                     |
| :------------------ | :---------------------------------------- |
| `.cursor/skills/`   | Project-level                             |
| `.claude/skills/`   | Project-level (Claude compatibility)      |
| `.codex/skills/`    | Project-level (Codex compatibility)       |
| `~/.cursor/skills/` | User-level (global)                       |
| `~/.claude/skills/` | User-level (global, Claude compatibility) |
| `~/.codex/skills/`  | User-level (global, Codex compatibility)  |

### SKILL.md Format

Cursor supports the standard `SKILL.md` format with frontmatter.

**Key Frontmatter Fields:**

- `disable-model-invocation`: Set to `true` to disable automatic context-based invocation (making it a manual slash command).

### Migrating Rules to Skills

Cursor includes a built-in `/migrate-to-skills` skill to convert existing dynamic rules and slash commands to the Agent Skills format.

## Cursor Subagents

Subagents are specialized AI assistants that Cursor's agent can delegate tasks to. Each subagent operates in its own context window.

### Built-in Subagents

- **Explore**: Searches and analyzes codebases (uses faster model for parallel searches).
- **Bash**: Runs series of shell commands (isolates verbose output).
- **Browser**: Controls browser via MCP tools.

### Execution Modes

| Mode           | Behavior                                             | Best for                     |
| :------------- | :--------------------------------------------------- | :--------------------------- |
| **Foreground** | Blocks until completion. Returns result immediately. | Sequential tasks.            |
| **Background** | Returns immediately. Works independently.            | Long-running/parallel tasks. |

### Creating Subagents

Create a markdown file in `.cursor/agents/` (project) or `~/.cursor/agents/` (user) with YAML frontmatter and a prompt.
