# LEARNINGS

## Usage
Record what worked and what failed to prevent repeated mistakes.

## Metadata
- module: `[global-or-feature]`
- artifact_type: `log`
- created_at: `YYYY-MM-DDTHH:mm:ss+07:00`
- updated_at: `2026-07-21T09:42:34+07:00`
- runtime: `[claude|codex|manual]`
- owner: `[name-or-role]`
- status: `in_progress`

## Entry Template

```markdown
### Entry: `LRN-[module]-[NNN]`
- created_at: `YYYY-MM-DDTHH:mm:ss+07:00`
- updated_at: `YYYY-MM-DDTHH:mm:ss+07:00`
- module: `[module-name]`
- status: `[open|applied|superseded]`
- context: `...`
- worked: `...`
- failed: `...`
- root_cause: `...`
- recommendation: `...`
- linked_artifacts: `[path1, path2]`
```

## Example

```markdown
### Entry: `LRN-auth-login-001`
- created_at: `2026-04-10T21:35:00+07:00`
- updated_at: `2026-04-10T21:35:00+07:00`
- module: `auth-login`
- status: `applied`
- context: `Frontend QA found a mismatch in the error state.`
- worked: `Added a design token for error text and border.`
- failed: `A hardcoded color caused a mismatch on the dark surface.`
- root_cause: `The implementation did not follow the specs in design.md.`
- recommendation: `Always map styles to design tokens before merge.`
- linked_artifacts: `artifacts/test/auth-login-frontend-qa.md`
```

See also: `guardrails/development/LOGGING_STANDARD.md`

### Entry: `LRN-scaffold-logging-001`
- created_at: `2026-06-18T12:04:49+07:00`
- updated_at: `2026-06-18T12:04:49+07:00`
- module: `scaffold-strict-logging`
- status: `applied`
- context: `Handoffs were being resumed without a reliable latest-step log entry.`
- worked: `Added hard guardrails so step completion and handoff require a matching SESSION_LOG entry and documentation sync record.`
- failed: `State docs alone were not sufficient to catch missing session log records.`
- root_cause: `The previous policy allowed completion of an official step without an explicit log completeness check.`
- recommendation: `Treat missing session log entries as a hard blocker before any next step or handoff.`
- linked_artifacts: `artifacts/operations/SESSION_LOG.md, guardrails/development/HANDOFF_PROTOCOL.md, guardrails/development/LOGGING_STANDARD.md`

### Entry: `LRN-design-html-prototype-001`
- created_at: `2026-06-18T13:11:20+07:00`
- updated_at: `2026-06-18T13:11:20+07:00`
- module: `design-html-prototype`
- status: `applied`
- context: `The scaffold supported design images and Figma references, but did not explicitly define where generated HTML UI shells should live.`
- worked: `Added explicit prototype paths for feature-specific and shared HTML UI references.`
- failed: `Leaving HTML prototypes to the generic assets rule could lead agents to place reference HTML in assets, artifacts, or production source inconsistently.`
- root_cause: `The design folder guardrails were written for images and Figma links before HTML UI shells became a regular reference artifact.`
- recommendation: `Treat generated HTML UI shells as isolated design reference artifacts under prototype/ unless an approved development scope promotes them to source implementation.`
- linked_artifacts: `AGENTS.md, CLAUDE.md, dev-doc/README.md, templates/design/master-ui-templates/README.md, guardrails/design/DESIGN_FOLDER_STRUCTURE.md, guardrails/design/DESIGN_ASSET_SUBMISSION.md`

### Entry: `LRN-task-type-classification-001`
- created_at: `2026-06-18T14:12:43+07:00`
- updated_at: `2026-06-18T14:12:43+07:00`
- module: `task-type-classification`
- status: `applied`
- context: `Existing-project work may arrive as feature work, bug fixing, refactor, migration, security, dependency, review-only, hotfix, or local readiness, and forcing every request into feature/bug flow leaves gaps.`
- worked: `Added a shared task type classification policy, registry, and template that all runtimes must use before significant work.`
- failed: `Without an explicit classification gate, agents could jump into coding or choose the wrong workflow for ambiguous or high-risk requests.`
- root_cause: `The previous guardrails defined many workflows but did not require a common entry classification step across Codex/GPT, Claude, and Gemini.`
- recommendation: `Classify task type, confidence, risk, required gates, artifacts, tests, and stop conditions before significant work; ask the founder when risk or ambiguity is non-trivial.`
- linked_artifacts: `guardrails/system/TASK_TYPE_CLASSIFICATION.md, guardrails/system/TASK_TYPE_REGISTRY.md, templates/task_classification_template.md, AGENTS.md, CLAUDE.md, GEMINI.md`

### Entry: `LRN-lifecycle-audit-cleanup-001`
- created_at: `2026-06-18T14:32:00+07:00`
- updated_at: `2026-06-18T14:32:00+07:00`
- module: `ai-contributor-lifecycle`
- status: `applied`
- context: `The evaluation document called for strict multi-agent flow, baseline testing, QA layers, impact checking, and handoff readiness, while the scaffold still had a few ambiguous parity and QA evidence gaps.`
- worked: `Updated runtime parity to explicitly include Codex/GPT, Claude, and Gemini; registered lifecycle support steps; added granular QA evidence; and documented a recommended multi-agent route.`
- failed: `The previous wording still implied some parity rules were only for Claude and Codex, and final QA could be interpreted too broadly without per-layer evidence.`
- root_cause: `Lifecycle guardrails existed, but several enforcement details were spread across workflow docs, commands, and runtime files instead of being registered and named consistently.`
- recommendation: `Keep lifecycle support steps, QA evidence, and runtime parity labels synchronized whenever the contributor workflow is improved.`
- linked_artifacts: `workflows/ai_contributor_lifecycle.md, guardrails/system/RUNTIME_PARITY_CONTRACT.md, guardrails/system/STEP_REGISTRY.md, templates/granular_qa_evidence_template.md, AGENTS.md, CLAUDE.md, GEMINI.md`

