## Chapter 17: Smells and Heuristics

### Comments
- **C1: Inappropriate Information** — Metadata (authors, dates, issue IDs) belongs in version control or tracking systems, not cluttering the source code.
- **C2: Obsolete Comment** — Delete or update old, incorrect comments; they become "floating islands of misdirection" as the code evolves.
- **C3: Redundant Comment** — Avoid comments that restate what the code clearly says for itself (e.g., `i++; // increment i`).
- **C4: Poorly Written Comment** — If a comment is worth writing, take time to be brief, use correct grammar, and avoid stating the obvious.
- **C5: Commented-Out Code** — Delete it immediately; the source code control system remembers it. Commented-out code pollutes modules and distracts readers.

### Environment
- **E1: Build Requires More Than One Step** — Project builds should be a single, trivial operation (e.g., one command) after checking out the source.
- **E2: Tests Require More Than One Step** — Running the entire unit test suite must be a single, obvious command or button click to ensure they are run frequently.

### Functions
- **F1: Too Many Arguments** — Prefer zero arguments; more than three is highly suspect and should be avoided with prejudice.
- **F2: Output Arguments** — Arguments should be inputs, not outputs; if a function must change state, it should change the state of its owning object.
- **F3: Flag Arguments** — Boolean arguments loudly declare that a function does more than one thing; eliminate them by splitting the function.
- **F4: Dead Function** — Discard methods that are never called; keeping dead code is wasteful and makes the system harder to understand.

