# Module 05 — Performance

> What separates "works in dev" from "scales in production." The lessons here pay back ×100.

EF Core is fast *when used right*. Most "EF is slow" complaints trace to a handful of patterns —
tracking when read-only, N+1, late filtering, missing pooling, untuned bulk paths. Fix these and
EF often matches hand-tuned Dapper code.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Performance Fundamentals](01.Performance-Fundamentals.md) | Tracking, projection, N+1, batching, async |
| 02 | [DbContext Pooling](02.DbContext-Pooling.md) | `AddDbContextPool`; reuse cost; pitfalls |
| 03 | [Compiled & Precompiled Queries](03.Compiled-and-Precompiled-Queries.md) | When the plan cache isn't enough |
| 04 | [Bulk Operations Performance](04.Bulk-Operations-Performance.md) | When to leave tracked entities for `ExecuteUpdate`/`ExecuteDelete` |
| 05 | [Diagnosing Slow Queries](05.Diagnosing-Slow-Queries.md) | Query tags, `LogTo`, sensitive-data logging, profilers |

## After this module you can

- Spot the most common EF perf anti-patterns at a glance.
- Set up DbContext pooling without breaking lifetime assumptions.
- Decide when to compile a query and when EF's plan cache is enough.
- Diagnose a slow query end-to-end and prove the fix.

---
◀ Prev: [04 — Migrations & Schema](../04-Migrations-and-Schema/README.md) · ▲ [Course home](../README.md) · ▶ Next: [06 — Production](../06-Production/README.md)