### Entry: `LRN-runtime-root-doc-consolidation-001`
- created_at: `2026-07-18T16:00:22+07:00`
- updated_at: `2026-07-18T16:00:22+07:00`
- task_id: `TASK-20260425-001`
- module: `runtime-root-docs`
- status: `applied`
- context: `Runtime-specific root files duplicated operational rules across AGENTS.md, CLAUDE.md, and GEMINI.md.`
- worked: `Consolidated unique Claude and Gemini guidance into AGENTS.md and converted CLAUDE.md and GEMINI.md into minimal compatibility pointers.`
- failed: `Duplicated root docs previously made instruction drift easier during scaffold improvements.`
- root_cause: `Runtime compatibility files had grown from pointers into parallel sources of truth.`
- recommendation: `Keep AGENTS.md as the only runtime instruction source and leave CLAUDE.md/GEMINI.md as redirect stubs unless the founder approves a new compatibility pattern.`
- linked_artifacts: `AGENTS.md, CLAUDE.md, GEMINI.md, README.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-medium-major-plan-first-001`
- created_at: `2026-07-18T16:41:21+07:00`
- updated_at: `2026-07-18T16:41:21+07:00`
- task_id: `TASK-20260425-001`
- module: `plan-first-gate`
- status: `applied`
- context: `The founder wanted strict planning approval for meaningful work without wasting tokens on simple questions.`
- worked: `Added a medium/major-only compact-plan gate so risky or multi-artifact work requires explicit founder approval before execution.`
- failed: `A universal plan-first rule would waste tokens for direct explanations and lightweight read-only checks.`
- root_cause: `The scaffold had plan-first rules for official steps and implementation, but not a general strict gate by change size.`
- recommendation: `Use direct answers for small questions, lightweight intent notes for simple read-only checks, and compact plans with explicit approval for all medium or major work.`
- linked_artifacts: `AGENTS.md, COMMANDS.md, guardrails/development/PRE_CODING_POLICY.md, guardrails/development/LOGGING_STANDARD.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-coding-skill-lookup-gate-001`
- created_at: `2026-07-18T16:49:53+07:00`
- updated_at: `2026-07-18T16:49:53+07:00`
- task_id: `TASK-20260425-001`
- module: `coding-skill-lookup`
- status: `applied`
- context: `The founder wanted every coding task to use the most relevant runtime skill or agent before implementation starts.`
- worked: `Added a pre-coding skill lookup gate with runtime-specific lookup order and a mandatory skill-creator fallback when no relevant skill exists.`
- failed: `The previous rule only made skill lookup strict for official steps, leaving informal coding requests less explicit.`
- root_cause: `Skill lookup enforcement was tied to workflow step names instead of all coding-related work.`
- recommendation: `Before any coding-related work, find the relevant runtime skill or agent first; if none exists, run skill-creator before coding and still keep pre-coding gates closed until all approvals exist.`
- linked_artifacts: `AGENTS.md, COMMANDS.md, guardrails/development/PRE_CODING_POLICY.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-dev-doc-discovery-gate-001`
- created_at: `2026-07-18T16:59:48+07:00`
- updated_at: `2026-07-18T16:59:48+07:00`
- task_id: `TASK-20260425-001`
- module: `dev-doc-discovery`
- status: `applied`
- context: `The founder wanted agents to consult dev-doc before backend, frontend, feature, or system implementation, not only for UI work.`
- worked: `Added a strict dev-doc discovery gate before feature/module/system coding work and required planning baseline repair when new-feature docs are missing.`
- failed: `The previous rules made dev-doc clearly important for frontend/design and feature listing, but not strict for all backend or system builds.`
- root_cause: `Dev-doc usage was documented by artifact type instead of enforced as a pre-coding discovery gate.`
- recommendation: `Search dev-doc by feature slug, related module/domain, synonyms, and feature-listing entries before planning/building; if missing for new feature work, stop and create the baseline first.`
- linked_artifacts: `AGENTS.md, COMMANDS.md, guardrails/development/PRE_CODING_POLICY.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-artifact-storage-cleanup-001`
- created_at: `2026-07-18T17:18:06+07:00`
- updated_at: `2026-07-18T17:18:06+07:00`
- task_id: `TASK-20260425-001`
- module: `artifact-storage`
- status: `applied`
- context: `The scaffold had legacy artifact roots for BRD, PRD, and design even though active feature docs were already moving toward dev-doc, creating risk that agents would store outputs in inconsistent places.`
- worked: `Added a strict artifact storage policy, updated active path references, moved reusable design template guidance to templates, and deleted removed legacy artifact roots for a clean scaffold.`
- failed: `Keeping legacy folders as archive/reference locations would invite instruction drift and misplaced future artifacts in an empty scaffold.`
- root_cause: `Artifact storage rules were spread across runtime docs, design guardrails, workflow docs, and README files instead of being governed by one active storage map.`
- recommendation: `Before writing any artifact, classify the artifact type and follow ARTIFACT_STORAGE_POLICY; do not recreate artifacts/brd, artifacts/prd, or artifacts/design.`
- linked_artifacts: `guardrails/development/ARTIFACT_STORAGE_POLICY.md, artifacts/README.md, AGENTS.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-feature-task-slicing-context-first-001`
- created_at: `2026-07-18T17:46:17+07:00`
- updated_at: `2026-07-18T17:46:17+07:00`
- task_id: `TASK-20260425-001`
- module: `feature-task-slicing`
- status: `applied`
- context: `The founder wanted feature work to be analyzed into small tasks, limited to one feature per session, and supported by context/memory so agents do not repeatedly relearn the repository.`
- worked: `Added a strict feature task slicing policy, task breakdown template, pre-coding blockers, memory recall rules, and workflow-state contract for context-first targeted scans.`
- failed: `Without a hard rule, agents could over-scan the repo, activate multiple features, or spend tokens rediscovering project facts already captured in context and memory.`
- root_cause: `The scaffold had memory and dev-doc gates, but did not explicitly connect them to feature slicing, selected session slices, and full-repo scan restrictions.`
- recommendation: `For feature work, read current state, memory, feature registry, and dev-doc first; select one feature slice; scan only targeted paths; document any full repo scan reason before proceeding.`
- linked_artifacts: `guardrails/development/FEATURE_TASK_SLICING_POLICY.md, templates/feature_task_breakdown_template.md, guardrails/memory/MEMORY_POLICY.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-shared-target-context-001`
- created_at: `2026-07-18T18:13:47+07:00`
- updated_at: `2026-07-18T18:13:47+07:00`
- task_id: `TASK-20260425-001`
- module: `shared-target-context`
- status: `applied`
- context: `The founder expects multiple developers to use the same scaffold on the same target project, and developer B's agent must understand developer A's latest context from Git-carried project files.`
- worked: `Added a shared target repository context policy and templates requiring ACTIVE_CONTEXT, CONTRIBUTOR_LOG, and handoff files under development/[project-folder]/artifacts/shared/.`
- failed: `Keeping continuity only in scaffold-local SESSION_LOG or memory would not reliably travel with the target project repository across developers.`
- root_cause: `The scaffold previously separated operational logs and memory locally, but did not define a Git-safe shared context layer inside the target repo.`
- recommendation: `For target repo work, read shared context before source scanning and update it after meaningful work, pause, blocker discovery, QA closure, handoff, implementation slice, or session close.`
- linked_artifacts: `guardrails/development/SHARED_CONTEXT_POLICY.md, templates/shared_active_context_template.md, templates/shared_contributor_log_template.md, templates/shared_handoff_template.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-manual-visual-qa-notification-001`
- created_at: `2026-07-21T09:42:34+07:00`
- updated_at: `2026-07-21T09:42:34+07:00`
- task_id: `TASK-20260425-001`
- module: `manual-visual-qa`
- status: `applied`
- context: `The founder wanted explicit notification when a QA pass requires human visual judgment.`
- worked: `Added manual visual QA notification rules to runtime QA policy, command guidance, granular QA evidence, shared context, and handoff templates.`
- failed: `Without explicit fields, agents could mark visual QA as skipped or pass without clearly asking the founder to review UI-sensitive changes.`
- root_cause: `The previous QA rules covered manual/browser blockers generally but did not require a founder-facing manual visual QA notification with route/state/checklist details.`
- recommendation: `When UI, layout, responsive behavior, visual state, animation, chart, canvas, generated image, PDF/rendered document, or browser-visible flow needs human judgment, notify the founder and keep ui_visual blocked/pending until sufficient automated evidence or founder approval exists.`
- linked_artifacts: `AGENTS.md, COMMANDS.md, templates/granular_qa_evidence_template.md, templates/shared_active_context_template.md, templates/shared_handoff_template.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-qa-token-efficiency-001`
- created_at: `2026-07-21T10:15:00+07:00`
- updated_at: `2026-07-21T10:15:00+07:00`
- task_id: `TASK-20260425-001`
- module: `qa-token-efficiency`
- status: `applied`
- context: `The founder wanted QA to remain reliable while avoiding repeated broad tests, unnecessary repository context, and long raw logs.`
- worked: `Added strict impact-scoped QA defaults, documented exceptions for broad/full-suite runs, last-passing-point delta checks, concise output summaries, and durable evidence-path rules.`
- failed: `The earlier QA policy required evidence and granular status, but did not explicitly prevent default broad-suite runs or repeated unchanged checks.`
- root_cause: `QA scope and logging requirements existed, but there was no dedicated policy connecting impact evidence, test-command selection, rerun decisions, and context-size control.`
- recommendation: `Start with the smallest check covering the impacted behavior; only expand QA with a recorded reason, and retain concise summaries plus evidence paths instead of raw logs.`
- linked_artifacts: `guardrails/qa/QA_TOKEN_EFFICIENCY_POLICY.md, AGENTS.md, COMMANDS.md, templates/during_dev_qa_log_template.md, templates/granular_qa_evidence_template.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-code-derived-project-baseline-001`
- created_at: `2026-07-21T21:15:19+07:00`
- updated_at: `2026-07-21T21:15:19+07:00`
- task_id: `TASK-20260425-001`
- module: `code-derived-project-baseline`
- status: `applied`
- context: `The founder wanted agents to retain a reliable project understanding when an inherited target repository has no BRD, PRD, or usable documentation.`
- worked: `Made target-repository PROJECT_STATE.md mandatory during first intake, required a founder documentation-reference question after an empty targeted search, and defined source-linked memory synchronization with targeted discovery rules.`
- failed: `Earlier memory and shared-context rules could preserve intake facts, but did not strictly require a code-derived baseline artifact or a founder reference check when documentation was absent.`
- root_cause: `The scaffold treated PROJECT_STATE.md as optional and did not connect empty documentation discovery to a mandatory source-derived baseline and memory-sync completion rule.`
- recommendation: `Ask for references after targeted documentation discovery finds no usable material; then create a concise source-linked project baseline, record unknowns, sync verified facts to memory, and use the baseline to narrow all future scans.`
- linked_artifacts: `guardrails/development/CODE_DERIVED_BASELINE_POLICY.md, guardrails/development/SHARED_CONTEXT_POLICY.md, templates/shared_project_state_template.md, AGENTS.md, COMMANDS.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-greenfield-start-routing-001`
- created_at: `2026-07-21T23:20:25+07:00`
- updated_at: `2026-07-21T23:20:25+07:00`
- task_id: `TASK-20260425-001`
- module: `greenfield-project-routing`
- status: `applied`
- context: `The founder wanted the same scaffold to support new projects from zero and to choose the correct route automatically when start is entered.`
- worked: `Added a G0-G5 greenfield route, required first-feature documentation and bootstrap approvals, and made start inspect development/ so zero entries select greenfield while one or more entries select existing/inherited intake.`
- failed: `The prior scaffold was designed around attached or inherited repositories, so it would incorrectly require I1/I2 before a new project had any repository or change baseline.`
- root_cause: `Startup modes described product categories but did not define a separate project-origin route or a strict automatic decision based on development/ state.`
- recommendation: `Use start as routing only: keep greenfield discovery documentation-first, build one approved feature slice at a time, and never allow framework bootstrap merely because development/ is empty.`
- linked_artifacts: `guardrails/development/GREENFIELD_PROJECT_POLICY.md, workflows/greenfield_project_workflow.md, templates/greenfield_project_charter_template.md, templates/greenfield_bootstrap_plan_template.md, AGENTS.md, COMMANDS.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-readme-workflow-summary-001`
- created_at: `2026-07-21T23:48:38+07:00`
- updated_at: `2026-07-21T23:48:38+07:00`
- task_id: `TASK-20260425-001`
- module: `readme-workflow-summary`
- status: `applied`
- context: `The root README still described only existing/inherited-project onboarding after the scaffold gained greenfield routing and token-efficient continuity controls.`
- worked: `Updated README as a concise user-facing summary of project-origin routing, baseline continuity, and QA behavior while leaving strict details in AGENTS.md and guardrails.`
- failed: `Operational logs and policy files captured the changes, but README users could follow obsolete existing-project-only guidance.`
- root_cause: `Major workflow improvements were recorded in operational artifacts without a corresponding README summary update.`
- recommendation: `Update README for major user-facing workflow changes, but keep per-change history in SESSION_LOG and LEARNINGS and strict requirements in guardrails.`
- linked_artifacts: `README.md, AGENTS.md, COMMANDS.md, artifacts/operations/SESSION_LOG.md`

