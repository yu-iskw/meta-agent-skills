---
name: security-scan
description: Scan the codebase for vulnerabilities and secrets.
---

# Security Scan

## Purpose

This skill scans the repository for security vulnerabilities (using `osv-scanner`, `trivy`, or similar) and accidentally committed secrets.

## Commands

| Project            | Working Directory | Scanner Type  | Command                       |
| :----------------- | :---------------- | :------------ | :---------------------------- |
| {{ project_name }} | `{{ cwd }}`       | Vulnerability | `{{ security_scan_command }}` |
| {{ project_name }} | `{{ cwd }}`       | Secret        | `{{ secret_scan_command }}`   |

## Instructions

1.  **Run Scanners**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Working Directory**.
3.  **Report**: List any findings. Do NOT print the actual secrets in the output.
    - _Note: If `osv-scanner` or `trivy` are not installed, suggest installation or use available alternatives._
