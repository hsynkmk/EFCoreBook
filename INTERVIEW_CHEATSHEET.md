# 🚀 EF Core Interview Cheat Sheet

**Read this the morning of the interview.** Every concept compressed. Targets **EF Core 10** with
EF 8/9 notes. Drill into the [full course](README.md) if a row feels rusty.

> 💡 The #1 thing interviewers probe: **do you understand that EF emits SQL, and can you control
> it?** Always be ready to say what SQL a LINQ query generates and how you'd diagnose a slow one.

---

## 1. The mental model (say this out loud)
EF Core is an **ORM**: LINQ + entities + **change tracking** + **migrations**, translating to SQL
via a **provider**. It's a *leaky abstraction over SQL — on purpose*. You ignore SQL until you
can't; seniors always can read it.

---

## 2. DbContext & lifetimes
- `DbContext` = **unit of work** + change tracker + `DbSet<T>`. **Scoped, short-lived, NOT
  thread-safe.**
- `AddDbContext` (scoped, default) · `AddDbContextPool` (perf, stateless context) ·
  `AddDbContextFactory` (background/parallel/Blazor).
- **Captive dependency** = singleton holding a scoped context → the classic bug. Fix: inject
  `IDbContextFactory<T>`.

---

## 3. Querying — the perf fundamentals
| Habit | Why |
|-------|-----|
| `AsNoTracking()` on reads | no snapshots — biggest one-line win |
| Project to DTOs (`Select`) | fewer columns, no materialization |
| Filter/sort/paginate **before** `ToListAsync` | DB does the work |
| Keyset pagination (`Where(id > last)`) | beats `Skip` for deep pages |
| `Include` / projection / `AsSplitQuery` | kill **N+1** & cartesian explosion |

```csharp
var dtos = await ctx.Blogs.AsNoTracking()
    .Where(b => b.Views > 1000)
    .Select(b => new BlogDto(b.Id, b.Title))
    .ToListAsync();
```

---

## 4. Loading strategies
- **Eager** `Include`/`ThenInclude` — one query (LEFT JOIN). Two collections → **`AsSplitQuery`**.
- **Explicit** `ctx.Entry(x).Collection(...).LoadAsync()` — load on demand.
- **Lazy** (proxies) — easy, but the #1 source of **N+1**. Off by default; keep it off.
- **Projection** often beats `Include`.

---

## 5. Saving & change tracking
- States: **Added / Unchanged / Modified / Deleted / Detached.**
- EF emits **only changed columns** (thanks to the snapshot).
- `Update(entity)` writes **every** column — for partial, mutate-tracked or `ExecuteUpdate`.
- `AsNoTracking` + mutate + `SaveChanges` = **does nothing** (entity not tracked).

---

## 6. Bulk operations (EF 7+, big in EF 10)
```csharp
await ctx.Orders.Where(o => o.Old).ExecuteUpdateAsync(s => s.SetProperty(o => o.Status, "Archived"));
await ctx.Sessions.Where(s => s.Expired).ExecuteDeleteAsync();
```
One SQL statement, no entities loaded, no tracker. **EF 10:** non-expression lambdas (conditional
sets) + JSON-property updates (`JSON_MODIFY`). ⚠️ bypasses SaveChanges interceptors; reload stale
tracked entities.

---

## 7. Transactions & concurrency
- `SaveChanges` is **implicitly transactional**. Open explicit transactions for multi-step work;
  **savepoints** for partial rollback.
- With `EnableRetryOnFailure`, wrap explicit transactions in
  `Database.CreateExecutionStrategy().ExecuteAsync(...)` and make them idempotent.
- **Optimistic concurrency:** `[Timestamp] byte[] RowVersion;` → `DbUpdateConcurrencyException` →
  resolve (client-wins / store-wins / merge). Counters → atomic `ExecuteUpdate`.

---

## 8. Migrations
- `migrations add` → **review** → `database update`. EF diffs the **model snapshot**, not the DB.
- **Prod:** never migrate on startup (races). Use `migrations script --idempotent` or **bundles**
  as a gated step.
