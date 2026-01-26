---
name: security-scan
description: Scan the codebase for vulnerabilities and secrets.
---

# Security Scan

## Purpose

This skill scans the repository for security vulnerabilities (using `osv-scanner`, `trivy`, or similar) and accidentally committed secrets.

## Instructions

1.  **Run Vulnerability Scanner**: Execute the configured security scanner.

    ```bash
    {{ security_scan_command }}
    ```

    _Note: If `osv-scanner` or `trivy` are not installed, suggest installation or use available alternatives._

2.  **Run Secret Scanner**: Execute the secret scanning tool.

    ```bash
    {{ secret_scan_command }}
    ```

    _If no specific tool is configured, use `trivy fs . --scanners secret` or `grep` patterns for common keys._

3.  **Report**: List any findings. Do NOT print the actual secrets in the output.
