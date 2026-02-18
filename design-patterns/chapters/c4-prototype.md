## Prototype (Creational)

*   **Intent**: Create new objects by cloning a prototypical instance rather than instantiating a class directly.
*   **Problem**: A system needs to be independent of how its products are created, but classes to instantiate are specified at run-time, or you want to avoid a factory class hierarchy that parallels the product hierarchy.
*   **Participants**:
    *   **Prototype**: Declares an interface for cloning itself.
    *   **ConcretePrototype**: Implements the cloning operation.
    *   **Client**: Creates a new object by asking a prototype to clone itself.
*   **When to Use**:
    *   Classes to instantiate are specified at run-time (e.g., dynamic loading).
    *   To avoid building a factory hierarchy that parallels the product hierarchy.
    *   When instances of a class have only a few different combinations of state; cloning is more convenient than manual instantiation.
*   **Implementation Notes**:
    *   **Clone Operation**: The hardest part. Requires deciding between shallow vs. deep copy. Deep copy is usually needed for complex structures to ensure independence.
    *   **Prototype Manager**: Use a registry (associative store) when the number of prototypes isn't fixed, allowing clients to browse/retrieve prototypes by key.
    *   **Initialization**: Clones might need an `Initialize` operation to set state, as `Clone` typically cannot take varying parameters.
*   **Consequences**:
    *   **Run-time Flexibility**: Can add/remove products at run-time by registering new prototypical instances.
    *   **Reduced Subclassing**: Eliminates the need for a Creator/Factory hierarchy.
    *   **Dynamic Configuration**: Key for environments where classes are loaded dynamically and constructors cannot be referenced statically.
    *   **Liability**: Every subclass must implement `Clone`, which is difficult for existing classes or those with circular references.
*   **Related Patterns**:
    *   **Abstract Factory**: Competing pattern; an Abstract Factory might store a set of prototypes to clone.
    *   **Composite/Decorator**: These patterns often benefit from Prototype for duplicating complex structures.
