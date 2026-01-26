---
name: meta-agent-skills
description: Proactively analyzes the codebase and generates specialized subagents and skills to standardize agentic workflows.
---

# Meta-Agent Skills

## Purpose

This skill serves as a "Meta-Skill" that bootstraps the Agentic Makefile environment. It empowers the Agent to analyze the repository's technology stack (e.g., Python/Poetry, Node/Next.js, Go), detect the AI environment (Claude Code, Cursor, Gemini), and generate specialized, ready-to-use Agent Skills and Subagents.

## When to Use

- When initializing a new repository for AI agent use.
- When the technology stack changes (e.g., switching from Pip to Poetry).
- When you want to reset or update the standard agent capabilities.
- When asked to "setup skills", "maintain agent rules", or "install standard agents".

## Instructions

1.  **Detect AI Environment**:
    - Check for `.claude/`, `.cursor/`, or `.gemini/` directories.
    - **Default**: If ambiguous or multiple exist, prioritize `.claude/skills/meta-agent-skills` (and `.claude/agents/meta-agent-skills`) as the shared standard for the organization.

2.  **Analyze Codebase**:
    - **Review Documentation**: Read `README.md`, `CONTRIBUTING.md`, `DEVELOPMENT.md`, or other relevant documentation to understand the project structure, development workflows, and any specific commands recommended for the codebase.
    - Identify the **Tech Stack**: Look for `pyproject.toml`, `package.json`, `go.mod`, etc., to determine how to run linters, builds, and updates.
    - Identify **Test Types**: Look for `tests/unit`, `tests/integration`, `cypress`, `playwright`, etc., to distinguish between Unit, Integration, and E2E tests.
    - Identify **Security Tools**: Check if `trivy`, `osv-scanner`, or other security tools are configured or available.
    - Identify **Setup Scripts**: Look for `pre-commit` config, `Makefile`, or setup scripts to include in `setup-dev-env`.

3.  **Verify Commands**:
    - Before generating skills, proactively verify that the detected commands work in the current environment.
    - Run `command --help`, `command --version`, or similar check for each primary command (e.g., `poetry --version`, `npm run --help`).
    - If a command fails or is missing, investigate alternatives or suggest installation in the final report.

4.  **Generate Skills & Agents**:
    - Read the templates located in `assets/templates/skills/` and `assets/templates/agents/`.
    - **Instantiate** each template by filling in the detected and verified commands (e.g., replace `{{ lint_fix_command }}` with `npm run lint:fix`).
    - **Write** the generated files to the target directory.
      - **Skills**: Each skill MUST be in its own folder nested under `meta-agent-skills/`, with the file itself named `SKILL.md` (e.g., `.claude/skills/meta-agent-skills/lint-fix/SKILL.md`).
      - **Agents**: Each agent MUST be in its own folder named `meta-agent-skills/` (e.g., `.claude/agents/meta-agent-skills/codebase-maintainer-agent.md`).
    - _Note_: For `test-*` skills, only generate the ones that match the detected test types.

5.  **Report**:
    - List the skills and agents created.
    - Mention which stack and test types were detected.
    - Report the results of command verification (which commands are confirmed and which might need setup).

## Capabilities Generated

- **Core Skills**: `lint-fix` (includes type checking), `build-project`, `update-deps`, `docs-gen-readme`, `security-scan`, `setup-dev-env`.
- **Test Skills**: `test-unit`, `test-integration`, `test-e2e`.
- **Subagents**: `codebase-maintainer-agent`, `security-auditor-agent`, `qa-engineer-agent`.

## References

- [Agent Skills Standard](references/agent-skills.md)
- [Claude Code](references/claude-code.md)
- [Cursor](references/cursor.md)
- [Gemini CLI](references/gemini-cli.md)
- [Codex](references/codex.md)
