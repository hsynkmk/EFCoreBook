# Module 03 — Saving & Concurrency

> Write data safely, atomically, and quickly — even when other writers fight you for it.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Change Tracking](01.Change-Tracking.md) | Entity states, the change tracker, gotchas |
| 02 | [Transactions](02.Transactions.md) | Implicit, explicit, savepoints, `TransactionScope` |
| 03 | [Concurrency Handling](03.Concurrency-Handling.md) | Optimistic concurrency, `rowversion`, conflict resolution |
| 04 | [Cascade Delete](04.Cascade-Delete.md) | Delete behaviors + soft delete via named filters |
| 05 | [Bulk Operations](05.Bulk-Operations.md) | `ExecuteUpdate`/`ExecuteDelete` — **EF 10 non-expression lambdas + JSON support** |
| 06 | [Interceptors & SaveChanges Hooks](06.Interceptors-and-SaveChanges-Hooks.md) | Cross-cutting concerns: auditing, soft delete, outbox |

## After this module you can

- Reason about what EF will do at `SaveChanges()`.
- Run multi-step writes atomically with explicit transactions and savepoints.
- Handle concurrency conflicts deliberately, not by accident.
- Replace N round-trips with one server-side `ExecuteUpdate`/`ExecuteDelete`.
- Hook into save/commit with interceptors for auditing and the outbox pattern.

---
◀ Prev: [02 — Querying](../02-Querying/README.md) · ▲ [Course home](../README.md) · ▶ Next: [04 — Migrations & Schema](../04-Migrations-and-Schema/README.md)
