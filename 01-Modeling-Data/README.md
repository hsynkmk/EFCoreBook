# Module 01 — Modeling Data

> The biggest, most important module. Most senior EF depth lives here.

Modeling decisions outlive any single query. A solid model makes queries simple and migrations
painless; a sloppy one bleeds into every layer forever. This module includes everything new and
exciting in EF Core 8/9/10 — **complex types**, **JSON columns**, **primitive collections**,
**HierarchyId**, **vector data**, and **named query filters**.

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [DbContext and Entities](01.DbContext-and-Entities.md) | Lifecycle, DI, `OnModelCreating` |
| 02 | [Configuring the Model](02.Configuring-the-Model.md) | Data annotations vs Fluent API vs `IEntityTypeConfiguration` |
| 03 | [Relationships](03.Relationships.md) | 1-1, 1-N, N-N skip nav, shadow FKs, delete behaviors |
| 04 | [Owned Entities & Complex Types](04.Owned-Entities-and-Complex-Types.md) | The difference; EF 10 optional + JSON mapping |
| 05 | [Value Conversions](05.Value-Conversions.md) | Custom mappings; `DateOnly`/`TimeOnly` (EF 8+) |
| 06 | [Field Mapping & Shadow Properties](06.Field-Mapping-and-Shadow-Properties.md) | Backing fields, metadata without entity props |
| 07 | [Indexes & Constraints](07.Indexes-and-Constraints.md) | Unique, composite, filtered, covering |
| 08 | [Global & Named Query Filters](08.Global-and-Named-Query-Filters.md) | Soft delete + multi-tenancy; **EF 10 named filters** |
| 09 | [Temporal Tables](09.Temporal-Tables.md) | Built-in history (SQL Server) |
| 10 | [JSON Columns & Primitive Collections](10.JSON-Columns-and-Primitive-Collections.md) | **EF 8** intro → **EF 9** read-only → **EF 10** SQL 2025 `json` type |
| 11 | [HierarchyId & Tree Data](11.HierarchyId-and-Tree-Data.md) | SQL Server hierarchies (EF 8+) |
| 12 | [Vector Data for AI](12.Vector-Data-for-AI.md) | **EF 10** vector type + `VECTOR_DISTANCE()` + Cosmos vector search |

## After this module you can

- Design entities and relationships that map to clean, correct schemas.
- Choose between owned entities, complex types, and JSON columns intentionally.
- Apply modern mappings (primitive collections, `DateOnly`, HierarchyId, vectors).
- Implement multi-tenancy / soft delete cleanly with named query filters.

---
◀ Prev: [00 — Foundations](../00-Foundations/README.md) · ▲ [Course home](../README.md) · ▶ Next: [02 — Querying](../02-Querying/README.md)
