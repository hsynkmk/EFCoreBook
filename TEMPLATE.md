# Topic Template & Contributor Guide

Every topic file in this course follows the **same shape**. That consistency is the backbone of a
course (vs a pile of notes): once you've read two topics, you know exactly where to look for the
intuition, the C#, the SQL EF emits, or the practice in every other one.

Copy the skeleton below when adding a topic. Keep the section order and the emoji headers — they
double as visual anchors when skimming.

---

## The Sections (in order)

1. **`# Title: <one-line intent>`** — the title names it; the subtitle is the one-line answer to
   "what does this give me?".
2. **`## 🧠 Intuition`** — analogy / mental model. **No code.** If a smart beginner wouldn't
   follow it, simplify.
3. **`## 🎯 The Problem`** — a concrete scenario and the *painful before* code. Make the reader
   *feel* the pain the feature relieves (slow query, N+1, runtime error, wrong SQL, etc.).
4. **`## 📐 How It Works`** — the mechanism. A diagram (Mermaid) where it earns its keep.
5. **`## 💻 C# Implementation`** — entity config + DbContext setup + LINQ usage (the *after*).
   Idiomatic, **EF Core 10** by default.
6. **`## ⚡ Generated SQL`** — the SQL EF actually emits (or how to capture it). **Required** for
   query-heavy topics; skip for pure config topics if it adds nothing.
7. **`## ⚖️ Trade-offs / Performance`** — honest. Numbers > adjectives where possible.
8. **`## ✅ When to Use / 🚫 When to Avoid`** — including how the feature is *misused* (its
   anti-pattern failure mode).
9. **`## 🆕 Latest EF Notes (8 / 9 / 10)`** — version-specific differences. Use callouts like
   *"New in EF 10"*, *"Requires EF 8+"*, *"Behavior changed in EF 9"*.
10. **`## 🌍 Real-World & Production Tips`** — gotchas, what to log, what to monitor.
11. **`## 🎯 Practice (with full solutions)`** — 2–3 refactoring/scenario exercises (easy → hard),
    each with a complete C# solution and *why it's better*. The solutions live **inside this repo**
    — no clicking out required.
12. **`## ✅ Key Takeaways`** — tight bullet summary, then **self-check questions**.
13. **Navigation footer** — `◀ Prev` · `▲ Module index` · `▶ Next` relative links.

> **Foundations files** (no real "before") use a lighter variant: intuition → walkthrough → practice
> → takeaways.

---

## Conventions

- **Audience:** a C# developer who can build a basic app but is new (or rusty) on EF Core.
- **Target version:** **EF Core 10** is the default. Always show the EF 10 idiom; call out EF 8/9
  alternatives or behavior changes explicitly.
- **Database provider:** **SQL Server primary** (`Microsoft.EntityFrameworkCore.SqlServer`). Add
  PostgreSQL (Npgsql) / SQLite / Cosmos callouts where the behavior diverges.
- **Async by default** — examples use `async`/`await` and `*Async` overloads.
- **Cross-link liberally.** Use relative links like
  `[Indexes](01-Modeling-Data/07.Indexes-and-Constraints.md)` (add `../` across modules).
- **Diagrams:** Mermaid blocks render on GitHub. Keep them legible.
- **Tone:** direct, encouraging, no fluff. Short sentences. Goal is *understanding then applying*.
- **Always show the "before."** The pain motivates the feature.

---

## Skeleton (copy me)

```markdown
# <Topic>: <one-line intent>

## 🧠 Intuition
<analogy / mental model — no code>

## 🎯 The Problem
<scenario + painful "before" code>

## 📐 How It Works
<concept, optional Mermaid>

## 💻 C# Implementation
\`\`\`csharp
<entity config + DbContext + LINQ usage>
\`\`\`

## ⚡ Generated SQL
\`\`\`sql
<the SQL EF emits>
\`\`\`

## ⚖️ Trade-offs / Performance
**Pros:** ...  **Cons:** ...

## ✅ When to Use / 🚫 When to Avoid

## 🆕 Latest EF Notes (8 / 9 / 10)
- **EF 8:** ...
- **EF 9:** ...
- **EF 10:** ...

## 🌍 Real-World & Production Tips

## 🎯 Practice (with full solutions)
### 1. <Refactor scenario> — `Easy`
**Smelly code / scenario:** ...
**Task:** ...
**Solution:**
\`\`\`csharp
...
\`\`\`
**Why it's better:** ...

## ✅ Key Takeaways
- ...

**Self-check:** <2–3 questions>

---
◀ [Prev](.) · ▲ [Module index](./README.md) · ▶ [Next](.)
```
