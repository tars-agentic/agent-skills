## Chapter 14: Refinement and Refactoring

**Agent relevance:** Agents tend to generate code in a single pass and move on. The refinement mindset — write it, then improve it, then improve it again — is what separates working code from clean code. Agents should budget a second pass.

### The Mindset
- **Clean Code as Craft:** Programs are not written in a single pass; they are evolved through a continuous process of drafting and refinement.
- **The Professional "Done":** Code is not "done" just because it works. Leaving it in a "rough draft" state is unprofessional and dangerous.
- **The Stopping Point:** If adding a feature feels like "bulldozing" through complexity, stop immediately. Clean the structure before proceeding.
- **Continuous Cleaning:** Never let rot start. A mess made five minutes ago is trivial to clean; a mess left for months becomes a malignant morass.

### The Process
- **The TDD Mandate:** You must have a robust suite of automated tests before refactoring; the system must stay "running" at every incremental step.
- **Tests for Behavior, Not Structure:** Use tests to ensure the *behavior* remains identical while the *structure* changes completely.
- **The Rubik's Cube Principle:** Many small moves are required to reach a large architectural goal; each move prepares the state for the next.
- **Parallel Migration Strategy:** When replacing components, add the new one, migrate callers one by one, and then delete the old version.
- **"Putting in to Take Out":** Use temporary "bridging" code during refactoring to maintain system stability until the migration is complete.
- **Iterative Refinement Acceptance:** Refactoring is cyclical; you may extract a method only to inline it later once the surrounding context becomes clearer.

### Techniques
- **Expose Temporal Couplings:** If methods must be called in order, pass the result of the first call as an argument to the second to make the dependency explicit.
- **Logical vs. Physical Dependencies:** A base class should remain generic; it should not assume or depend on the specific physical details of its derivatives.
- **Partitioning of Concerns:** Separate different kinds of code (logic, data marshalling, error formatting) into their own distinct modules or classes.
- **Polymorphism over Type-Checking:** Replace `instanceof` chains and `switch` statements with polymorphic calls to keep core logic generic and clean.
- **Pushing Implementation Down:** Move specific logic from high-level classes into specialized derivatives to keep the core abstractions clean.
