---
name: add-or-update-alert
description: Workflow command scaffold for add-or-update-alert in CIPP.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-alert

Use this workflow when working on **add-or-update-alert** in `CIPP`.

## Goal

Adds or modifies an alert definition for tenant monitoring, including UI configuration.

## Common Files

- `src/data/alerts.json`
- `src/pages/tenant/administration/alert-configuration/alert.jsx`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or append entry in src/data/alerts.json
- Update src/pages/tenant/administration/alert-configuration/alert.jsx to reflect the new/changed alert

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.