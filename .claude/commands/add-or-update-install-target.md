---
name: add-or-update-install-target
description: Workflow command scaffold for add-or-update-install-target in everything-claude-code.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-install-target

Use this workflow when working on **add-or-update-install-target** in `everything-claude-code`.

## Goal

Adds or updates an install target (e.g., IDE, plugin, integration) with scripts, schemas, and manifest registration.

## Common Files

- `.*/install.js`
- `.*/install.sh`
- `.*/uninstall.js`
- `.*/uninstall.sh`
- `manifests/install-modules.json`
- `schemas/ecc-install-config.schema.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Add new install scripts (install.js, install.sh, uninstall.js, uninstall.sh) under a dedicated directory (e.g., .codebuddy/).
- Update manifests/install-modules.json to include the new target.
- Update schemas/ecc-install-config.schema.json and schemas/install-modules.schema.json as needed.
- Add or update scripts/lib/install-targets/*.js for the new target.
- Update tests/lib/install-targets.test.js to cover the new target.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.