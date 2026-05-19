---
name: update-extension-manifest-defaults
description: Workflow command scaffold for update-extension-manifest-defaults in DreamServer.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /update-extension-manifest-defaults

Use this workflow when working on **update-extension-manifest-defaults** in `DreamServer`.

## Goal

Standardize or correct default values in extension manifest.yaml files, often to improve CLI/dashboard compatibility or platform support.

## Common Files

- `resources/dev/extensions-library/services/*/manifest.yaml`
- `dream-server/extensions/services/*/manifest.yaml`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit one or more manifest.yaml files under resources/dev/extensions-library/services/*/ or dream-server/extensions/services/*/
- Set or update default values for env_vars or gpu_backends fields.
- Optionally, update related documentation or compose files.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.