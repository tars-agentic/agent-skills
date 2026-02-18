## Mediator (Behavioral)

### Intent
* Encapsulate interaction logic between a set of objects.
* Promote loose coupling by preventing objects from referring to each other explicitly.
* Allow varying object interactions independently of the objects themselves.

### Problem
* Distributed behavior among many objects results in a "spaghetti" of interconnections.
* High coupling makes objects less reusable and the system difficult to change.
* Customizing behavior requires extensive subclassing of individual components.

### Participants
* **Mediator**: Defines an interface for communicating with Colleague objects.
* **ConcreteMediator**: Implements coordination logic; maintains references to colleagues.
* **Colleague**: Each object knows its mediator; communicates with it instead of other colleagues.

### When to Use
* Objects communicate in well-defined but complex, unstructured ways.
* Reusing an object is difficult because it depends on many others.
* Distributed behavior should be customizable without heavy subclassing.

### Implementation Notes
* **Abstract Mediator**: Can be omitted if colleagues only work with one mediator.
* **Communication**: Colleagues can notify the mediator via the Observer pattern or a specialized notification interface.
* **Identification**: Colleagues often pass themselves as arguments so the mediator knows the sender.
* **Centralization**: The mediator simplifies colleague protocols but risks becoming a complex "god object."

### Consequences
* **Decouples Colleagues**: Promotes many-to-many to one-to-many relationships.
* **Simplifies Protocols**: Replaces complex interconnections with a central hub.
* **Abstracts Cooperation**: Focuses on how objects interact as a distinct concept.
* **Centralized Complexity**: Complexity shifts from colleagues to the mediator itself.

### Related Patterns
* **Facade**: Provides a unidirectional interface to a subsystem; Mediator is multidirectional for cooperative behavior.
* **Observer**: Often used to implement the communication between colleagues and the mediator.
