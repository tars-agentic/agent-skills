## Chapter 12: Emergence

Kent Beck’s Four Rules of Simple Design (Priority Order):

1. **Runs All the Tests**
   - **Verification:** A system that cannot be verified is not deployable. Tests confirm intended behavior.
   - **Design Pressure:** Comprehensive testability mandates Single Responsibility Principle (SRP) and high cohesion.
   - **Decoupling:** Writing tests forces the use of Dependency Inversion Principle (DIP), Dependency Injection (DI), and abstraction to minimize tight coupling.
   - **Verification Loop:** Passing all tests continuously is the baseline for any refactoring.

2. **Contains No Duplication (DRY)**
   - **Primary Enemy:** Duplication creates additional work, risk, and unnecessary complexity.
   - **Reuse in the Small:** Extract tiny commonalities to build foundations for large-scale reuse.
   - **Consolidation:** Simplify logic by tying related methods to a single source of truth (e.g., `isEmpty` returns `size == 0`).
   - **Template Method Pattern:** Use inheritance to pull common algorithmic structures into base classes, leaving specific differences to subclasses.
   - **Refactoring Safety:** With tests in place (Rule 1), code can be aggressively cleaned without fear.

3. **Expresses Intent (Expressive)**
   - **Maintenance Cost:** The majority of software cost is long-term maintenance; readability reduces defects and cost.
   - **Naming:** Choose names that reveal responsibility and intent; avoid surprising the reader.
   - **Granularity:** Small classes and functions are inherently easier to name, write, and understand.
   - **Standardization:** Use standard design patterns (e.g., Command, Visitor) as linguistic shorthand for developers.
   - **Living Docs:** Treat unit tests as documentation by example to explain class behavior.
   - **Workmanship:** Spend time actively refining code for the "next person" (often your future self).

4. **Minimizes Classes and Methods**
   - **System Size:** Aim for the smallest overall system footprint possible while maintaining clarity.
   - **Anti-Dogmatism:** Resist pointless rules (e.g., "interface for every class" or strict data/behavior separation) that inflate class counts.
   - **Priority Check:** This is the lowest priority; never sacrifice testability, DRY, or expressiveness to reduce method counts.
   - **Pragmatism:** Balance the desire for tiny components against the overhead of excessive abstractions.
