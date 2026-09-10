# MEMORY_INDEX

## Metadata
- module: `scaffold-memory`
- artifact_type: `improvement`
- created_at: `2026-04-26T06:43:16+07:00`
- updated_at: `2026-04-26T21:42:16+07:00`
- runtime: `codex`
- owner: `founder`
- status: `in_progress`
- task_id: `TASK-20260425-001`
- resume_safe: `yes`

## Purpose
Index persistent scaffold memory entries and their current status.

## Source Of Truth
- Policy: `guardrails/memory/MEMORY_POLICY.md`
- Capture rules: `guardrails/memory/MEMORY_CAPTURE_RULES.md`
- Recall rules: `guardrails/memory/MEMORY_RECALL_RULES.md`
- Retention rules: `guardrails/memory/MEMORY_RETENTION_POLICY.md`
- Machine-readable ledger: `artifacts/memory/MEMORY_LEDGER.toml`
- Feature/module registry: `artifacts/memory/FEATURE_REGISTRY.toml`

## Maintenance Agent
- Codex agent: `.codex/agents/memory-curator.md`
- Claude agent: `.claude/agents/memory-curator.md`
- default_behavior: `invoke after meaningful workflow events or explicit memory commands`
- authority: `advisory_only`

## Memory Files
- `artifacts/memory/PROJECT_FACTS.md`
- `artifacts/memory/WORKFLOW_PATTERNS.md`
- `artifacts/memory/CONSTRAINTS.md`
- `artifacts/memory/TASK_GRAPH.md`
- `artifacts/memory/MEMORY_CHANGELOG.md`
- `artifacts/memory/MEMORY_LEDGER.toml`
- `artifacts/memory/FEATURE_REGISTRY.md`
- `artifacts/memory/FEATURE_REGISTRY.toml`

## Feature Registry Status
- registry: `artifacts/memory/FEATURE_REGISTRY.toml`
- human_summary: `artifacts/memory/FEATURE_REGISTRY.md`
- target_repo_status: `not_attached`
- feature_discovery_status: `not_started`
- module_discovery_status: `not_started`
- current_entries: `0`

## Current Entries

| ID | Type | Status | Confidence | Source | Review After | Summary |
|---|---|---|---|---|---|---|
| MEM-PF-001 | project_fact | verified | high | `artifacts/operations/WORKFLOW_STATE.md` | 2026-05-26 | Target contributor repository is not attached yet. |
| MEM-PF-002 | project_fact | verified | high | `AGENTS.md` | 2026-05-26 | `guardrails/` contains strict rules and `artifacts/` contains state and outputs. |
| MEM-WF-001 | workflow_pattern | verified | high | `COMMANDS.md` | 2026-05-26 | User-facing commands are centralized in root `COMMANDS.md`. |
| MEM-CON-001 | constraint | verified | high | `artifacts/operations/PRE_CODING_GATE.md` | 2026-05-26 | Coding is blocked until target repo, intake, impact scan, allowed write paths, and founder approval exist. |
| MEM-TASK-001 | task_node | verified | high | `artifacts/operations/CURRENT_TASK.md` | 2026-05-26 | Next real workflow action is read-only `I1 Existing Project Intake` after a target repo is attached. |
| MEM-WF-002 | workflow_pattern | verified | high | `guardrails/flutter/FLUTTER_DEVELOPMENT_POLICY.md` | 2026-05-26 | Existing Flutter/Dart projects are supported through Flutter-specific intake, policy, builder, and QA agents, but Flutter build remains blocked until intake, impact scan, allowed write paths, and approval exist. |
