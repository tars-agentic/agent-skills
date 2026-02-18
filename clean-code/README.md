# Clean Code — Agent Skill

Distilled from *Clean Code: A Handbook of Agile Software Craftsmanship* by Robert C. Martin (2008). 667 lines of actionable reference material for AI coding agents, with 2026 agentic framing.

## Contents

| Chapter | Lines | Topic |
|---------|-------|-------|
| 00 – Agent Anti-Patterns | 36 | AI-specific self-check for common code generation mistakes |
| 01 – Clean Code | 10 | Core philosophy: Boy Scout Rule, 10:1 read-to-write ratio |
| 02 – Meaningful Names | 75 | Naming conventions, intention-revealing names |
| 03 – Functions | 69 | Function size, arguments, side effects, CQS |
| 04 – Comments | 29 | When to comment vs. when to refactor |
| 05 – Formatting | 22 | Vertical code ordering (horizontal handled by formatters) |
| 06 – Objects & Data Structures | 35 | Objects vs DTOs decision guide, Law of Demeter |
| 07 – Error Handling | 52 | Exceptions, null elimination, Special Case pattern |
| 08 – Boundaries | 24 | Third-party API wrapping, learning tests |
| 09 – Unit Tests | 50 | TDD laws, FIRST properties, test readability |
| 10 – Classes | 56 | SRP, cohesion, OCP, DIP, class decomposition |
| 11 – Systems | 32 | DI, construction vs use, start simple / scale up |
| 12 – Emergence | 30 | Kent Beck's 4 Rules of Simple Design |
| 13 – Concurrency | 43 | Thread safety, async patterns, execution models |
| 14 – Refinement & Refactoring | 24 | Incremental improvement process |
| 17 – Smells & Heuristics | 80 | The checklist: G1-G36, N1-N7, T1-T9, C1-C5, E1-E2, F1-F4 |

## What Was Cut

The original book is ~460 pages. This skill retains principles and heuristics; the following were removed:

- **Biographical content** — definitions of "clean code" from various luminaries (ch01)
- **Horizontal formatting rules** — auto-formatters handle these now (ch05)
- **Java-specific content** — EJB, Spring examples, checked exceptions debate (ch11)
- **Code walkthroughs** — the Args, JUnit, and SerialDate case studies (ch14-16); meta-lessons preserved
- **AOP details** — kept the cross-cutting concern principle, dropped framework-specific content (ch11)
- **Redundant motivational content** — "clean your code" said 8 ways (ch14)

## What Was Added

- **Agent Anti-Patterns (ch00)** — original content cataloguing the specific ways AI agents violate Clean Code, with cross-references to relevant chapters
- **Agent Relevance notes** — every chapter has a 2-3 line note on why it matters for agentic coding
- **Decision guides** — Objects vs Data Structures decision tree (ch06), responsibility self-checks (ch10)
- **Modern concurrency patterns** — async/await, channels, actors alongside the classic thread model (ch13)

## Source

97.3% reduction from source material (24,864 lines → 667 lines).

Pipeline: PDF → markitdown → chapter split → sub-agent distillation (ag-flash) → critical review → sub-agent refinement → polish pass.
