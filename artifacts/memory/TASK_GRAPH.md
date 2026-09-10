# TASK_GRAPH

Dependency-aware task memory for resuming work across sessions.

## Current Graph

### `MEM-TASK-001`
- type: `task_node`
- status: `verified`
- confidence: `high`
- created_at: `2026-04-26T06:43:16+07:00`
- updated_at: `2026-04-26T06:43:16+07:00`
- source: `artifacts/operations/CURRENT_TASK.md`
- review_after: `2026-05-26`
- summary: `Next real workflow action is read-only I1 Existing Project Intake after a target repo is attached.`
- depends_on: `target_repo_path_or_url`
- blocks: `I2 Impact Scan, P1-P7, B1-B3, R1-R4`

## Dependency Notes
- `I1 Existing Project Intake` requires a target repository path or URL.
- `I2 Impact Scan` requires completed intake and one scoped change.
- Build steps require completed impact scan, allowed write paths, and founder approval.
- Feature/module dependency state belongs in `artifacts/memory/FEATURE_REGISTRY.toml` and `artifacts/memory/FEATURE_REGISTRY.md`.
