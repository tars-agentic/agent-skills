## Introduction: Design Patterns Fundamentals

- **Definition**: A design pattern names, abstracts, and identifies the key aspects of a common design structure that make it useful for creating a reusable object-oriented design.
- **Essential Elements**:
    - **Pattern Name**: A handle used to describe a design problem, its solutions, and consequences; increases design vocabulary.
    - **Problem**: Describes when to apply the pattern; explains the problem, context, and conditions to be met.
    - **Solution**: Describes the design elements (classes/objects), their relationships, responsibilities, and collaborations.
    - **Consequences**: Results and trade-offs (space/time, flexibility, extensibility, portability) of applying the pattern.

- **Taxonomy by Purpose**:
    - **Creational**: Concerns the process of object creation (abstracting instantiation).
    - **Structural**: Deals with the composition of classes or objects (assembling larger structures).
    - **Behavioral**: Characterizes the ways in which classes or objects interact and distribute responsibility.

- **Taxonomy by Scope**:
    - **Class**: Static relationships established through inheritance; fixed at compile-time.
    - **Object**: Dynamic relationships between objects; changeable at run-time.

- **Core Design Principles**:
    - **Program to an interface, not an implementation**:
        - Manipulate objects solely in terms of interfaces defined by abstract classes.
        - Clients remain unaware of specific types or implementing classes, reducing subsystem dependencies.
    - **Favor object composition over class inheritance**:
        - **Inheritance (White-box reuse)**: Internals are visible; breaks encapsulation; bound at compile-time.
        - **Composition (Black-box reuse)**: Assembles objects with well-defined interfaces; respects encapsulation; dynamic.
        - Keeps classes focused/encapsulated; behavior depends on interrelationships rather than deep hierarchies.
    - **Encapsulate what varies**:
        - Identify aspects of design likely to change and isolate them.
        - Enables changing the varying concept (algorithm, state, creation) without a total redesign.

- **Common Variabilities Addressed**:
    - **Creational**: Families of products, construction processes, or specific classes to instantiate.
    - **Structural**: Interfaces, object implementations, object structures, or responsibilities.
    - **Behavioral**: Algorithms, request fulfillment, interaction protocols, and object states.

- **Key Mechanisms**:
    - **Delegation**: Passing a request from a receiver to a delegate (passing 'self' to allow feedback); replaces inheritance.
    - **Aggregation**: A "part-of" relationship implying ownership and identical lifetimes.
    - **Acquaintance**: A "knows-of" relationship (association); looser coupling than aggregation.
    - **Dynamic Binding**: Associating a request to an object/operation at run-time; enables polymorphism.
