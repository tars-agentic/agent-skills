## Factory Method (Creational)

### Intent
- Define an interface for creating an object while letting subclasses decide which class to instantiate.
- Defer object instantiation to subclasses.
- Alias: Virtual Constructor.

### Problem
- A framework or class must instantiate products but only knows their abstract interfaces, not concrete implementations.
- The specific subclass to instantiate is unforeseeable or should be decided by extensions.

### Participants
- **Product**: Interface for objects created by the factory.
- **ConcreteProduct**: Specific implementation of the Product interface.
- **Creator**: Declares the factory method (returning Product). Can provide a default implementation.
- **ConcreteCreator**: Overrides the factory method to return a specific ConcreteProduct.

### When to Use
- A class cannot anticipate the specific class of objects it needs to create.
- A class wants its subclasses to specify the objects it creates.
- To localize the knowledge of which helper subclasses are responsible for specific tasks.

### Implementation
- **Abstract vs. Concrete Creator**: Creator can be abstract (forcing subclassing) or concrete (providing a default product).
- **Parameterized Methods**: Factory method accepts a parameter (ID) to create various products under one interface.
- **Lazy Initialization**: Use accessors to trigger the factory method only when the object is first requested.
- **Templates (C++)**: Use template subclasses of Creator to avoid manual subclassing for every product type.
- **Constructor Warning**: Avoid calling factory methods inside the Creator's constructor (subclass overrides aren't active yet in C++).
- **Naming**: Use distinct naming conventions (e.g., `CreateDocument`, `MakeWidget`) to signal factory behavior.

### Consequences
- **Decoupling**: Eliminates the need to bind application-specific classes into the code; operates on Product interface.
- **Subclassing Overhead**: Clients may need to subclass the Creator just to create a specific ConcreteProduct.
- **Hooks**: Provides a flexible entry point for subclasses to extend or swap internal components.
- **Parallel Hierarchies**: Naturally connects related class hierarchies (e.g., Figures and their Manipulators).

### Related Patterns
- **Abstract Factory**: Frequently implemented using factory methods.
- **Template Method**: Factory methods are often the "hook" steps within a larger template method.
- **Prototype**: Alternative that uses cloning to avoid subclassing the Creator.
