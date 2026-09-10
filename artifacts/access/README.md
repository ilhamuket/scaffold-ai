# artifacts/access

Use this document as the single source of truth for local, development, and demo access details.

Allowed here:
- running app URLs
- local or demo usernames or emails
- local or demo passwords only when the founder explicitly approves storing them in the repository
- notes about where an account comes from, such as manual registration, seed data, Docker bootstrap, or fixture setup

Do not store here:
- production credentials
- personal passwords
- API keys, tokens, private certificates, or secret-manager values
- any credential that should remain outside the repository

## Running URLs

| surface | environment | url | notes |
| --- | --- | --- | --- |
| app | local | `fill-me` | `example: https://localhost:8443` |
| api | local | `fill-me` | `example: https://localhost:8443/api` |
| admin | local | `fill-me` | `optional` |

## Access Accounts

| account_label | environment | role | username_or_email | password | source | status | notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `fill-me` | `local` | `admin` | `fill-me` | `fill-me or external-reference` | `manual-register / seed / docker / fixture` | `active` | `use external reference instead of plaintext when possible` |

## Retrieval Notes

- Preferred pattern: keep only local or demo credentials here.
- If a password should not be committed, replace it with a retrieval note such as `see local .env`, `generate via seed command`, or `create manually through /auth/register`.
- Update this document whenever the active local URL, demo account, or bootstrap flow changes.
