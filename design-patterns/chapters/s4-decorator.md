## Decorator (Structural)

### Intent
* Dynamically attach additional responsibilities to an object.
* Provide a flexible alternative to subclassing for functionality extension.

### Problem
* Static inheritance is inflexible; it applies to all instances and cannot be changed at runtime.
* Adding every possible feature combination via subclassing leads to class explosion.
* Need to add behavior to individual objects without affecting others of the same class.

### Participants
* **Component:** Interface for objects that can have responsibilities added.
* **ConcreteComponent:** The base object to which responsibilities are attached.
* **Decorator:** Maintains reference to a Component; conforms to the Component interface.
* **ConcreteDecorator:** Implements the added responsibilities; overrides methods to add behavior before/after forwarding requests.

### When to Use
* Adding/removing responsibilities dynamically and transparently at runtime.
* When extension by subclassing is impractical due to the number of combinations.
* When a class definition is hidden or unavailable for subclassing.

### Implementation Notes
* **Interface Conformance:** Decorators must strictly follow the interface of the component they wrap.
* **Omit Abstract Class:** If adding only one responsibility, merge Decorator and ConcreteDecorator.
* **Lightweight Component:** Keep the base Component class focused on interface, not data storage, to avoid heavy decorators.
* **Skin vs. Guts:** Decorators change the "skin" (outer behavior); use Strategy to change the "guts" (inner algorithm).

### Consequences
* **Higher Flexibility:** Responsibilities can be added/removed at runtime; allows mixing/matching behaviors.
* **Avoids Bloat:** Functionality is composed from simple pieces rather than monolithic, feature-heavy classes.
* **Identity Issues:** A decorated component is not identical to the original; avoid relying on object identity.
* **Object Proliferation:** Can result in many small, similar-looking objects that make debugging harder.

### Related Patterns
* **Adapter:** Changes the interface; Decorator only changes responsibilities.
* **Composite:** A Decorator is like a Composite with only one child; focus is on behavior, not aggregation.
* **Strategy:** Changes the internal implementation; Decorator changes the external wrapper.
