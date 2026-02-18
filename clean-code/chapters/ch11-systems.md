## Chapter 11: Systems

### Separation of Construction from Use
- **Startup vs. Runtime:** Separate the startup process (wiring) from the runtime logic.
- **Main Separation:** Move all construction logic to a dedicated setup or "Main" module.
- **Lazy Initialization:** Can simplify but mixes construction with use; prefer explicit wiring or DI containers.
- **Inversion of Control (IoC):** The app doesn't fetch dependencies; it receives them. Control flows from the framework into your code.
- **Dependency Injection:** Applications should be passive, receiving dependencies rather than fetching them.
- **DI Containers:** When wiring gets complex, delegate to a container (Spring, Guice, etc.) rather than manual factories.
- **Abstract Factories:** Use factories when the app decides *when* to create an object, but not *how*.
- **Testability:** Designing classes to receive dependencies ensures they are easily testable and mockable.

### Scaling and Emergent Architecture
- **Incremental Growth:** Software architectures can and should grow incrementally, unlike physical buildings.
- **Avoid BDUF:** Big Design Up Front inhibits change; start with "naively simple" designs and scale up.
- **Test-Driven Architecture:** Maintain the ability to evolve by keeping concerns decoupled and tested.
- **Economic Feasibility:** Radical change is possible only if concerns are effectively separated.
- **Iterative Agility:** Implement only today's stories; refactor and expand for tomorrow's requirements.

### Cross-Cutting Concerns
- **Modularity:** Persistence, security, and logging should be separable from core domain logic.
- **Plain Object Purity:** Keep domain objects plain — no framework base classes, no ORM annotations, no infrastructure imports. Domain logic should be testable with zero dependencies.
- **Non-Invasive Logic:** Decouple the "what" (business rules) from the "how" (storage, transport).
- **Modern Patterns:** Use middleware, decorators, or plugin hooks to handle systemic behaviors.

### Implementation Checklist
- **Isolate Construction:** Is all `new` keyword usage localized to factories or wiring modules?
- **Passive Dependencies:** Does the class ask for what it needs instead of building it?
- **Plain Objects:** Can domain classes be tested without booting a framework or container?
- **Simplicity Rule:** Use the simplest architecture that satisfies the current requirements.

**Agent relevance:**
When agents scaffold a new project, they should separate wiring (construction) from logic (use) from the start.
The most common agent mistake is hardcoding dependencies inline instead of injecting them.
