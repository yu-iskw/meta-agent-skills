---
name: { { skill_name } }
description: { { skill_description } }
---

# {{ skill_title }}

## Purpose

{{ purpose_description }}

## Commands

| Order       | Component       | Path         | Layer       | Command         | Description       |
| :---------- | :-------------- | :----------- | :---------- | :-------------- | :---------------- |
| {{ order }} | {{ component }} | `{{ path }}` | {{ layer }} | `{{ command }}` | {{ description }} |

## Guidance

{{ guidance_text }}

## Instructions

1.  **Execute {{ skill_title }}**: Run the commands in the **Commands** table sequentially.
2.  **CWD Awareness**: For each command, ensure you are in the specified **Path**.
3.  **Verify**: Check the output of the commands to ensure they succeeded.
