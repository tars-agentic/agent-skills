## Visitor (Behavioral)

### Intent
- Represent an operation to be performed on elements of an object structure.
- Define new operations without changing the classes of the elements on which it operates.

### Problem
- Distributing operations across node classes leads to hard-to-maintain, "polluted" classes.
- Adding a new operation usually requires recompiling all element classes.
- Logic for different phases (e.g., type-checking vs. code-gen) gets mixed together.

### When to Use
- Structure contains many classes with differing interfaces.
- Many distinct and unrelated operations need to be performed.
- The Element hierarchy is stable, but the algorithms applied to it change frequently.

### Participants
- **Visitor**: Declares `Visit(ConcreteElement)` for every element class in the structure.
- **ConcreteVisitor**: Implements the algorithm fragments; stores state across the traversal.
- **Element**: Defines an `Accept(Visitor)` interface.
- **ConcreteElement**: Implements `Accept` to call back the specific visit method (`visitor.VisitConcreteElement(this)`).
- **ObjectStructure**: Maintains elements; provides a high-level interface for visitors.

### Double Dispatch
- **Definition**: The operation depends on two receiver types: the Visitor and the Element.
- **Logic**: Instead of binding operations statically, `Accept` performs a runtime binding based on both class hierarchies.
- **Result**: Effectively allows adding operations to classes without modifying them.

### Traversal Strategies
- **ObjectStructure**: Common for collections; iterates and calls `Accept`.
- **Visitor**: Used for irregular or complex traversals that depend on visit results.
- **Iterator**: Separate object handles the iteration, calling `Accept` on each element.

### Consequences
- **(+) Easy to add operations**: Just define a new Visitor subclass; no need to touch elements.
- **(+) Localized Logic**: Groups related behavior for a specific operation in one class.
- **(+) State accumulation**: Easy to gather data (e.g., total cost, inventory) during traversal.
- **(-) Hard to add element types**: Adding a new element class requires updating all Visitor subclasses.
- **(-) Broken Encapsulation**: Elements often must expose internal state via public methods for the Visitor.

### Related Patterns
- **Composite**: Often used together to apply operations over tree structures.
- **Interpreter**: Visitor can implement the interpretation/evaluation of the AST.
