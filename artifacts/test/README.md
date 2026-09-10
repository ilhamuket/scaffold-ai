# artifacts/test

Store test and QA artifacts here.

Founder-authored active bug-fix input belongs in root `bug-listing/`, not in this folder.

Default automated platform for browser-based functionality testing:
- `Playwright`

Recommended automated evidence flow:
- run Playwright functional/E2E tests in the product repo
- keep Playwright test source under `playwright/` instead of scattering it in the repo root
- keep Playwright runtime artifacts under `artifacts/qa/playwright/`
- summarize results here
- attach bug IDs and verification evidence

## Runtime Output Boundary

- Prepared Playwright runtime artifact root: `../qa/playwright/`
- Prepared HTML report folder: `../qa/playwright/report/`
- Prepared raw result folder: `../qa/playwright/test-results/`
- Prepared CLI log folder: `../qa/playwright/.playwright-cli/`
- Keep this `artifacts/test/` folder for human-authored summaries and verification docs, not raw Playwright output dumps.

## Bug Fix Input vs Evidence

- Default founder input queue/index: `bug-listing/list-bug.md`
- Dynamic founder input files: `bug-listing/[bug-list-name].md`
- Bug-fix evidence and runtime-maintained status stay here in `artifacts/test/`
- Do not create new founder-facing bug lists under `artifacts/test/bug-list/`

## Recommended Files Per Module

- Frontend QA: `[module]-frontend-qa.md`
- API QA: `[module]-api-qa.md`
- Backend QA: `[module]-backend-qa.md`
- DB QA: `[module]-db-qa.md`
- Integration QA: `[module]-integration-qa.md`
- E2E QA: `[module]-e2e-qa.md`
- Security QA: `[module]-security-qa.md`
- Bug log: `[module]-bug-log.md`
- Bug status summary: `[module]-bug-status.md`

## Bug Log Template (Minimal)

```markdown
## Metadata
- module: `[module-name]`
- artifact_type: `test`
- created_at: `YYYY-MM-DDTHH:mm:ss+07:00`
- updated_at: `YYYY-MM-DDTHH:mm:ss+07:00`
- runtime: `[claude|codex|manual]`
- owner: `[name-or-role]`
- status: `in_progress`

### Entry: `BUG-[module]-[NNN]`
- created_at: `YYYY-MM-DDTHH:mm:ss+07:00`
- updated_at: `YYYY-MM-DDTHH:mm:ss+07:00`
- severity: `[critical|high|medium|low]`
- status: `[open|triaged|in_progress|fixed|verified|closed|reopened]`
- title: `...`
- environment: `...`
- reproduce_steps: `...`
- expected: `...`
- actual: `...`
- root_cause: `...`
- fix_reference: `...`
- verification_evidence: `...`
```

See also: `guardrails/development/LOGGING_STANDARD.md`

Recommended templates:
- `templates/qa/e2e-qa-report-template.md`
- `templates/qa/auth-login.functional.spec.ts.example`

