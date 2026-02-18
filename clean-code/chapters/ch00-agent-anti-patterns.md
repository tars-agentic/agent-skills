## Agent Anti-Patterns

Common ways AI coding agents violate Clean Code principles. Use as a self-check.

### Code Generation Anti-Patterns
- **God Functions** — Dumping all logic into one long function instead of decomposing. Agents often generate 80+ line functions that do setup, validation, processing, error handling, and formatting in a single block. *Fix: apply ch03 — extract until each function does one thing.*
- **Inconsistent Naming** — Using `getData` in one module and `fetchData` in another, or `user` here and `currentUser` there for the same concept. *Fix: apply ch02 (N1, G11) — one word per concept, used consistently.*
- **Over-Commenting** — Generating boilerplate docstrings for every function including trivial getters and self-explanatory methods. Writing `// increment counter` above `counter++`. *Fix: apply ch04 — if the name says it all, skip the comment.*
- **Defensive Over-Engineering** — Wrapping everything in try/catch, adding null checks at every level, creating interfaces nobody will ever implement. *Fix: apply ch07 — handle errors at boundaries, use the Special Case pattern, trust your own code.*
- **Copy-Paste Variations** — Generating near-identical functions with minor differences instead of extracting shared logic. *Fix: apply G5 (DRY) — if two functions share 80% of their code, extract the common part.*
- **Premature Abstraction** — Creating `IUserService`, `AbstractUserFactory`, and `UserRepositoryBase` when there's only one implementation. *Fix: apply ch12 rule 4 — minimize entities. Add abstraction when you have a second use case, not before.*

### Structural Anti-Patterns
- **Kitchen Sink Classes** — Creating `UserManager` or `DataHandler` classes that accumulate every vaguely related method. *Fix: apply ch10 — if you can't describe the class in one sentence without "and," split it.*
- **Leaky Boundaries** — Scattering raw third-party API calls throughout the codebase instead of wrapping them. *Fix: apply ch08 — one wrapper, many callers.*
- **Hybrid Objects** — Classes that expose public data fields AND contain business logic methods. Neither a proper object nor a clean data structure. *Fix: apply ch06 — choose one role.*
- **Train Wreck Chains** — `user.getAccount().getSettings().getPreferences().getTheme()` — violating Law of Demeter by navigating deep object graphs. *Fix: apply G36 — talk to immediate collaborators only.*

### Testing Anti-Patterns
- **Missing Edge Cases** — Testing the happy path but ignoring null inputs, empty collections, boundary values, and error conditions. *Fix: apply T5 — test boundaries exhaustively.*
- **Test-After Fragility** — Generating implementation first, then bolting on tests that mirror the implementation structure rather than verifying behavior. *Fix: apply ch09 — tests verify behavior, not structure.*
- **Slow/Coupled Tests** — Tests that hit real databases, make network calls, or depend on execution order. *Fix: apply FIRST — Fast, Independent, Repeatable, Self-Validating, Timely.*

### Process Anti-Patterns
- **Single-Pass Generation** — Generating code once and declaring it done. No refinement, no self-review. *Fix: apply ch14 — budget a second pass. Write it, then improve it.*
- **Rewrite Reflex** — When asked to fix existing code, rewriting the entire file instead of making targeted changes. *Fix: apply the Boy Scout Rule — small improvements, not demolitions.*
- **Context Blindness** — Ignoring existing codebase conventions (naming patterns, error handling style, file organization) and generating code that clashes with its surroundings. *Fix: apply G11 and G24 — read the existing code first, then match its conventions.*

### Quick Self-Check
Before submitting generated code, an agent should verify:
1. Can every function be described in one sentence? (ch03)
2. Are names intention-revealing and consistent? (ch02)
3. Are comments adding value the code can't express? (ch04)
4. Is error handling at the boundaries, not scattered everywhere? (ch07)
5. Are there tests for the happy path AND edge cases? (ch09)
6. Does the code match the surrounding codebase's conventions? (G11, G24)
