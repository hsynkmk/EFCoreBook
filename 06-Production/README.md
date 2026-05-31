# Module 06 — Production

> Everything between "the code works on my machine" and "I sleep through the on-call rotation."

## Contents

| # | Topic | One-liner |
|---|-------|-----------|
| 01 | [Dependency Injection](01.Dependency-Injection.md) | `AddDbContext` lifetimes, scoping, factory patterns |
| 02 | [Configuration & Connection Strings](02.Configuration-and-Connection-Strings.md) | User secrets, Key Vault, env-specific |
| 03 | [Logging & Diagnostics](03.Logging-and-Diagnostics.md) | `LogTo`, `EnableSensitiveDataLogging`, query tags, EventCounters |
| 04 | [Error Handling & Resilience](04.Error-Handling-and-Resilience.md) | `EnableRetryOnFailure`, transient errors, deadlock retries |
| 05 | [Security Best Practices](05.Security-Best-Practices.md) | Parameterization, least-priv, encryption, audit, secrets |

## After this module you can

- Wire EF into a real DI container without lifetime bugs.
- Get the right logs in dev, the right logs in prod, never leak secrets.
- Handle transient and deadlock errors automatically.
- Pass a security review with a straight face.

---
◀ Prev: [05 — Performance](../05-Performance/README.md) · ▲ [Course home](../README.md) · ▶ Next: [07 — Testing](../07-Testing/README.md)
