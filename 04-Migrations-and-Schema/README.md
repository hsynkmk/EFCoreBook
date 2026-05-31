# Module 04 — Migrations & Schema

> Evolve your schema without downtime, mystery, or surprises in production.

Migrations look simple in tutorials and explode in production. This module focuses on the parts
that bite real teams: idempotent scripts, multi-environment promotion, design-time wiring, and
versioning strategies for breaking changes.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Migrations Basics](01.Migrations-Basics.md) | `dotnet ef`, generating, applying, rolling back |
| 02 | [Migrations in Production](02.Migrations-in-Production.md) | Idempotent scripts, bundles, zero-downtime patterns |
| 03 | [Versioning & Schema Evolution](03.Versioning-and-Schema-Evolution.md) | Backwards-compatible changes, expand-contract |
| 04 | [Design-Time Configuration](04.Design-Time-Configuration.md) | `IDesignTimeDbContextFactory`, multi-provider setups |

## After this module you can

- Add, apply, and revert migrations safely.
- Generate idempotent SQL bundles for CI/CD.
- Roll out breaking schema changes with expand-contract migrations.
- Configure design-time so EF tooling works for any environment.

---
◀ Prev: [03 — Saving & Concurrency](../03-Saving-and-Concurrency/README.md) · ▲ [Course home](../README.md) · ▶ Next: [05 — Performance](../05-Performance/README.md)
