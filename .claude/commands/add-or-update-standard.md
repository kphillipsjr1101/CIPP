---
name: add-or-update-standard
description: Workflow command scaffold for add-or-update-standard in CIPP.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-standard

Use this workflow when working on **add-or-update-standard** in `CIPP`.

## Goal

Adds a new standard or updates an existing one in the application, typically reflecting a new policy or configuration option.

## Common Files

- `src/data/standards.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or append new entry to src/data/standards.json
- Optionally update related documentation or UI to reflect the new standard

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.