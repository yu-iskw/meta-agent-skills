# Meta-Agent Skills

The **Meta-Agent Skills** is a "Meta-Skill" designed to bootstrap an "Agentic Makefile" environment for any repository. It proactively analyzes your codebase to detect the technology stack (Python, Node, Go, etc.) and generates specialized, ready-to-use Agent Skills and Subagents.

---

## 👩‍💻 For Users

### Introduction

When you start working on a new repository with an AI Agent (Claude Code, Cursor, etc.), you often need to teach it how to run tests, lint code, or manage dependencies. Instead of doing this manually, `meta-agent-skills` does it for you.

It scans your project and generates a standard set of skills that work specifically for your setup.

### Usage

You can invoke this skill by asking your Agent to set up or maintain the environment.

**Triggers:**

- "Setup skills for this repo"
- "Install standard agents"
- "Maintain agent rules"
- "Initialize agent environment"

**Example Interaction:**

> **User**: "Please setup the standard skills for this Python project."
>
> **Agent**: _Analyzes pyproject.toml... Detects Poetry... Generates skills..._
> "I have created `lint-fix`, `test-unit`, and other skills in `.claude/skills/` tailored for Poetry."

### Output

The skill generates files in your agent's configuration directory (defaulting to `.claude/skills/meta-agent-skills/` and `.claude/agents/meta-agent-skills/`).

**Generated Skills**:
(Stored in `.claude/skills/meta-agent-skills/<skill-name>/SKILL.md`)

- `lint-fix`: Runs linters/formatters (e.g., `ruff`, `eslint`).
- `build-project`: Compiles the code (e.g., `go build`, `npm build`).
- `update-deps`: Updates dependencies.
- `test-unit` / `test-integration` / `test-e2e`: Runs specific test suites.
- `security-scan`: Scans for vulnerabilities and secrets.
- `setup-dev-env`: Sets up the local development environment.
- `docs-gen-readme`: Generates or updates README.md.

**Generated Subagents**:
(Stored in `.claude/agents/meta-agent-skills/`)

- `codebase-maintainer-agent`: A general-purpose maintenance loop.
- `security-auditor-agent`: Specialized in security reviews.
- `qa-engineer-agent`: Specialized in testing.

### Troubleshooting

- **Ambiguous Stack**: If your project uses multiple package managers (e.g., both `package.json` and `requirements.txt`), the Agent might ask for clarification or pick one. You can manually edit the generated skills in `.claude/skills/` if needed.
- **Missing Tools**: If generated skills fail (e.g., `trivy: command not found`), you may need to install the underlying tools on your system or update the skill to use an alternative.

---

## 🛠️ For Developers

This section is for contributors who want to extend or modify the `meta-agent-skills` itself.

### Architecture

This skill uses a **Prompt-Driven Generation** approach. Unlike traditional scripts that use rigid logic (if/else) to generate code, this skill relies on the Agent's semantic understanding.

1.  **Instruction**: `SKILL.md` instructs the Agent to analyze the codebase.
2.  **Templates**: Markdown templates in `assets/templates/` provide the structure.
3.  **Generation**: The Agent reads the templates, infers the correct commands for the active repo, and writes the final files.

There are **no Python scripts** driving the logic. The "brain" is the Agent executing the `SKILL.md` instructions.

### Directory Structure

```text
meta-agent-skills/
├── SKILL.md                 # The brain: instructions for the Agent
├── README.md                # This file
├── README.ja.md             # Japanese documentation
└── assets/
    └── templates/
        ├── skills/          # Templates for atomic skills
        │   ├── lint-fix.md
        │   └── ...
        └── agents/          # Templates for subagents
            ├── codebase-maintainer-agent.md
            └── ...
```

### Adding New Skills

To add a new standard skill (e.g., `deploy`):

1.  **Create Template**: Add `deploy.md` to `assets/templates/skills/`.
    - Use `{{ placeholders }}` for dynamic commands (e.g., `{{ deploy_command }}`).
2.  **Update Instructions**: Edit `SKILL.md` to make the Agent aware of the new template.
    - Add it to the list of templates the Agent should look at.
    - (Optional) Add specific hints if detection is complex.

### Testing

Since this is a prompt-driven skill, testing involves running it against various "fixture" repositories.

1.  Create a temporary folder simulating a tech stack (e.g., a `package.json` file).
2.  Run the Agent in that folder and invoke `meta-agent-skills`.
3.  Verify that valid Markdown files are generated in `.claude/skills/`.
