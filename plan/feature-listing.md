# Feature Listing Input Queue

## Metadata
- module: `feature-listing`
- artifact_type: `improvement`
- created_at: `2026-05-07T16:06:33+07:00`
- updated_at: `2026-09-07T00:00:00+07:00`
- runtime: `claude`
- owner: `founder`
- status: `active`
- task_id: `TASK-TEMPLATE-000`
- resume_safe: `yes`

## Purpose
This file is the user-editable queue for features that should be planned or developed.

The system reads each non-empty, non-comment line, detects the prefix, then looks for supporting documents in `dev-doc/[feature-name]/` and feature-specific design references in `dev-doc/[feature-name]/design/`.

Do not look for feature BRD or PRD in removed legacy roots. For this queue, BRD and PRD live only inside `dev-doc/[feature-name]/`.

Bug-fix input lists live in root `bug-listing/`, not under `artifacts/test/bug-list/`.

## Accepted Prefixes

```text
new feature/[feature-name]
add feature/[feature-name]
bugfix/[bug-list-name]
```

- `new feature/[feature-name]`: a new feature or module that does not exist yet.
- `add feature/[feature-name]`: an addition to an existing module or feature.
- `bugfix/[bug-list-name]`: a bug-fix scope driven by `bug-listing/[bug-list-name].md` or `bug-listing/list-bug.md`.

## Feature Queue

Add one feature per line below. Lines beginning with `#` are comments and should be ignored.

```text
# Examples:
# new feature/login-otp
# add feature/student-attendance-export
# bugfix/main
```

Write your real feature list here:

```text
# (empty — no feature queued yet)
```

## How To Fill This File

Use this format when the feature or module does not exist yet:

```text
new feature/[feature-name]
```

Example:

```text
new feature/login-otp
```

Use this format when the feature is added to an existing module:

```text
add feature/[feature-name]
```

Example:

```text
add feature/student-attendance-export
```

The `[feature-name]` must match the folder names used for docs and design:

```text
plan/feature-listing.md entry:
new feature/login-otp

docs folder:
dev-doc/login-otp/

design folder:
dev-doc/login-otp/design/
```

## Lookup Rules

For every feature entry, the system must check:

```text
dev-doc/[feature-name]/
dev-doc/[feature-name]/design/
```

Required documents under `dev-doc/[feature-name]/`:

```text
brd.md
prd.md
use-case.md
userflow.md
database-diagram.md
```

Optional documents under `dev-doc/[feature-name]/`:

```text
implementation-plan.md
impact-scan.md
qa-checklist.md
handoff.md
```

Design documents and assets are looked up under:

```text
dev-doc/[feature-name]/design/
```

Feature BRD and PRD are not looked up under removed legacy roots.

Bug-fix lists are looked up under:

```text
bug-listing/[bug-list-name].md
bug-listing/list-bug.md
```

## Missing Document Behavior

If a required document or design folder does not exist:

- Mark it as `missing`.
- Do not invent document contents.
- Continue with planning or clarification only.
- Do not open build gates.
- Do not edit product code.

## Processing Rules

### `new feature/[feature-name]`
- Treat the scope as a new feature or module.
- Check required docs in `dev-doc/[feature-name]/`.
- Check design in `dev-doc/[feature-name]/design/`.
- If documents are missing, list missing docs and recommend the next clarification/documentation action.
- Continue to architecture/sprint/build only after requirements, impact, allowed write paths, and founder approval exist.

### `add feature/[feature-name]`
- Treat the scope as an addition to an existing module.
- Check required docs in `dev-doc/[feature-name]/`.
- Check design in `dev-doc/[feature-name]/design/`.
- Require impact scan before coding because existing behavior may be affected.
- Continue to build only after allowed write paths and founder approval exist.

### `bugfix/[bug-list-name]`
- Treat the scope as bug-fix work.
- Read `bug-listing/[bug-list-name].md` if it exists.
- If the named file does not exist, read `bug-listing/list-bug.md`.
- Bug list names are dynamic and may be scoped by module, page, role, flow, sprint, release, or regression batch.
- Require intake, impact scan, allowed write paths, and pre-coding gate before implementation.
- Keep the root bug listing, `artifacts/test/[module]-bug-log.md`, and `artifacts/test/[module]-bug-status.md` synchronized.
- For UI or browser-visible bugfixes, run required QA before moving to the next bug.

## Parser Acceptance Examples

These lines must be recognized:

```text
new feature/login-otp
add feature/student-attendance-export
bugfix/main
```

Expected lookup results:

```text
dev-doc/login-otp/
dev-doc/login-otp/design/

dev-doc/student-attendance-export/
dev-doc/student-attendance-export/design/

bug-listing/main.md
bug-listing/list-bug.md
```
