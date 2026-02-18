# Clean Code — Agent Skill

> Distilled from *Clean Code: A Handbook of Agile Software Craftsmanship* by Robert C. Martin (2008).
> Condensed into actionable reference material for AI coding agents, with 2026 agentic framing.

## When to Use This Skill

Load this skill (or specific chapters) when:
- Writing new code and need quality heuristics
- Reviewing or refactoring existing code
- Naming variables, functions, or classes
- Designing function signatures or class hierarchies
- Writing or improving tests
- Debugging code smells
- Self-checking generated code for common agent anti-patterns

## Chapter Lookup

| # | Chapter | Lines | Best For |
|---|---------|-------|----------|
| 00 | **Agent Anti-Patterns** | 36 | Self-check for common AI code generation mistakes |
| 01 | Clean Code | 10 | Core philosophy: Boy Scout Rule, 10:1 ratio |
| 02 | Meaningful Names | 75 | Naming conventions, intention-revealing names |
| 03 | Functions | 69 | Function size, arguments, side effects, CQS |
| 04 | Comments | 32 | When to comment vs. when to refactor |
| 05 | Formatting | 22 | Vertical code ordering (not horizontal — use formatters) |
| 06 | Objects & Data Structures | 35 | Objects vs DTOs decision guide, Law of Demeter |
| 07 | Error Handling | 52 | Exceptions, null handling, Special Case pattern |
| 08 | Boundaries | 24 | Third-party API wrapping, learning tests |
| 09 | Unit Tests | 50 | TDD laws, FIRST properties, test readability |
| 10 | Classes | 56 | SRP, cohesion, OCP, DIP, class decomposition |
| 11 | Systems | 32 | DI, construction vs use, start simple/scale up |
| 12 | Emergence | 30 | Kent Beck's 4 Rules of Simple Design |
| 13 | Concurrency | 43 | Thread safety, async patterns, execution models |
| 14 | Refinement & Refactoring | 19 | Incremental improvement process |
| 17 | Smells & Heuristics | 80 | **The checklist** — G1-G36, N1-N7, T1-T9 |

## Task-Based Navigation

**"I'm writing a new function"** → ch03 (Functions), ch02 (Names)
**"I'm designing a class"** → ch10 (Classes), ch06 (Objects & Data Structures)
**"I'm writing tests"** → ch09 (Unit Tests), ch12 (Emergence)
**"I'm handling errors"** → ch07 (Error Handling)
**"I'm integrating a library"** → ch08 (Boundaries)
**"I'm refactoring"** → ch14 (Refinement), ch17 (Smells)
**"I need a code review checklist"** → ch17 (Smells & Heuristics) — start here
**"I'm dealing with concurrency"** → ch13 (Concurrency)
**"I want to self-check my generated code"** → ch00 (Agent Anti-Patterns)

## Quick Reference: The 5 Most Important Rules

1. **Functions should do one thing** (ch03) — if you can extract a meaningfully-named sub-function, it's doing too much
2. **Names should reveal intent** (ch02) — `elapsedTimeInDays` not `d`; long names for long scopes
3. **Don't repeat yourself** (ch12, G5) — duplication is the root of all evil in software
4. **Boy Scout Rule** (ch01) — leave code cleaner than you found it
5. **Command-Query Separation** (ch03) — a function either does something or answers something, never both

## File Structure

```
clean-code/
├── SKILL.md              ← this file
└── chapters/
    ├── ch00-agent-anti-patterns.md   ← NEW: AI-specific self-check
    ├── ch01-clean-code.md
    ├── ch02-meaningful-names.md
    ├── ch03-functions.md
    ├── ch04-comments.md
    ├── ch05-formatting.md
    ├── ch06-objects-and-data-structures.md
    ├── ch07-error-handling.md
    ├── ch08-boundaries.md
    ├── ch09-unit-tests.md
    ├── ch10-classes.md
    ├── ch11-systems.md
    ├── ch12-emergence.md
    ├── ch13-concurrency.md
    ├── ch14-successive-refinement.md
    └── ch17-smells-and-heuristics.md
```
