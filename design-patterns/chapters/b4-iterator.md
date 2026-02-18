## Iterator (Behavioral)

### Intent
- Provide a way to access elements of an aggregate object sequentially without exposing its underlying internal representation.

### Problem
- You need to traverse different structures (lists, trees, stacks) using a uniform interface.
- You want to support multiple simultaneous traversals or different traversal orders (forward, backward, filtered).
- The aggregate object should not be bloated with various traversal methods.

### When to Use
- To hide the internal complexity of a collection from clients.
- To support polymorphic iteration (same code works for different collection types).
- To allow multiple traversals to be "in-flight" on the same aggregate.

### Participants
- **Iterator**: Defines the interface for access and traversal (`First`, `Next`, `IsDone`, `CurrentItem`).
- **ConcreteIterator**: Implements the traversal algorithm and tracks the current position.
- **Aggregate**: Defines an interface for creating an Iterator object.
- **ConcreteAggregate**: Returns an instance of the appropriate ConcreteIterator.

### Implementation Notes
- **External vs. Internal**: External iterators (client controls `Next`) are more flexible (e.g., comparing two collections). Internal iterators (iterator accepts a functional/callback) are easier to use but less flexible in languages without closures.
- **Robustness**: Modifying a collection during iteration is dangerous. Robust iterators ensure traversal continues correctly without copying the entire collection (usually via registration with the aggregate).
- **Null Iterator**: Useful for tree structures; leaf nodes return a `NullIterator` that is always `IsDone`, simplifying recursive traversal code.
- **Cursors**: A variation where the aggregate performs the `Next` operation and the iterator merely stores the state (index/pointer).

### Consequences
- **Pros**: Supports multiple traversal variations; simplifies the Aggregate's public API; decouples the traversal algorithm from the data structure.
- **Cons**: Can be overkill for simple collections; polymorphic iterators in C++ may require manual memory management (often solved with Proxy/Smart Pointers).

### Related Patterns
- **Composite**: Iterators are frequently used to traverse recursive structures.
- **Factory Method**: Used by the Aggregate to create the correct Iterator subclass.
- **Memento**: Can be used to capture the state of an iteration so it can be resumed later.
