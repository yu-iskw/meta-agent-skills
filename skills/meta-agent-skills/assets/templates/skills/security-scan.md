---
name: security-scan
description: Scan the codebase for vulnerabilities and secrets.
---

# Security Scan

## Purpose

This skill scans the repository for security vulnerabilities (using `osv-scanner`, `trivy`, or similar) and accidentally committed secrets.

## Commands

| Order       | Component       | Path         | Layer       | Command         | Description       |
| :---------- | :-------------- | :----------- | :---------- | :-------------- | :---------------- |
| {{ order }} | {{ component }} | `{{ path }}` | {{ layer }} | `{{ command }}` | {{ description }} |

## Guidance

{{ guidance }}

## Instructions

1.  **Run Scanners**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Path**.
3.  **Report**: List any findings. Do NOT print the actual secrets in the output.
    - _Note: If `osv-scanner` or `trivy` are not installed, suggest installation or use available alternatives._
