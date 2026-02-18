## Chapter 6: Objects and Data Structures

### The Fundamental Dichotomy
*   **Objects**: Hide implementation behind abstractions; expose behavior. True abstraction allows manipulation of the "essence" of data without knowing its form (e.g., `getPercentFuel()` vs `getGallons()`).
*   **Data Structures**: Expose their data and have no meaningful functions.
*   **The Anti-Symmetry**: Objects make it easy to add new classes without changing functions. Data structures make it easy to add new functions without changing data structures.
*   **Hiding Implementation**: It is not enough to just use private variables with getters/setters. That is just a data structure in disguise.

### The Law of Demeter (Agent Heuristics)
*   **The Rule**: A method `f` of class `C` should only call methods of `C`, objects created by `f`, arguments to `f`, or instance variables of `C`.
*   **Train Wrecks**: Agents frequently generate chains like `disk.getDrive().getPartition().getPath()`. This is a massive coupling failure and a violation of Demeter.
*   **Tell, Don't Ask**: Instead of navigating through an object to find data, tell the object to perform the task: `disk.getAbsolutePath()`.
*   **Distinction**: Demeter applies to **Objects**. It does **not** apply to **Data Structures** (DTOs), which naturally expose their internal structure.

### The Hybrid Anti-Pattern
*   **Definition**: Classes that are half-object and half-data structure (public variables/accessors + business logic).
*   **Why Agents Fail Here**: Agents love "convenience" methods. They often take a simple DTO and start adding validation or processing logic to it, or take a Service and expose its internal state.
*   **The Cost**: Hybrids are "the worst of both worlds." They are hard to add functions to (requires checking state) and hard to add types to (requires updating existing logic).

### Specialized Structures
*   **DTO (Data Transfer Object)**: Public variables, no functions. Ideal for DB communication, socket messages, and API responses.
*   **Active Record**: DTOs with navigational methods (`save`, `find`). 
*   **Critical Warning**: Never add business rule methods to Active Records. Treat them as data structures; create separate domain objects that hide their internal Active Record instances.

### Agent Decision Guide
When generating code, use this logic to choose your path:

1.  **Will you add more TYPES over time?** (e.g., `Circle`, `Square`, `Triangle`)
    → **Use Objects.** Polymorphism allows adding new types without touching existing code.
2.  **Will you add more OPERATIONS over time?** (e.g., `draw()`, `area()`, `toJSON()`)
    → **Use Data Structures.** Procedural code allows adding new functions without touching the data shapes.
3.  **Not sure?**
    → **Default to Data Structures** for system boundaries (DTOs, API responses, Persistence).
    → **Default to Objects** for the core Domain Model (Business logic, State transitions).
4.  **The Switch Test**: If you find yourself writing a `switch` or `if/else` block based on a type field, you are writing procedural code. If that list of types is likely to grow, refactor to an Object.
