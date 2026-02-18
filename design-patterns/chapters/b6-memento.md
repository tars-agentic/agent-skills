## Memento (Behavioral)

### Intent
* Capture and externalize an object's internal state without violating encapsulation.
* Allow the object to be restored to this specific state at a later time.

### Problem
* Need to implement undo mechanisms or checkpoints to recover from errors or tentative operations.
* Direct access to internal state breaks encapsulation and compromises reliability/extensibility.
* Exposing internals to an external "caretaker" makes the object's implementation hard to change.

### Participants
* **Memento**: Stores internal state of the Originator; opaque to all other objects.
* **Originator**: Creates the memento; uses it to restore its own state.
* **Caretaker**: Responsible for memento's safekeeping; never operates on or examines its contents.

### When to Use
* A snapshot of an object's state must be saved for later restoration.
* A direct interface for state access would expose implementation details/break encapsulation.

### Implementation Notes
* **Narrow vs. Wide Interface**: The Caretaker sees a narrow interface (can only pass the memento); the Originator sees a wide interface (can access state data).
* **Language Support**: Use "friend" classes (C++), private inner classes, or opaque tokens to restrict access to the memento's internals.
* **Incremental Changes**: Mementos can store only the difference (delta) from a previous state if created in a predictable sequence.
* **Storage Overhead**: If state is large or snapshots are frequent, mementos can become expensive in terms of memory and copy time.

### Consequences
* **Preserves Encapsulation**: Keeps complex internal state management hidden from clients.
* **Simplifies Originator**: Offloads the burden of state storage management to the client/caretaker.
* **Hidden Costs**: Caretakers may unknowingly incur high storage costs for opaque mementos.
* **Lifecycle Management**: The caretaker must ensure mementos are deleted when no longer needed.

### Related Patterns
* **Command**: Commands often use mementos to store state for undoable operations.
* **Iterator**: Mementos can represent the state of an iteration to avoid breaking collection encapsulation.
