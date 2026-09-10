# Existing Project Intake

Use `templates/existing_project_intake_template.md` as the working structure.

## Status
- created_at: `2026-04-25T23:16:50+07:00`
- updated_at: `2026-04-26T21:42:16+07:00`
- status: `pending_target_repo`
- task_id: `TASK-20260425-001`
- runtime: `codex`
- resume_safe: `yes`

## Objective
- Prepare the intake structure for a future contributor repository while making it clear that no target project has been audited yet.

## Project Summary
- Product or system name: `pending_target_repo`
- Short description: `The scaffold is ready to onboard an existing or inherited project, but the target repository is not attached yet.`
- Primary users: `founder, AI runtimes, future contributor or maintainer`
- Current business goal: `Keep the scaffold ready for safe intake before planning or implementation.`

## Repository And Ownership
- Repo path or URL: `pending_target_repo`
- Known owner or original team: `unknown_until_repo_available`
- Deployment ownership: `unknown_until_repo_available`
- Environment access status: `unknown_until_repo_available`

## Current Stack
- Frontend framework: `not_selected`
- Backend framework: `not_selected`
- Database: `not_selected`
- Package manager: `not_selected`
- Testing stack: `not_selected`
- Infra or deployment notes: `not_selected`
- Mobile framework: `not_selected`
- Flutter project status: `not_audited`
- Flutter intake checklist: `artifacts/flutter/FLUTTER_INTAKE_CHECKLIST.md`

## Current Development Route
- Architecture style: `not_selected`
- Frontend root: `not_selected`
- Backend root: `not_selected`
- Shared contracts root: `not_selected`
- Other important folders: `not_selected`

## Major Modules
- `pending_target_repo`

## Existing Constraints
- Do not select frameworks, database, package manager, deployment route, or implementation roots before the target repository is available.
- Do not bootstrap a new application inside `development/` as a substitute for the target project.
- Keep all official planning, build, QA, and release gates blocked until intake and impact scan have real evidence.

## Known Risks
- Mistaking scaffold readiness for completed project intake.
- Inventing stack or route facts without a repository audit.
- Starting implementation before a scoped change and impacted artifacts are known.

## Data To Collect When Target Repo Is Available
- Repository path or URL and ownership context.
- Product summary, current users, and current business goal.
- Frontend, backend, database, package manager, test stack, and deployment details.
- Major routes, modules, jobs, integrations, and important folders.
- Known inherited constraints, broken areas, release risks, and environment access status.
- First feature, bugfix, redesign, migration, refactor, or cleanup slice to impact-scan.

## Flutter Data To Collect When Applicable
- `pubspec.yaml`, Flutter SDK constraint, and Dart SDK constraint.
- Flutter app root, package roots, entrypoints, and platform folders.
- State management, routing, dependency injection, API/data layer, persistence, theming, localization, and environment/flavor patterns.
- Platform targets and native integrations.
- Unit, widget, integration, golden, analyzer, CI, and smoke test commands.
- Android/iOS/web/desktop release route, versioning, signing status, store ownership, and rollback path.
- Flutter-specific risks, known failing tests, dependency risks, and environment gaps.

## Recommended Next Step
- Attach or identify the target contributor repository, then run `I1 Existing Project Intake` as a read-only audit before any implementation.
