# API Specs Folder

Store feature-level API specifications here.

## Required files per feature

- `[feature]-openapi.yaml` for machine-readable contract
- `[feature]-api-spec.md` for implementation notes, examples, and edge cases

## Example

- `auth-login-openapi.yaml`
- `auth-login-api-spec.md`

## Policy

- API spec is finalized after frontend contract is validated.
- Backend implementation must follow this folder as source of truth.
- For feature additions, update only impacted API specs.