### Entry: `LRN-requirement-precedence-readiness-gate-001`
- created_at: `2026-07-22T01:08:10+07:00`
- updated_at: `2026-07-22T01:08:10+07:00`
- task_id: `TASK-20260425-001`
- module: `requirement-precedence-readiness`
- status: `applied`
- context: `The contributor-flow evaluation identified missing strict precedence for product requirements and an implicit, rather than explicit, readiness baseline dependency before existing-project coding.`
- worked: `Added a source order for requirements, dedicated feature-level conflict decisions, and hard existing-project readiness evidence with CI/CD, formatter, healthcheck, and baseline-failure classification.`
- failed: `Earlier guardrail conflict policy only resolved scaffold-vs-repository rules, while lifecycle readiness evidence was not directly represented as a pre-coding blocker.`
- root_cause: `Product requirement authority and baseline-readiness status were distributed across documents without one enforcement point connected to coding permission.`
- recommendation: `Record the controlling requirement source, resolve material conflicts before coding, and use completed readiness evidence to separate inherited failures from change regressions.`
- linked_artifacts: `guardrails/development/REQUIREMENT_PRECEDENCE_POLICY.md, templates/requirement_conflict_decision_template.md, guardrails/development/PRE_CODING_POLICY.md, templates/readiness_baseline_template.md, artifacts/operations/PRE_CODING_GATE.md`

