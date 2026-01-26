# Claude Code

- [Extend Claude with Skills](https://code.claude.com/docs/en/skills)
- [Create Custom Subagents](https://code.claude.com/docs/en/sub-agents)

## Extend Claude with Skills

Skills extend Claude's capabilities. Create a `SKILL.md` file with instructions, and Claude adds it to its toolkit. Claude uses skills when relevant, or you can invoke one directly with `/skill-name`.

### Where Skills Live

| Location       | Path                                     | Applies to                |
| :------------- | :--------------------------------------- | :------------------------ |
| **Enterprise** | Managed settings                         | All users in organization |
| **Personal**   | `~/.claude/skills/<skill-name>/SKILL.md` | All your projects         |
| **Project**    | `.claude/skills/<skill-name>/SKILL.md`   | This project only         |
| **Plugin**     | `<plugin>/skills/<skill-name>/SKILL.md`  | Where plugin is enabled   |

### Frontmatter Reference

| Field                      | Description                                                          |
| :------------------------- | :------------------------------------------------------------------- |
| `name`                     | Display name / slash command.                                        |
| `description`              | When to use the skill.                                               |
| `disable-model-invocation` | Set to `true` to prevent automatic loading (manual invocation only). |
| `user-invocable`           | Set to `false` to hide from `/` menu.                                |
| `allowed-tools`            | Tools Claude can use without asking permission.                      |
| `model`                    | Model to use when this skill is active.                              |
| `context`                  | Set to `fork` to run in a forked subagent context.                   |
| `agent`                    | Which subagent type to use when `context: fork` is set.              |

### Advanced Patterns

- **Inject Dynamic Context**: Use `!command` syntax to run shell commands and insert output into the prompt.
- **Run in Subagent**: Add `context: fork` to run the skill in isolation.

## Create Custom Subagents

Subagents are specialized AI assistants that handle specific types of tasks in their own context window.

### Built-in Subagents

- **Explore**: Read-only, optimized for codebase search (uses Haiku).
- **Plan**: Research agent used during plan mode.
- **General-purpose**: Capable agent for complex tasks (uses main conversation settings).

### Subagent Configuration

Subagents are defined in Markdown files (e.g., `~/.claude/agents/my-agent.md`) with YAML frontmatter.

**Frontmatter Fields:**

| Field             | Description                                                          |
| :---------------- | :------------------------------------------------------------------- |
| `name`            | Unique identifier.                                                   |
| `description`     | When Claude should delegate to this subagent.                        |
| `tools`           | Allowlist of tools the subagent can use.                             |
| `disallowedTools` | Denylist of tools.                                                   |
| `model`           | `sonnet`, `opus`, `haiku`, or `inherit`.                             |
| `permissionMode`  | `default`, `acceptEdits`, `dontAsk`, `bypassPermissions`, or `plan`. |
| `skills`          | List of skills to preload into the subagent's context.               |
| `hooks`           | Lifecycle hooks (PreToolUse, PostToolUse, Stop).                     |

### Permission Modes

- **`default`**: Standard permission checking.
- **`acceptEdits`**: Auto-accept file edits.
- **`dontAsk`**: Auto-deny permission prompts.
- **`bypassPermissions`**: Skip all checks (use with caution).
- **`plan`**: Read-only exploration.
