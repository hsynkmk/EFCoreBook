# Module 02 — Querying

> Get the *right* SQL, fast. Bad LINQ is the #1 cause of "EF is slow" complaints.

EF is a translator: your LINQ becomes SQL. Senior EF developers think in *both* worlds at once.
This module walks you through every form of query EF supports, with the SQL each one emits.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Basic Queries](01.Basic-Queries.md) | LINQ to entities, projections, filtering, ordering, async |
| 02 | [Advanced Querying](02.Advanced-Querying.md) | Grouping, set ops, **EF 10 LeftJoin/RightJoin**, `EF.Functions` |
| 03 | [Loading Strategies](03.Loading-Strategies.md) | Eager (`Include`) / explicit / lazy + lazy-loading proxies |
| 04 | [Split Queries](04.Split-Queries.md) | Avoid cartesian explosion with `AsSplitQuery` |
| 05 | [Raw SQL Queries](05.Raw-SQL-Queries.md) | `FromSql`, `ExecuteSql`, **EF 8+ `SqlQuery<T>`** for primitives |
| 06 | [Compiled & Precompiled Queries](06.Compiled-and-Precompiled-Queries.md) | Reuse plans; **EF 9 MSBuild compiled model**; AOT |
| 07 | [Query Tags & Diagnostics](07.Query-Tags-and-Diagnostics.md) | `TagWith` + capturing SQL in logs |
| 08 | [No-Tracking & Identity Resolution](08.No-Tracking-and-Identity-Resolution.md) | When to drop tracking; `AsNoTrackingWithIdentityResolution` |

## After this module you can

- Read the SQL EF generates and predict it from LINQ.
- Pick the right loading strategy (and avoid N+1).
- Use raw SQL safely when LINQ can't express what you need.
- Tag, log, and diagnose any query in production.

---
◀ Prev: [01 — Modeling Data](../01-Modeling-Data/README.md) · ▲ [Course home](../README.md) · ▶ Next: [03 — Saving & Concurrency](../03-Saving-and-Concurrency/README.md)
