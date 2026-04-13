---
name: add-or-update-alert
description: Workflow command scaffold for add-or-update-alert in CIPP.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-alert

Use this workflow when working on **add-or-update-alert** in `CIPP`.

## Goal

Adds or updates an alert definition and its configuration UI for tenant monitoring.

## Common Files

- `src/data/alerts.json`
- `src/pages/tenant/administration/alert-configuration/alert.jsx`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit src/data/alerts.json to add or update alert definition
- Edit src/pages/tenant/administration/alert-configuration/alert.jsx to implement or update alert UI/configuration

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.