- **Zero downtime:** **expand-contract** (add nullable → backfill → enforce/drop later).
- **EF 10** applies migrations **per-step** (reverted EF 9's single transaction).

---

## 9. Modeling (EF 8/9/10 features interviewers love)
| Feature | Version | One-liner |
|---------|---------|-----------|
| Complex types | EF 8 | value objects, no key (Address) |
| Primitive collections | EF 8 | `List<string>` → JSON column, LINQ-queryable |
| JSON columns | EF 8 | `OwnsOne(...).ToJson()` |
| HierarchyId | EF 8 | SQL Server tree data |
| DateOnly/TimeOnly | EF 8 | native `date`/`time` mapping |
| `SqlQuery<T>` | EF 8 | raw SQL → primitives/DTOs |
| Compiled model (MSBuild) | EF 9 | faster cold start |
| `UseAzureSql` | EF 9 | Azure-tuned SQL |
| **Vector data** | EF 10 | `vector(n)` + `VECTOR_DISTANCE` (AI/RAG) |
| **SQL 2025 `json` type** | EF 10 | native JSON column |
| **LeftJoin/RightJoin** | EF 10 | clean LINQ joins |
| **Named query filters** | EF 10 | multiple filters, selective bypass |

---

## 10. Production
- **Connection strings** = secrets → user secrets (dev), Key Vault / **Managed Identity** (prod).
  Never in source.
- **`EnableSensitiveDataLogging` = DEV ONLY** (logs PII).
- **`TagWith("...")`** every important query; OpenTelemetry for traces; health checks for the DB.
- **`EnableRetryOnFailure`** for cloud DBs. **Project to DTOs** so APIs don't leak columns.

---

## 11. Testing
- **Don't mock `DbSet`.** **Avoid the InMemory provider** (it doesn't enforce SQL semantics).
- **SQLite in-memory** for fast, real-relational unit tests (keep the connection open!).
- **Testcontainers + real SQL Server** for provider-specific features (JSON/temporal/vector) and
  migrations.

---

## 12. EF vs Dapper vs Raw
- **EF** — domain, CRUD, writes, migrations, multi-provider.
- **Dapper** — hot read paths, complex reporting SQL.
- **Raw / SqlBulkCopy** — millions of rows, drivers.
- Mix them: run **Dapper on EF's connection** (`ctx.Database.GetDbConnection()`).

---

## 13. Anti-patterns to name on sight
Captive DbContext · N+1 · materialize-then-filter · tracking read-only queries · `SaveChanges` in a
loop · generic Repository-over-EF · returning entities from APIs · `EnableSensitiveDataLogging` in
prod · string-concatenated `FromSqlRaw` · migrate-on-startup · async-over-sync (`.Result`).

---

## 14. Likely interview questions
1. **"What SQL does this LINQ generate?"** → describe the `SELECT`/`WHERE`/`JOIN`; mention
   `ToQueryString()`.
2. **"How do you fix N+1?"** → `Include` / projection / `AsSplitQuery`.
3. **"DbContext lifetime?"** → scoped, not thread-safe; captive-dependency trap; factory fix.
4. **"`IQueryable` vs `IEnumerable`?"** → `IQueryable` translates to SQL; `IEnumerable` runs in
   memory. Don't materialize early.
5. **"How do you do optimistic concurrency?"** → `RowVersion` + handle
   `DbUpdateConcurrencyException`.
6. **"Migrations in production?"** → idempotent scripts/bundles, gated step, expand-contract.
7. **"When NOT to use EF?"** → hot single query (Dapper), heavy reporting (SQL), bulk movement
   (SqlBulkCopy).
8. **"What's new in EF 10?"** → vector data, SQL 2025 JSON type, LeftJoin/RightJoin, named filters,
   ExecuteUpdate improvements.

---

## 15. 30-second talking point (memorize)
> "EF Core is an ORM that turns LINQ into SQL, tracks changes, and manages schema with migrations —
> a leaky abstraction over SQL, by design. The skill isn't memorizing APIs; it's **knowing the SQL
> EF emits**, choosing tracking/loading/bulk strategies deliberately, diagnosing queries with tags
> and execution plans, and knowing when to drop to Dapper or raw SQL. EF 10 (LTS, .NET 10) adds
> vector data, the SQL 2025 JSON type, LeftJoin/RightJoin, and named query filters."

---
▲ [Course home](README.md) · 🧭 [Foundations](00-Foundations/README.md) · 🆕 [What's New in EF 10](08-Whats-New/01.EF-Core-10.md)
