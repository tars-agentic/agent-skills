## State (Behavioral)

*   **Intent:** Allow an object to alter its behavior when its internal state changes. The object will appear to change its class.
*   **Problem:** Avoiding massive conditional (if/switch) statements that depend on an object's state and are duplicated across many operations.
*   **When to Use:**
    *   An object's behavior depends on its state and must change at run-time.
    *   Operations have large, multipart conditional statements based on state constants.
*   **Participants:**
    *   **Context:** Defines the interface of interest to clients; maintains an instance of a ConcreteState subclass representing the current state.
    *   **State:** Defines an interface for encapsulating behavior associated with a particular state of the Context.
    *   **ConcreteState subclasses:** Each subclass implements behavior associated with a specific state.
*   **Implementation Notes:**
    *   **Defining Transitions:** Transitions can be defined in the Context (if criteria are fixed) or in the State subclasses (more flexible but introduces dependencies between subclasses).
    *   **Creation/Destruction:** Create state objects on-demand (saves space if states are rarely used) or pre-allocate them (higher performance if state changes are frequent).
    *   **Sharing:** If State objects have no instance variables (intrinsic state only), they can be shared as Flyweights.
    *   **Table-based alternative:** A transition table is more regular/data-driven but harder to attach actions to and less efficient than virtual functions.
*   **Consequences:**
    *   **Localizes State Behavior:** Puts all behavior for a specific state into one object, making it easy to add new states.
    *   **Explicit Transitions:** State changes are represented by re-binding a variable, not just updating data values, making transitions atomic and visible.
    *   **Class Explosion:** Can increase the number of classes, which is only beneficial if there are many states/complex logic.
*   **Related Patterns:**
    *   **Flyweight:** Used for sharing State objects.
    *   **Singleton:** State objects are often implemented as singletons.
    *   **Strategy:** Similar structure, but State handles behavior that changes based on internal state, while Strategy typically handles interchangeable algorithms.