# Agent Skills Standard

- [Agent Skills Home](https://agentskills.io/home)
- [What are Skills?](https://agentskills.io/what-are-skills)
- [Skill Specification](https://agentskills.io/specification)
- [Integrate Skills](https://agentskills.io/integrate-skills)

## What are Skills?

Agent Skills are a lightweight, open format for extending AI agent capabilities with specialized knowledge and workflows. At its core, a skill is a folder containing a `SKILL.md` file with metadata and instructions.

### Directory Structure

```
skill-name/
├── SKILL.md      # Required: instructions + metadata
├── scripts/      # Optional: executable code
├── references/   # Optional: documentation
└── assets/       # Optional: templates, resources
```

### The SKILL.md File

Every skill starts with a `SKILL.md` file containing YAML frontmatter and Markdown instructions.

**Frontmatter Example:**

```yaml
---
name: pdf-processing
description: Extract text and tables from PDF files, fill forms, merge documents.
---
```

## Specification

### Frontmatter Fields

| Field           | Required | Constraints                                     | Description                                                |
| :-------------- | :------- | :---------------------------------------------- | :--------------------------------------------------------- |
| `name`          | Yes      | Max 64 chars, lowercase alphanumeric & hyphens. | Unique identifier for the skill.                           |
| `description`   | Yes      | Max 1024 chars.                                 | Describes what the skill does and when to use it.          |
| `license`       | No       | -                                               | License name or reference to a bundled file.               |
| `compatibility` | No       | Max 500 chars.                                  | Environment requirements (product, packages, etc.).        |
| `metadata`      | No       | -                                               | Arbitrary key-value mapping.                               |
| `allowed-tools` | No       | -                                               | Space-delimited list of pre-approved tools (Experimental). |

### Optional Directories

- **`scripts/`**: Contains executable code (Python, Bash, JS, etc.). Scripts should be self-contained or document dependencies.
- **`references/`**: Additional documentation (e.g., `REFERENCE.md`, `FORMS.md`) loaded on demand.
- **`assets/`**: Static resources like templates, images, and data files.

### Progressive Disclosure

Skills are designed for efficient context usage:

1.  **Metadata** (~100 tokens): `name` and `description` loaded at startup.
2.  **Instructions** (< 5000 tokens): Full `SKILL.md` body loaded upon activation.
3.  **Resources**: Files in `scripts/`, `references/`, etc., loaded only when required.

## Integrate Skills

A skills-compatible agent needs to discover, match, and activate skills.

### Discovery & Loading

- **Discovery**: Scan configured directories for folders containing `SKILL.md`.
- **Loading Metadata**: Parse only the frontmatter at startup to keep context usage low.

### Context Injection

Include skill metadata in the system prompt. Example XML format for Claude:

```xml
<available_skills>
  <skill>
    <name>pdf-processing</name>
    <description>Extracts text and tables from PDF files...</description>
    <location>/path/to/skills/pdf-processing/SKILL.md</location>
  </skill>
</available_skills>
```
