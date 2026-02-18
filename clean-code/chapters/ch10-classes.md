## Chapter 10: Classes

### Class Organization
- Follow standard conventions: 1) Public static constants, 2) Private static variables, 3) Private instance variables.
- Public variables should be extremely rare; maintain encapsulation.
- Public functions should be followed by the private utilities they call (Stepdown Rule).
- Loosen encapsulation (e.g., `protected` for tests) only as a last resort.

### Classes Should Be Small
- The first and second rule of classes: they should be small.
- Measure size by **responsibilities**, not physical lines.
- Class names must be descriptive; if you can't name it concisely, it's too large.
- Avoid "weasel words" like *Processor*, *Manager*, or *Super* in class names.
- A class description should be ~25 words without using "if," "and," "or," or "but."

### Single Responsibility Principle (SRP)
- A class or module should have one, and only one, reason to change.
- SRP is often abused because "getting it to work" is prioritized over "clean organization."
- A system of many small, single-purpose classes is easier to manage than a few large "God classes."
- Small classes act as well-labeled toolboxes; large ones are junk drawers.

### Cohesion
- Cohesion is high when methods and variables of a class are co-dependent.
- A class is maximally cohesive when every instance variable is used by every method.
- High cohesion leads to "hanging together" as a logical whole.
- When classes lose cohesion, they should be split.
- Breaking large functions into smaller ones often creates new classes with higher cohesion.

### Concrete Example: SQL Decomposition
- A class like `Sql` that handles SELECT, INSERT, UPDATE, and DELETE violates SRP.
- Decompose into: `SelectSql`, `InsertSql`, `UpdateSql`, etc., each handling one statement type.
- Adding a new type (e.g., `UpsertSql`) means adding a class, not modifying existing ones (OCP).

### Organizing for Change
- Change is continual; classes must be organized to reduce the risk of change.
- Violating SRP makes classes "fragile" when new features are added.
- **Open-Closed Principle (OCP)**: Classes should be open for extension but closed for modification.
- Ideally, new features are incorporated by extending the system, not modifying existing code.
- Refactor large multi-purpose classes into hierarchies of single-purpose subclasses.

### Isolating from Change
- Dependencies on concrete details (e.g., an external API) make code volatile and hard to test.
- Use interfaces and abstract classes to represent concepts and isolate implementation details.
- **Dependency Inversion Principle (DIP)**: Classes should depend upon abstractions, not concrete details.
- Minimizing coupling ensures elements are better isolated from each other and from change.
- Testability is a hallmark of a decoupled system.

### Key Heuristics for AI Agents
- **Name Check**: If the name is generic (e.g., `DataHandler`), split it.
- **Variable Check**: If a method only uses a subset of instance variables, consider extracting a new class.
- **Change Check**: If adding a feature requires editing an existing `switch` or `if/else` block, use polymorphism/OCP.
- **Test Check**: If a class is hard to mock or stub, its coupling is too high.
- **Responsibility Check**: Can you describe what this class does in one sentence without "and"?

### Agent Relevance
Agents default to creating "God classes"—one class that handles everything. The Name Check and the "one-sentence-without-'and'" test are fast self-checks agents should run on every class they generate.
