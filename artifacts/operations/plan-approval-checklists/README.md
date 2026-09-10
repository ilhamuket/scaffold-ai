# Plan Approval Checklists

Store one checklist artifact here for every scoped change request that adds, changes, refactors, or creates a feature/module.

Required path pattern:
- `artifacts/operations/plan-approval-checklists/[task-id]-[context-name]-plan-approval.md`

Required source template:
- `templates/plan_approval_checklist_template.md`

Minimum purpose of each checklist:
- prove the matching plan file already exists in root `plan/`
- record founder review status
- record explicit approval reference
- state whether build/coding is still blocked or already allowed

If the matching checklist artifact is missing, implementation must remain blocked even when a plan file already exists.
