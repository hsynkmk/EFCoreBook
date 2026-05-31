# Entity Framework Core — A Complete Course (EF Core 10)

> **Read this repo top to bottom and you'll go from "what is an ORM?" to senior-level EF Core
> fluency** — including everything new in **EF Core 8, 9, and 10**.

This isn't a list of pages — it's an **ordered curriculum**. The folders are numbered `00 → 09`.
Read them in order and each topic only relies on what came before. Every file starts with plain-
English intuition, shows the *painful before code*, then the clean fix in modern C# + EF Core 10,
the actual SQL EF emits, and ends with **refactoring exercises solved in full**.

**Target:** EF Core **10** (LTS, Nov 2025 → Nov 2028; requires .NET 10). EF 8 / 9 differences are
called out inline so EF 8 LTS users can follow along.
**Provider:** SQL Server primary, with PostgreSQL (Npgsql), SQLite, and Cosmos callouts.

🎯 **In a hurry before an interview?** → [Interview Cheat Sheet](INTERVIEW_CHEATSHEET.md).
🧭 **New to EF?** → [What Is EF Core](00-Foundations/01.What-Is-EF-Core.md).
🆕 **Just upgrading?** → [What's New in EF Core 10](08-Whats-New/01.EF-Core-10.md) or the
[Version Compatibility Cheatsheet](08-Whats-New/04.Version-Compatibility-Cheatsheet.md).

---

## 🗺️ The Curriculum

| # | Module | What you'll learn | Why it's here |
|---|--------|-------------------|---------------|
| **00** | [Foundations](00-Foundations/README.md) | What EF Core is, setup, first CRUD, providers | The lens for everything after |
| **01** | [Modeling Data](01-Modeling-Data/README.md) | DbContext, relationships, **complex types**, value conversions, indexes, named filters, temporal, **JSON columns**, **primitive collections**, **HierarchyId**, **vector data for AI** | Where senior depth lives |
| **02** | [Querying](02-Querying/README.md) | LINQ basics → advanced, EF 10 **LeftJoin/RightJoin**, loading strategies, split queries, raw SQL + `SqlQuery<T>`, **precompiled queries**, tags | Get the *right* SQL fast |
| **03** | [Saving & Concurrency](03-Saving-and-Concurrency/README.md) | Change tracking, transactions, optimistic concurrency, cascade delete, **ExecuteUpdate/Delete**, interceptors | Write data safely and quickly |
| **04** | [Migrations & Schema](04-Migrations-and-Schema/README.md) | Migrations basics → production, versioning, design-time | Evolve your schema without pain |
| **05** | [Performance](05-Performance/README.md) | Fundamentals, **DbContext pooling**, compiled-queries perf, bulk ops, diagnosing slow queries | What separates "works" from "scales" |
| **06** | [Production](06-Production/README.md) | DI, configuration, logging & diagnostics, resilience, security | Ship with confidence |
| **07** | [Testing](07-Testing/README.md) | Strategy, SQLite / InMemory unit tests, Testcontainers integration tests | Real coverage without flakiness |
| **08** | [What's New](08-Whats-New/README.md) | EF 10 / EF 9 / EF 8 deep dives + compatibility cheatsheet | Stay on top of every release |
| **09** | [Beyond](09-Beyond/README.md) | Anti-patterns, EF vs Dapper vs raw SQL, study plan | Use it wisely |

---

## 🧭 How to Study This

1. **Don't skip Foundations.** Without "what is a `DbContext`" and the provider model, everything
   later feels arbitrary.
2. **Feel the pain first.** Each file opens with painful *before* code — read it slowly. The
   feature only makes sense against the problem it solves.
3. **Read the Generated SQL.** EF is a layer over SQL — knowing what it emits is half of senior
   EF fluency. Every query-heavy file shows it.
4. **Do the 🎯 Practice.** Each topic ends with **refactoring exercises**. Attempt before peeking.
5. **Use the self-check questions** as your "ready to move on?" gate.
6. **Watch the 🆕 Latest EF Notes** in each file — that's where modern features live.

A week-by-week roadmap lives in the [Study Plan](09-Beyond/03.Study-Plan.md).

---

## 📐 How Each Topic Is Structured

Every file follows the same shape — intuition → the painful *before* → how it works → C# (the
*after*) → **generated SQL** → trade-offs → when to use/avoid → **latest EF (8/9/10) notes** →
production tips → **refactoring practice with solutions** → takeaways. See [TEMPLATE.md](TEMPLATE.md).

> 💡 The golden rule of this repo: **EF Core is a leaky abstraction over SQL, in a good way.**
> Learn the SQL it emits and you control the performance. Treat it as a black box and you'll be
> bitten.

---

## 🤝 Contributing

PRs welcome. New content must follow [TEMPLATE.md](TEMPLATE.md) so the learning curve stays
consistent. Open an issue first for anything large.