### Entry: `LRN-root-scaffold-workflow-guide-001`
- created_at: `2026-07-22T01:30:00+07:00`
- updated_at: `2026-07-22T01:30:00+07:00`
- task_id: `TASK-20260425-001`
- module: `root-scaffold-workflow-guide`
- status: `applied`
- context: `The scaffold had detailed rules distributed across AGENTS.md, guardrails, workflows, and templates, but developers needed one concise end-to-end guide.`
- worked: `Added SCAFFOLD_WORKFLOW.md in the root and linked it from README. The guide explains the purpose and sequence from start routing through intake, context recall, planning, gates, implementation, QA, handoff, and release readiness.`
- failed: `A single concise developer guide did not previously exist; users had to assemble the flow from multiple strict documents.`
- root_cause: `Detailed enforcement documents were intentionally distributed by responsibility without a lightweight navigation workflow.`
- recommendation: `Use SCAFFOLD_WORKFLOW.md for orientation, then consult AGENTS.md and the linked guardrails or templates whenever a strict gate or artifact requirement applies.`
- linked_artifacts: `SCAFFOLD_WORKFLOW.md, README.md, AGENTS.md, workflows/ai_contributor_lifecycle.md`

### Entry: `LRN-commands-release-boundary-sync-001`
- created_at: `2026-07-22T01:45:00+07:00`
- updated_at: `2026-07-22T01:45:00+07:00`
- task_id: `TASK-20260425-001`
- module: `commands-release-boundary`
- status: `applied`
- context: `The scaffold workflow now distinguishes continuity handoff, review readiness, release consideration, and actual release execution.`
- worked: `Updated COMMANDS.md with explicit handoff, release readiness, and release commands, plus readiness evidence fields and founder approval boundaries.`
- failed: `Earlier command guidance covered R3/R4 but did not clearly separate user-requested release readiness from an approved release action.`
- root_cause: `Release preparation, review readiness, and release execution were present but their decision boundaries were not explicit in the user-facing command menu.`
- recommendation: `Use handoff for continuity, ready to pr for review evidence, release readiness for release consideration, and release only after a separate explicit founder decision.`
- linked_artifacts: `COMMANDS.md, SCAFFOLD_WORKFLOW.md, AGENTS.md, artifacts/operations/PRE_CODING_GATE.md`

