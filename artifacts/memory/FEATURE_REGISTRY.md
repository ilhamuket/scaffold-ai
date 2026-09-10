# FEATURE_REGISTRY

Human-readable feature and module registry.

Machine-readable registry:
- `artifacts/memory/FEATURE_REGISTRY.toml`

Maintained by:
- Codex: `.codex/agents/memory-curator.md`
- Claude: `.claude/agents/memory-curator.md`

## Metadata
- module: `feature-registry`
- artifact_type: `memory-feature-registry`
- created_at: `2026-04-26T07:10:04+07:00`
- updated_at: `2026-09-07T00:00:00+07:00`
- runtime: `none`
- owner: `founder`
- status: `active`
- task_id: `none`
- resume_safe: `yes`

## Purpose
Track known features and modules across sessions without mixing active task state, daily session history, and durable project memory.

Use this registry to answer:
- What features or modules are known?
- What is each feature's latest workflow status?
- Which systems are involved?
- Which features/modules depend on each other?
- What is blocked, risky, tested, released, or deprecated?

## Current State
- target_repo_status: `not_attached`
- feature_discovery_status: `not_started`
- module_discovery_status: `not_started`
- current_entries: `0`

`none yet — add entries after I1/I2 discovers modules or scopes a feature.`

## Entry Template

```markdown
### `FEAT-001`
- name: `Feature name`
- type: `feature|module|integration|workflow`
- status: `discovered|intake_only|impact_scanned|requirements_ready|design_ready|architecture_ready|planned|in_progress|blocked|qa_ready|qa_failed|qa_passed|release_ready|released|deprecated|unknown`
- current_gate: `I1|I2|P1|P2|P3|P4|P5|P6|P7|B1|B2|B3|R1|R2|R3|R4|none`
- source: `path/to/source-artifact.md`
- last_updated_at: `YYYY-MM-DDTHH:mm:ss+07:00`
- owner_runtime: `codex|claude|manual`
- summary: `One sentence summary.`
- impacted_systems: `frontend, backend, database, external-api, queue, auth, storage, iot, unknown`
- depends_on: `feature/module ids`
- blocks: `feature/module ids`
- related_artifacts: `paths`
- related_tests: `paths`
- risks: `known risks`
- notes: `short notes`
```

## Registry Rules
- Add entries after `I1 Existing Project Intake` discovers modules or after `I2 Impact Scan` scopes a feature.
- Update entries after build, QA, release, incident, or founder decision events.
- Do not create entries from guesses.
- Do not mark a feature released or QA-passed without evidence.
- Keep this file synchronized with `FEATURE_REGISTRY.toml`.