### General
- **G1: Multiple Languages in One Source File** — Ideally, a source file contains one language; minimize mixing (e.g., XML/JS in Java) to reduce complexity and confusion.
- **G2: Obvious Behavior Is Unimplemented** — Follow "The Principle of Least Surprise"; implement behaviors that another programmer could reasonably expect.
- **G3: Incorrect Behavior at the Boundaries** — Don't trust intuition for correctness; look for every boundary condition and write a test to prove the algorithm holds.
- **G4: Overridden Safeties** — Risking safety for convenience (turning off warnings, ignoring failing tests) leads to catastrophic failures and endless debugging.
- **G5: Duplication** — DRY (Don't Repeat Yourself); duplication represents missed abstractions. Use polymorphism for switch chains and Template Method for similar algorithms.
- **G6: Code at Wrong Level of Abstraction** — Higher-level general concepts must be completely separated from lower-level implementation details in different containers.
- **G7: Base Classes Depending on Their Derivatives** — Base classes should know nothing about their derivatives; this allows independent deployment and components.
- **G8: Too Much Information** — Well-defined modules have tiny interfaces; hide internal data, constants, and utility functions to keep coupling low.
- **G9: Dead Code** — Remove unexecuted code (unreachable if-branches, unused utilities, catch blocks that never fire); dead code rots and confuses readers.
- **G10: Vertical Separation** — Define variables and functions close to their usage. Private functions should be found by scanning downward from the caller.
- **G11: Inconsistency** — Choose conventions carefully and follow them reliably; if you name one variable `response`, use the same name for similar objects.
- **G12: Clutter** — Remove meaningless artifacts: empty default constructors, unused variables, and comments that add no information.
- **G13: Artificial Coupling** — Don't put variables or functions in convenient but inappropriate locations; keep independent things uncoupled.
- **G14: Feature Envy** — A method should not reach into other objects to manipulate their data; it should belong in the class that holds the data it envies.
- **G15: Selector Arguments** — Passing flags or enums to select behavior is a lazy way to avoid splitting a large function into several smaller, focused ones.
- **G16: Obscured Intent** — Code should be expressive; avoid impenetrable run-on expressions, Hungarian notation, and magic numbers that mask meaning.
- **G17: Misplaced Responsibility** — Place code where a reader would naturally expect it (e.g., PI in Math); use function names as a guide for placement.
- **G18: Inappropriate Static** — Prefer nonstatic methods to allow for polymorphism; only use static if there is no chance it will ever need to be overridden.
- **G19: Use Explanatory Variables** — Make opaque modules transparent by breaking complex calculations into intermediate values with meaningful names.
- **G20: Function Names Should Say What They Do** — If you must read the implementation to understand a function, the name has failed and must be changed.
- **G21: Understand the Algorithm** — It is not enough to pass tests by "fiddling"; you must truly understand how the code works to ensure the solution is correct.
- **G22: Make Logical Dependencies Physical** — A module should not make assumptions about its collaborators; explicitly request all information it depends upon.
- **G23: Prefer Polymorphism to If/Else or Switch/Case** — Most switch statements are suspect; follow the "One Switch" rule to create polymorphic objects.
- **G24: Follow Standard Conventions** — Every team must follow a coding standard based on industry norms; the code itself should provide the examples.
- **G25: Replace Magic Numbers with Named Constants** — Hide raw tokens behind well-named constants; this prevents errors and clarifies intent in assertions.
- **G26: Be Precise** — Don't be lazy: check for nulls, handle concurrent updates with locks, and use precise types like integers for currency.
- **G27: Structure over Convention** — Enforce design compliance with code structures (like abstract methods) rather than just naming conventions.
- **G28: Encapsulate Conditionals** — Boolean logic is hard to parse; extract conditional checks into functions that explain the intent behind the check.
- **G29: Avoid Negative Conditionals** — Negatives are harder to understand than positives; always prefer `if (isFull)` over `if (!isNotFull)` to improve readability.
- **G30: Functions Should Do One Thing** — If a function performs a series of operations in sections, convert them into smaller functions that handle one task.
- **G31: Hidden Temporal Couplings** — When call order matters, structure function arguments (bucket brigade) so the result of one is required by the next.
- **G32: Don’t Be Arbitrary** — Every structural decision must have a reason; arbitrary structures empower others to break conventions and erode design.
- **G33: Encapsulate Boundary Conditions** — Boundary conditions (+1, -1) are hard to track; put their processing in one place instead of letting them leak.
- **G34: Functions Should Descend Only One Level of Abstraction** — Statements within a function should share a level of detail one step below the function name.
- **G35: Keep Configurable Data at High Levels** — Don't bury default values or configuration in low-level functions; pass them down from the highest levels.
- **G36: Avoid Transitive Navigation** — Law of Demeter: modules should only know immediate collaborators, not the whole object graph (e.g., `a.getB().getC()`).

### Generalized Principles (Java)
- **J2: Don't Inherit Constants** — Do not use inheritance to cheat scope; use explicit imports or static references to access constants instead.
- **J3: Constants versus Enums** — Prefer rich types (Enums) over raw integers/strings to preserve semantic meaning and attach behavior to values.

### Names
- **N1: Choose Descriptive Names** — Take time to select names that clearly describe purpose and overload the structure with intent.
- **N2: Choose Names at the Appropriate Level of Abstraction** — Names should reflect the conceptual role, not the implementation details.
- **N3: Use Standard Nomenclature Where Possible** — Leverage common patterns and the project's "ubiquitous language" for familiarity.
- **N4: Unambiguous Names** — Use names that distinguish a function’s specific role from similar or surrounding logic.
- **N5: Use Long Names for Long Scopes** — The length of a name should correspond to the size of the scope it covers (short for local, long for global).
- **N6: Avoid Encodings** — Do not pollute names with type info (Hungarian notation) or redundant scope prefixes like `m_` or `f_`.
- **N7: Names Should Describe Side-Effects** — Ensure names account for everything a function does (e.g., `createOrReturnOos` vs `getOos`).

### Tests
- **T1: Insufficient Tests** — A test suite is only complete when it tests everything that could possibly break; don't stop at "enough."
- **T2: Use a Coverage Tool** — Visually identify gaps in testing; ensure if/else branches and catch blocks are exercised.
- **T3: Don’t Skip Trivial Tests** — Simple tests are cheap to write and provide significant documentation of behavior.
- **T4: An Ignored Test Is a Question about an Ambiguity** — Use ignored tests to highlight requirements that need clarification or ambiguity in design.
- **T5: Test Boundary Conditions** — Most bugs happen at the edges; test every limit and boundary condition exhaustively.
- **T6: Exhaustively Test Near Bugs** — Bugs cluster; if you find one, the surrounding code is likely to contain more.
- **T7: Patterns of Failure Are Revealing** — Analyzing how tests fail as a group (e.g., all long inputs fail) can pinpoint underlying issues.
- **T8: Test Coverage Patterns Can Be Revealing** — Use the path of execution through passing tests to find clues for why others are failing.
- **T9: Tests Should Be Fast** — If tests are slow, they won't be run regularly; optimize them to maintain developer flow and system quality.