### Entry: `LRN-scaffold-improvement-parity-removal-001`
- created_at: `2026-07-22T02:00:00+07:00`
- updated_at: `2026-07-22T02:00:00+07:00`
- task_id: `TASK-20260425-001`
- module: `scaffold-improvement-scope`
- status: `applied`
- context: `The founder no longer wants scaffold/process changes to offer or enforce mirroring into sibling repositories.`
- worked: `Removed active ON/OFF scaffold-improvement parity controls, sibling-repository paths, plan fields, and operational contract fields while retaining runtime consistency requirements.`
- failed: `The earlier model mixed repository-mirroring controls with the separate requirement that Codex, Claude, and Gemini follow compatible workflow gates.`
- root_cause: `Both concepts used the word parity even though they control different concerns.`
- recommendation: `Treat scaffold improvements as local to the current repository. Keep runtime consistency as a separate contract for agent behavior and artifact compatibility.`
- linked_artifacts: `AGENTS.md, COMMANDS.md, SCAFFOLD_WORKFLOW.md, guardrails/system/RUNTIME_PARITY_CONTRACT.md`

### Entry: `LRN-runtime-skill-consolidation-001`
- created_at: `2026-07-22T02:25:00+07:00`
- updated_at: `2026-07-22T02:25:00+07:00`
- task_id: `TASK-20260425-001`
- module: `runtime-skill-consolidation`
- status: `applied`
- context: `Local skills were present under .agents/skills, which Codex could discover in some environments but which was not an official scaffold runtime source.`
- worked: `Copied all nine skills into both runtime folders, normalized their names with explicit category mappings, verified both copies against the source byte-for-byte, refreshed the catalog, and removed source files from .agents/skills.`
- failed: `The generic category heuristic classified several domain-specific skills incorrectly, including Vue, because their instructions contain vocabulary from multiple domains.`
- root_cause: `Category inference relied only on broad content keywords and did not include known-skill overrides.`
- recommendation: `Keep .codex/skills and .claude/skills as the only runtime roots. Use explicit category mappings for known multi-domain skills, then use find-skills with allowlisted acquisition before falling back to skill-creator.`
- linked_artifacts: `scripts/sync-skills.ps1, scripts/sync-skills.sh, guardrails/system/SKILL_CHECK_POLICY.md, guardrails/system/SKILL_CATALOG.md, AGENTS.md, COMMANDS.md`

### Entry: `LRN-team-repository-governance-001`
- created_at: `2026-07-22T03:05:00+07:00`
- updated_at: `2026-07-22T03:05:00+07:00`
- task_id: `TASK-20260425-001`
- module: `team-repository-governance`
- status: `applied`
- context: `The scaffold is becoming an internal Odonplay team baseline that may evolve without weakening its required workflow.`
- worked: `Added internal license, contribution and security guidance, CODEOWNERS, CI, protected-core change policy, Git initialization, and a committed shared-context default template.`
- failed: `The previous baseline had no Git repository, collaboration governance, CI, license, or safe default shared-context folder. A direct development template would also have broken greenfield detection without route exclusions.`
- root_cause: `The scaffold was built for workflow enforcement before it was prepared as a shared repository maintained by multiple contributors.`
- recommendation: `Keep target project code isolated in its own repository while allowing Git-safe target shared context to remain trackable. Require maintainer review for core workflow changes and CI validation for every pull request.`
- linked_artifacts: `LICENSE.md, CONTRIBUTING.md, SECURITY.md, CODEOWNERS, .github/workflows/validate-scaffold.yml, guardrails/system/SCAFFOLD_CORE_CHANGE_POLICY.md, development/_project-template/artifacts/shared/`

## LRN-nested-project-git-isolation-001
- Date: `2026-07-22`
- Learning: A scaffold repository and its target projects need separate Git repositories. The parent scaffold must ignore every target-project file, including shared context; that context is committed by the nested project repository.
- Control: `.gitignore` protects untracked paths only. Pair it with locally enabled root hooks and a GitHub Ruleset for server-side identity enforcement.
## LRN-codex-model-routing-001
- Date: `2026-07-22`
- Learning: Deterministic model switching must happen before a new Codex CLI session begins. AGENTS.md can govern routing behavior but cannot replace the model of an active thread.
- Control: Classify by risk, scope, accuracy floor, ambiguity, validation need, and relative token/cost band. Treat prompt length as a supporting signal only, record estimates honestly, and never auto-rerun a generic failed task on another model.

## LRN-codex-routing-tier-standard-001
- Date: `2026-07-22`
- Learning: A generic model alias can hide a more expensive routing target and undermine a cost-aware scaffold default.
- Control: Use explicit `gpt-5.6-luna`, `gpt-5.6-terra`, and `gpt-5.6-sol` profile identifiers. Reserve GPT-5.5 for founder-requested legacy reproduction or benchmarking, require documented evidence for escalation, and keep actual usage unavailable unless the runtime exposes authoritative data.

## LRN-codex-automatic-delegation-001
- Date: `2026-07-23`
- Learning: An active Codex editor session cannot replace its own model, so automatic routing needs a stable Terra supervisor and bounded child workers rather than a claimed in-place model switch.
- Control: Keep Terra as supervisor, delegate only Luna/Sol profiles through one ephemeral locked worker, and preserve workflow approvals, evidence, and no-retry behavior.

