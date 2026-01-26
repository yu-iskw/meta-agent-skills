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
    - **Detect Sub-Projects**: Recursively search for "logical project boundaries" in sub-directories. Look for files like `package.json` (Node.js), `go.mod` (Go), `pyproject.toml` or `requirements.txt` (Python), `main.tf` or `*.tf` (Terraform), etc.
    - **Detect Multi-Layered Builds**: Search for files that indicate a layered build or deployment process, such as `Dockerfile`, `docker-compose.yml`, `Earthfile`, `Tiltfile`, `Skaffold.yaml`, or `kustomization.yaml`.
    - **Map Tech Stack per Project**: For each detected sub-project, determine its specific tech stack and how to run builds, linters, and tests within its directory.
    - **Analyze Layered Commands**: Categorize commands into logical layers (e.g., `App` for compilation, `Docker` for image building, `Infra` for deployment or local orchestration).
    - **Identify Test Types**: Look for `tests/unit`, `tests/integration`, `cypress`, `playwright`, etc., to distinguish between Unit, Integration, and E2E tests for each project.
    - **Identify Security Tools**: Check if `trivy`, `osv-scanner`, or other security tools are configured or available.
    - **Identify Setup Scripts**: Look for `pre-commit` config, `Makefile`, or setup scripts to include in `setup-dev-env`.

3.  **Verify Commands**:
    - Before generating skills, proactively verify that the detected commands work in their respective project environments.
    - Run `command --help`, `command --version`, or similar check for each primary command in the correct working directory.
    - If a command fails or is missing, investigate alternatives or suggest installation in the final report.

4.  **Generate Skills & Agents**:
    - Read the templates located in `assets/templates/skills/` and `assets/templates/agents/`.
    - **Instantiate Templates**:
      - For each skill template, populate the **Commands** table with the verified commands for all detected sub-projects.
      - **Build Separation**: Distinguish between project compilation (App layer) and container image building (Docker layer).
        - Use `build-project` template for compilation/build commands (e.g., `npm run build`, `go build`).
        - Use `build-container-image` template for containerization commands (e.g., `docker build`, `earthly --push +docker`).
      - Each row in the table MUST include the `Order`, `Component`, `Path` (relative to root), `Layer` (e.g., App, Docker), `Command`, and `Description`.
      - Ensure the **order of commands** is logical (e.g., compile app before building docker image).
    - **Check & Merge Existing Files**:
      - **Admire & Respect**: Before writing, check if the target file already exists. If it does, assume it contains valuable manual customizations or improvements.
      - **Smart Merge**:
        - Read the existing file content.
        - Merge the newly generated content (commands, paths) with the existing content.
        - **Preserve**: Keep manual additions (e.g., extra commands, custom descriptions, specific environment variables) that are not present in the standard template.
        - **Update**: Only update parts that are clearly outdated or incorrect based on the current codebase analysis (e.g., new package manager, new test directory).
        - **Do not overwrite** blindly.
      - **New Files**: If the file does not exist, write the generated content as is.
    - **Write** the final content to the target directory.
      - **Skills**: Each skill MUST be in its own folder nested under `meta-agent-skills/`, with the file itself named `SKILL.md` (e.g., `.claude/skills/meta-agent-skills/lint-fix/SKILL.md`).
      - **Agents**: Each agent MUST be in its own folder named `meta-agent-skills/` (e.g., `.claude/agents/meta-agent-skills/codebase-maintainer-agent.md`).
    - **Bind Skills to Agents**:
      - For each generated agent, identify the `skills` required from its template frontmatter.
      - Synchronize the `Capabilities` section between `<!-- SKILLS_START -->` and `<!-- SKILLS_END -->` markers.
      - Ensure each mentioned skill is linked to its respective `SKILL.md` file (e.g., `[lint-fix](../../skills/meta-agent-skills/lint-fix/SKILL.md)`).
    - _Note_: For `test-*` skills, only generate the ones that match the detected test types.

5.  **Verify & Fix Generated Output**:
    - **Audit**: Read a sample of the generated `SKILL.md` files (prioritize `lint-fix` and `build-project`).
    - **Check for Placeholders**: Ensure no unpopulated templates like `{{ command }}` remain in the generated files.
    - **Path Validation**: Verify that the `Working Directory` paths specified in the tables actually exist relative to the workspace root.
    - **Immediate Remediation**: If errors, broken links, or missing information are found, use editing tools to fix the generated files immediately.

6.  **Execute Generated Skills & Agents**:
    - **Smoke Test**: Execute a subset of the generated skills to verify their real-world functionality.
    - **Priority Skills**: Run `setup-dev-env` (if applicable), followed by `lint-fix`, `build-project`, and `build-container-image`.
    - **Verify Subagents**: If a subagent was generated, consider invoking it for a simple query (e.g., "Analyze the current state of the codebase").
    - **Error Handling**: If execution fails, analyze the output, fix the generated skill/agent, and re-run until successful.

7.  **Report**:
    - List the skills and agents created.
    - Mention which stack and test types were detected.
    - Report the results of command verification (which commands are confirmed and which might need setup).
    - Report on the **Verification & Fix** results (e.g., "Verified all generated skills; fixed 1 path error in lint-fix").
    - Report on the **Execution** results (e.g., "Successfully ran lint-fix, build-project, and build-container-image skills").

## Capabilities Generated

- **Core Skills**: `lint-fix` (includes type checking), `build-project`, `build-container-image`, `update-deps`, `docs-gen-readme`, `security-scan`, `setup-dev-env`, `add-skill-templates`, `add-agent-templates`, `mend-agent-templates`.
- **Test Skills**: `test-unit`, `test-integration`, `test-e2e`.
- **Subagents**: `codebase-maintainer-agent`, `security-auditor-agent`, `qa-engineer-agent`, `template-factory-agent`.

## References

- [Agent Skills Standard](references/agent-skills.md)
- [Claude Code](references/claude-code.md)
- [Cursor](references/cursor.md)
- [Gemini CLI](references/gemini-cli.md)
- [Codex](references/codex.md)
