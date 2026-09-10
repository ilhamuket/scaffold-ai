# DECISION_LOG

## Usage
Record decisions that should persist across sessions.

## Template
### [DATE] Decision Title
- Status: proposed / approved / rejected / deprecated
- Context:
- Decision:
- Reason:
- Consequence:

### 2026-09-07 LumiRace Stack Selection
- Status: `approved` (founder confirmed Next.js for the public frontend on 2026-09-07, resolving the one open stack decision)
- Context: Founder confirmed LumiRace (Luminos Karya) will be built fresh rather than adapting the existing single-tenant reference codebases (`btr-backend`, `bbir-frontend`), with explicit priorities "lebih rapi, lebih aman, lebih cepat performanya" and an infra-only budget (server + domain).
- Decision: Laravel 12 **running on Laravel Octane (Swoole), API-only (no Filament/Blade admin)** + PostgreSQL (single-DB multi-tenancy via `organizer_id` scoping + Postgres Row-Level Security) + Redis (cache/queue) for `development/lumirace-backend/`; **one Next.js + TypeScript + Tailwind + shadcn/ui app** for `development/lumirace-frontend/`, covering both the public landing pages/registration/payment (`(marketing)` route group) and the organizer + super-admin dashboard (`(dashboard)` route group, Sanctum-authenticated) with a fully custom design system — no generic admin-generator UI; S3-compatible object storage (e.g. Cloudflare R2); Jenkins CI/CD (reusing the pattern already proven in both reference repos).
- Reason: Postgres RLS gives defense-in-depth for tenant isolation ("lebih aman"); Redis-backed queues speed up bib generation/email/webhook processing ("lebih cepat"); Octane keeps the app booted in memory across requests, closing most of the raw-throughput gap with Node/Go without losing Laravel — founder explicitly questioned whether Laravel could really be "fast enough," and Octane is the concrete answer rather than a language switch. Filament was dropped because founder found its generated admin-panel look "murahan/gratisan" (generic/cheap-looking) and wants full custom UI — moving the entire UI layer (public + admin) into one Next.js/shadcn app gives full design control and a single consistent, premium-feeling design system across marketing and dashboard, instead of splitting the product visually between a PHP-rendered generic admin and a custom React public site. shadcn/ui was chosen over a pre-styled admin kit (e.g. Refine's default themes) specifically because it ships unstyled primitives — nothing to "de-genericize" later.
- Consequence: Dropping Filament trades away its free auto-generated CRUD scaffolding — the organizer and super-admin dashboards (tables, forms, filters) must now be hand-built in React instead of generated. This is a real, acknowledged increase in V1 frontend build effort in exchange for the premium/custom look founder wants; TanStack Table/Query is the recommended toolkit to keep that build effort reasonable. Next.js and Octane remain additive to the team's existing Laravel/Tripay knowledge, not a full rewrite. Founder approved this reasoning on 2026-09-07 ("gas aja sesuai rekomendasi kamu", then "jangan pakai filament ... saya ingin bagus dengan full ui custom").
