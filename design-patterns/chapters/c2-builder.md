## Builder (Creational)

### Intent
Separate the construction of a complex object from its representation so that the same construction process can create different representations.

### Problem
- Construction logic for a complex object (parsing, assembly) is coupled with the representation of its parts.
- Creating different representations requires duplicating the construction algorithm.
- Object creation needs to happen step-by-step rather than in a single call.

### Participants
- **Builder**: Abstract interface for creating parts of a Product object.
- **ConcreteBuilder**: Implements Builder interface to construct/assemble parts; tracks the representation and provides a retrieval method.
- **Director**: Constructs an object using the Builder interface (e.g., a parser/reader).
- **Product**: The complex object under construction (internal structure varies by ConcreteBuilder).

### When to Use
- The algorithm for creating a complex object should be independent of the parts and their assembly.
- The construction process must allow for different representations of the constructed object.
- You need finer control over the construction process than other creational patterns provide.

### Implementation
- **Step-by-Step**: Unlike other creational patterns, Builder constructs products piece-by-piece under Director control.
- **Assembly Interface**: The Builder interface must be general enough to support all concrete representations.
- **Abstract Builder Defaults**: Typically provides empty/no-op methods so ConcreteBuilders only override parts they need.
- **Product Variety**: Products often differ so much they lack a common parent class; clients retrieve results from the specific ConcreteBuilder.
- **Retrieval**: The Director typically does not return the product; the client retrieves it from the Builder after the process finishes.

### Consequences
- **Varies Representation**: Changing a product's internal structure only requires defining a new ConcreteBuilder.
- **Isolates Construction**: Encapsulates the mechanism for assembly; Directors and Clients are shielded from part classes.
- **Finer Control**: Provides a "step-by-step" construction flow, allowing for complex assembly logic (e.g., bottom-up tree construction).

### Related Patterns
- **Abstract Factory**: Focuses on families of product objects (returned immediately); Builder focuses on step-by-step construction of one complex object.
- **Composite**: Often the kind of complex object that a Builder is used to create.
