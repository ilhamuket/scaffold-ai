# Dev Doc

`dev-doc/` stores compact source documents for feature planning and development.

For feature entries in `plan/feature-listing.md`, BRD and PRD must be placed here.

Removed legacy roots `artifacts/brd/`, `artifacts/prd/`, and `artifacts/design/` must not be recreated.

Use one folder per feature:

```text
dev-doc/[feature-name]/
  brd.md
  prd.md
  use-case.md
  userflow.md
  database-diagram.md
  design/
    page-overview.md
    [page]/[section]/design.md
    [page]/[section]/assets/
    [page]/[section]/[sub-section]/prototype/index.html
  implementation-plan.md
  impact-scan.md
  qa-checklist.md
  handoff.md
```

Required before build planning:
- `brd.md`
- `prd.md`
- `use-case.md`
- `userflow.md`
- `database-diagram.md`

Optional but recommended:
- `implementation-plan.md`
- `impact-scan.md`
- `qa-checklist.md`
- `handoff.md`

Feature-specific design references for the same feature also live here:

```text
dev-doc/[feature-name]/design/
```

If UI does not exist yet and the runtime creates an HTML UI shell, store it as a prototype reference:

```text
dev-doc/[feature-name]/design/[page]/[section]/[sub-section]/prototype/index.html
```

HTML prototypes are not production source code. They may guide frontend implementation, but they must not be copied into the target frontend/backend source tree unless an approved development scope explicitly promotes them to production implementation.

Shared UI baselines may exist in:

```text
templates/design/master-ui-templates/
```

Use `templates/design/master-ui-templates/` only as a shared fallback or legacy reference, not as the primary source of truth for an active feature folder.

If a document is missing, mark it as `missing` and ask for clarification or documentation. Do not invent missing documents.