## LRN-antigravity-runtime-adapter-001
- Date: `2026-07-23`
- Learning: Antigravity uses workspace rules and its own skill path, while its active model remains sticky during a turn; a Codex child-worker implementation cannot be reused as though it were an Antigravity capability.
- Control: Use `.agents/rules/` as an Antigravity entrypoint to `AGENTS.md`, keep `.agents/skills/` byte-identical to the Codex canonical mirror, and record `model_switch_unavailable` rather than claiming unsupported automatic model changes.

## LRN-claude-vscode-model-routing-001
- Date: `2026-07-23`
- Learning: Claude Code VS Code supports model-aware native subagents, but its visible conversation model remains sticky and `Auto` controls permissions rather than model selection.
- Control: Start new project sessions on Sonnet, use bounded Haiku and Opus subagents for eligible task levels, and treat Fable as unavailable until a real local or managed model ID/alias is verified. Record `model_switch_unavailable` rather than claiming a switch that the runtime cannot perform.

## LRN-token-aware-agent-activity-log-001
- Date: `2026-07-23`
- Learning: Cross-agent continuity needs a dedicated activity record, but logging every tool call would consume context without improving handoff quality.
- Control: Use scaffold `artifacts/operations/AGENT_ACTIVITY_LOG.md` only for meaningful task lifecycle events. Keep a short current snapshot, read only relevant recent entries, and link rather than copy routing, QA, and handoff evidence.

## LRN-development-workspace-marker-001
- Date: `2026-07-23`
- Learning: A generic `README.md` directly under the local development workspace can collide with project or tool-generated documentation and silently break scaffold parity.
- Control: Keep `development/` free of scaffold marker files, store its instructions in `docs/DEVELOPMENT_WORKSPACE.md`, ignore direct workspace files by default, and exclude only `_project-template/` during startup detection.

## LRN-agent-activity-model-evidence-001
- Date: `2026-07-23`
- Learning: `not_recorded` hides whether a model is genuinely unknown or simply omitted, reducing the audit value of activity logs.
- Control: Require `model_or_profile`, `model_source`, and `model_availability_reason` for every activity event. Copy Codex router choices such as `gpt-5.6-terra / standard` exactly; use `active_model_unavailable` only when authoritative evidence does not exist.

## LRN-graphify-master-boundary-001
- Date: `2026-07-31`
- Learning: A reusable scaffold should provide Graphify's decision flow and project-scoped helpers, but not generate or commit a graph for itself or unrelated projects.
- Control: Keep `graphify-out/` local and ignored; record only graph status in target shared context, and require an explicit informed Y/N choice before setup or refresh.

## LRN-graphify-entrypoint-policy-001
- Date: `2026-08-01`
- Learning: Runtime skill guidance alone is insufficient because an agent can work outside the command-dispatch path.
- Control: Keep the mandatory Graphify consent, target-only, Git-safe, and update boundaries in `AGENTS.md`; skills and command documentation provide the operational detail.

## LRN-graphify-target-activation-001
- Date: `2026-08-01`
- Learning: A project can become active through attachment or a resumed session, not only through the start command.
- Control: Trigger the Graphify status choice whenever exactly one target is active, while retaining explicit user approval for every local Graphify action.

## LRN-scaffold-reset-to-template-001
- Date: `2026-09-07`
- Learning: A scaffold meant to be reused as a starting template must not carry a prior real project's operational history (task state, session log, activity log, memory feature registry, dev-doc, plan) as its default baseline — that history silently biases and slows down the next project's intake, and cannot be recovered once deleted without version control.
- Control: Before reusing this scaffold for a new project, confirm `artifacts/operations/*`, `artifacts/memory/FEATURE_REGISTRY.*`, `dev-doc/`, and `plan/` are at a clean `not_attached`/`none` baseline (not mid-task state from a previous engagement). Initialize a fresh local Git repository as soon as the scaffold is cloned for reuse so future resets are reversible.

