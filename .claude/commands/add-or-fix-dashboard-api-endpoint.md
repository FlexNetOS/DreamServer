---
name: add-or-fix-dashboard-api-endpoint
description: Workflow command scaffold for add-or-fix-dashboard-api-endpoint in DreamServer.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-fix-dashboard-api-endpoint

Use this workflow when working on **add-or-fix-dashboard-api-endpoint** in `DreamServer`.

## Goal

Add new API endpoints or fix/extend existing ones in the dashboard API, often accompanied by UI and test updates.

## Common Files

- `dream-server/extensions/services/dashboard-api/routers/*.py`
- `dream-server/extensions/services/dashboard-api/tests/*.py`
- `dream-server/extensions/services/dashboard/src/pages/*.jsx`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Edit or add routers/*.py in dashboard-api to implement/fix endpoint.
- Update or add corresponding tests in tests/*.py.
- Edit dashboard/src/pages/*.jsx to update UI as needed.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.