---
name: build-container-image
description: Build container images (e.g., Docker) for the project.
---

# Build Container Image

## Purpose

This skill builds container images for the project to ensure they can be packaged and deployed correctly.

## Commands

| Order       | Component       | Path         | Layer       | Command         | Description       |
| :---------- | :-------------- | :----------- | :---------- | :-------------- | :---------------- |
| {{ order }} | {{ component }} | `{{ path }}` | {{ layer }} | `{{ command }}` | {{ description }} |

## Guidance

{{ guidance }}

## Instructions

1.  **Build Container Images**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Path**.
3.  **Check Output**: Verify that each image build completed successfully.
