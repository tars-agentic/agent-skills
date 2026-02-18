## Singleton (Creational)

*   **Intent**: Ensure a class has only one instance and provide a global point of access to it.
*   **Problem**: Certain classes (spoolers, file systems, window managers) must have exactly one instance to maintain consistency and should be easily accessible.
*   **Participants**:
    *   **Singleton**: Defines an `Instance` operation (static/class method) to access the unique instance. Responsible for creating and managing its own sole instance.
*   **When to Use**:
    *   There must be exactly one instance of a class, accessible from a well-known point.
    *   The sole instance should be extensible by subclassing without modifying client code.
*   **Implementation Notes**:
    *   **Uniqueness**: Hide the constructor (protected/private) and provide a static method that handles lazy initialization.
    *   **Static vs. Lazy**: Lazy initialization in a static method is preferred over global objects to control initialization order and avoid instantiating unused singletons.
    *   **Subclassing**: To allow subclasses, the `Instance` method can use environment variables, hard-coded logic, or a registry to determine which class to instantiate.
    *   **Registry approach**: Singleton classes register their instances by name in a lookup table, allowing `Instance` to remain decoupled from specific subclasses.
*   **Consequences**:
    *   **Controlled Access**: Strict control over how and when clients access the instance.
    *   **Reduced Name Space**: Avoids polluting the global namespace with variables.
    *   **Variable Instance Count**: Easy to adapt if the design later requires a specific number of instances (e.g., a pool) rather than just one.
    *   **Extensibility**: Allows polymorphic overrides of operations through subclassing.
*   **Related Patterns**:
    *   **Abstract Factory, Builder, Prototype**: These creational patterns are often implemented as Singletons.
    *   **Global Variables**: Singleton is the structured alternative to global state.
