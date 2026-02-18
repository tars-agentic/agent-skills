## Facade (Structural)

### Intent
* Provide a unified, high-level interface to a set of interfaces in a subsystem.
* Make complex subsystems easier to use by simplifying the entry point.

### Problem
* Complex subsystems with many classes are difficult for most clients to interact with directly.
* Tight coupling between clients and subsystem internals limits portability and independence.
* Changes inside a subsystem force recompilation of all dependent client code.

### Participants
* **Facade:** Knows which subsystem classes are responsible for a request; delegates work to them.
* **Subsystem Classes:** Implement specific functionality; have no knowledge of the Facade.

### When to Use
* Providing a simple default view of a complex subsystem for most clients.
* Decoupling clients from subsystem implementation to promote independence.
* Layering subsystems; use a Facade as the entry point for each level.

### Implementation Notes
* **Reducing Coupling:** Make Facade an abstract class or configure it with different subsystem objects to swap implementations.
* **Public vs. Private:** Use the Facade as the public interface while keeping complex subsystem details private/internal (e.g., via namespaces).
* **Don't Hide Internals:** A Facade simplifies but should not prevent advanced clients from accessing lower-level classes if needed.

### Consequences
* **Shields Clients:** Reduces the number of objects clients must manage and understand.
* **Weak Coupling:** Allows varying subsystem components without affecting the client.
* **Reduced Dependencies:** Minimizes compilation dependencies in large systems (changing a subsystem doesn't require recompiling all clients).
* **Layering Support:** Simplifies cross-subsystem communication by channeling it through a single point.

### Related Patterns
* **Abstract Factory:** Can be used with Facade to create subsystem objects in a platform-independent way.
* **Mediator:** Centralizes communication between colleague objects; Facade abstracts an existing interface to simplify use.
* **Singleton:** Facades are often implemented as Singletons since only one access point is usually required.