## LRN-postgres-rls-docker-superuser-001
- Date: `2026-09-07`
- Learning: A Postgres Row-Level Security policy can be fully written, migrated, and even pass a test suite while doing nothing at all — `docker-compose`'s `POSTGRES_USER` bootstrap role is always a Postgres superuser with `BYPASSRLS`, and superuser/BYPASSRLS always ignores RLS regardless of `FORCE ROW LEVEL SECURITY`. This only surfaced by actually running the Docker stack and testing with real `psql`/HTTP requests against a live Postgres connection — the committed Pest suite ran against sqlite (where RLS deliberately no-ops), so "tests passing" gave false confidence about the DB-level defense layer specifically.
- Control: Whenever a greenfield bootstrap uses Postgres RLS as a tenant-isolation layer, create a dedicated non-superuser, non-BYPASSRLS application role via a `docker-entrypoint-initdb.d/init.sql` script and connect the app as that role — never as the compose-file bootstrap user. Verify RLS with a real query against the real database (not just against the test suite's sqlite connection) before treating it as a working control.

## LRN-postgres-set-command-bind-params-001
- Date: `2026-09-07`
- Learning: Postgres's `SET` configuration command does not accept query bind parameters (`SET x = $1` is a syntax error), even though it looks like ordinary SQL and works fine with a literal value. Laravel's `DB::statement($sql, $bindings)` uses bound parameters by default, so a naive `DB::statement('SET app.foo = ?', [$value])` fails — but only against a real Postgres connection, which is exactly the kind of bug a sqlite-only test suite cannot catch.
- Control: To set a Postgres session/config variable from a parameterized value, use `SELECT set_config('key', ?, false)` instead of `SET key = ?` — `set_config()` is a regular function call and accepts bind parameters normally.

## LRN-risk-tier-fast-track-001
- Date: `2026-09-07`
- Learning: A blanket "read ~17 files and run the full plan/dev-doc/slicing/doc-sync gate for every request" rule taxes trivial and low-risk work (typo fixes, single-file bounded edits, direct questions) as heavily as a schema migration, which slows everyday development without adding real safety for that class of work.
- Control: Added a Risk Tier classification (`trivial`/`low`/`medium`/`major-critical`) at the top of `AGENTS.md` Process Control Rules. `trivial`/`low` work skips the compact-plan gate, feature-slicing template, and the full mandatory-read list, but still requires skill lookup, an open pre-coding gate for code edits, and closes with a one-line `SESSION_LOG.md` note. Any mid-task surprise (schema/security impact, wider scope, ambiguous behavior) escalates immediately to `medium`, where the full gate applies unchanged. Also consolidated the three separate Codex/Antigravity/Claude-VS-Code model-routing gates into one unified gate to cut duplicated reading.

## LRN-rls-independent-of-orm-scope-bypass-001
- Date: `2026-09-09`
- Learning: When an app uses two independent tenant-isolation layers (an ORM-level global scope plus database-level Row-Level Security), bypassing the ORM layer for a legitimate cross-tenant code path (e.g. `withoutGlobalScopes()` for a public, unauthenticated endpoint) does nothing to the RLS layer — they are enforced completely independently. If the only code that ever mirrors the app's tenant context into the database's RLS session variables lives in authenticated-route middleware, any new unauthenticated route silently gets 100% of its reads/writes rejected by RLS, with an error that looks identical to "record not found" (404), not an obvious permissions failure. This was only caught by an actual `curl` against the real database — the automated test suite ran against sqlite, where RLS deliberately no-ops, so "tests passing" gave no signal here either.
- Control: When adding RLS as a second enforcement layer, put the app-context-to-RLS-session-variable sync in the single shared object both layers read from (e.g. the tenant-context class's own setters), not in route middleware — so every future caller gets both layers automatically instead of needing to remember a second call site per new code path. For any new endpoint that legitimately needs to look up a record before its tenant is known (a public slug, a signed webhook payload), open a narrow, explicit "superadmin"/bypass window for only that initial lookup, then immediately narrow back down to the resolved tenant before any further query. Verify against the real database driver, not just the test suite's driver, whenever RLS or any DB-specific policy is involved.

## LRN-css-var-self-reference-silent-fallback-001
- Date: `2026-09-09`
- Learning: A CSS custom property defined as `--font-sans: var(--font-sans);` (or any self-referential `var()`) is a silent no-op — it never resolves to anything, which makes the whole `font-family` value list it's used in invalid, so the browser ignores that declaration and falls back to an inherited or user-agent default (a generic serif, in this case) with zero console warning or build error. This existed from a scaffold's original bootstrap and affected every page in the app, not just newly-added ones, and was invisible to `tsc`, `eslint`, and a quick screenshot glance (bold sans-ish serif at small sizes reads as "fine" without close inspection) — only `getComputedStyle(element).fontFamily` in a real browser exposed it.
- Control: When wiring a font token through a `@theme`/CSS-variable indirection layer (e.g. Tailwind v4's `@theme inline` mapping a semantic token to a font-loader's generated variable), verify the token actually resolves by checking `getComputedStyle` in a real browser — not just that the font-loader's own variable exists — especially right after scaffolding, before any page has had reason to look at it closely. Treat "the page renders without errors" as insufficient proof that typography tokens are wired correctly.

## LRN-execsync-shell-escaping-of-embedded-code-001
- Date: `2026-09-09`
- Learning: Building a shell command string via string interpolation (e.g. Node's `execSync(\`command --flag="${scriptContainingItsOwnLanguage}"\`)`) is unsafe whenever the embedded content has its own `$`-prefixed syntax — a PHP arrow function `fn($q) => $q->where(...)` embedded inside a double-quoted shell argument gets `$q` expanded by the intermediate shell (to an empty string, since `$q` isn't a shell variable) before the target program ever receives it, silently corrupting the script into something that fails with a confusing downstream error, not an obvious "your shell quoting is wrong" message. This is easy to miss in ad hoc/interactive testing (where the exact same content, entered by hand with the necessary `\$` escaping already muscle-memoried in, works fine) and only surfaces when the *unescaped* form ships in actual source code.
- Control: When a script needs to hand a snippet of another language's code (PHP, Python, SQL, ...) to a subprocess, use the `execFile`/`execFileSync`/`spawn` family with an argv array instead of a single command string — this bypasses the intermediate shell entirely, so nothing in the embedded snippet is reinterpreted. Reserve `exec`/`execSync` (string-command form) for cases with no embedded untrusted-shape content, or where every `$`, backtick, and quote in the interpolated value has been deliberately escaped for that specific shell.

## LRN-tanstack-query-refetch-interval-background-pause-001
- Date: `2026-09-09`
- Learning: TanStack Query's `refetchInterval` defaults `refetchIntervalInBackground` to `false`, silently pausing polling the instant `document.hidden` becomes `true` — no error, no warning, the query just stops refetching. This is easy to miss in normal development (the tab being edited/tested usually stays foregrounded) and easy to miss in review (the option isn't obviously "wrong" to omit, since pausing background polling is a reasonable default for many use cases). It becomes a real, user-facing bug specifically when the flow being polled is one the user is *expected* to background — e.g. a "waiting for payment confirmation" screen where the payment link itself opens in a new tab (`target="_blank"`), which backgrounds the exact tab doing the polling for literally every user who clicks it, not just in a test environment.
- Control: Before shipping a `useQuery`/`refetchInterval` polling loop, ask whether the flow it belongs to can plausibly background the tab as part of normal use (opening a payment link, an OAuth flow, a "check your email" step, anything with an external redirect or new-tab action). If so, set `refetchIntervalInBackground: true` explicitly and verify the polling actually continues with the tab backgrounded — check `document.visibilityState`/`document.hidden` directly in the browser being tested rather than assuming a driven browser tab counts as "foreground" (automation panes are frequently backgrounded from the OS's perspective even while being actively driven).

## LRN-playwright-context-isolation-and-mac-chromium-001
- Date: `2026-09-09`
- Learning: Two Playwright-specific assumptions cost real debugging time this session: (1) each `test()` function gets its own isolated browser context (no shared cookies) by default, and `test.describe.serial` only guarantees execution *order* between tests, not shared *state* — splitting one login-dependent flow into two separate tests silently redirected the second test to the login page, with no error other than a generic locator timeout. (2) The latest `@playwright/test` (1.63.0 at the time) bundles a Chromium build that refuses to install on an older host OS (macOS 13/"mac13") with a hard `ERROR: Playwright does not support chromium on mac13` and no override flag — an older pinned version (1.55.0) still bundled a compatible build.
- Control: Keep any browser interaction that depends on server-set session state (auth cookies, etc.) within a single `test()` function rather than splitting it for readability — split only at points where a fresh, unauthenticated context is actually desired. When Playwright's browser install fails with an OS-support error, don't assume the whole approach is broken — try pinning to a recent-but-not-bleeding-edge version of `@playwright/test` first; the OS-support cutoff moves forward with new releases faster than most host OSes are upgraded.

## LRN-mail-after-transaction-commit-001
- Date: `2026-09-09`
- Learning: A transactional email tied to a DB write (registration confirmation, payment confirmation) must be sent *after* the wrapping `DB::transaction()` returns, never from inside the closure — a slow SMTP handshake or transport failure inside the transaction would hold the row lock open needlessly, and a transaction that later rolls back must never have already emailed the user about something that didn't happen. Separately, an idempotent operation (e.g. `confirmPayment()`, safe to call again on an already-confirmed row) must gate its email on the *transition itself*, not on the row's state after the call returns — checking "is the row confirmed now" can't distinguish a fresh confirmation from a no-op re-confirmation, and a naive unlocked pre-check (`$row->fresh()->status`) to detect the transition introduces a race window between the check and the lock.
- Control: Structure the method as `$result = DB::transaction(function () use (&$transitioned) { ...; $transitioned = true; return $row; })` (capturing the transition flag by reference from *inside* the lock, only on the branch that actually changed something), then send the email after the transaction returns, gated on that flag. This keeps the side effect out of the transaction entirely while still making the "only on real transitions" guarantee race-free.

## LRN-generic-proxy-header-forwarding-001
- Date: `2026-09-09`
- Learning: A generic BFF/proxy route that forwards a backend response by explicitly copying headers (e.g. `headers: { "content-type": contentType }`) forwards *only* the headers it names — adding a new backend feature that depends on a different response header (here, a CSV export's `Content-Disposition: attachment; filename=...`) silently loses that header through the proxy with no error. The frontend feature can still appear to work (a `<a download>` attribute forces a save dialog regardless of `Content-Disposition`), masking the gap — the download happens, just with a generic/wrong filename instead of the meaningful one the backend generated.
- Control: When a new backend endpoint's contract includes a non-default response header, check the proxy layer forwards it by name, not just that a "successful" response arrives client-side. Test by inspecting `response.headers.get(...)` through the full proxy path, not just confirming the download/response happens at all.

## LRN-label-htmlfor-not-automatic-001
- Date: `2026-09-09`
- Learning: A `<Label>` component wrapping a plain `<label>` element does not automatically associate itself with a sibling `<Input>`/`<Textarea>` — omitting `htmlFor` (matching the input's `id`) compiles fine, renders fine, and looks correct in a screenshot, but is both a real accessibility bug (a screen reader can't announce the field's purpose) and breaks any tooling that finds form fields by their label text (Playwright's `getByLabel`, browser autofill, clicking a label to focus its input). This is easy to miss across a large form built by copy-pasting a `<div><Label>X</Label><Input .../></div>` pattern for many similar fields, especially in a dynamic/repeating list where each row needs a *unique* id, not just any id.
- Control: Every `<Label>` needs an explicit `htmlFor` matching its input's `id`. In a repeating list, key both by the row index (or a stable row id) so each row's fields get unique, distinct ids. Treat a `page.getByLabel(...)` failure in a new Playwright test as a signal to fix the markup's label association, not to switch to a different, less-meaningful locator.

## LRN-verify-state-transition-ui-exists-001
- Date: `2026-09-09`
- Learning: A CRUD resource can have a complete-looking API (create, read, update, list) and a complete-looking read-side UI (a table, a detail page, an edit form) while still missing the actual control to trigger an important state transition the rest of the feature depends on — here, events could be created, listed, and have every other field edited through the dashboard, but nothing in the UI could flip `status` from `draft` to `published`, even though the entire public-facing landing page feature is meaningless without that transition. The gap was invisible in isolation (every existing screen "worked") and only surfaced organically while building an unrelated feature (an E2E test needed to view a public page).
- Control: When reviewing a feature area for completeness (not just when something else surfaces the gap by accident), explicitly enumerate the resource's state machine (draft → published, pending → confirmed, etc.) and confirm the UI has a control for every transition an end user is expected to trigger themselves — not just the ones exercised by whatever screens happen to already exist.
