## Observer (Behavioral)

*   **Intent:** Define a 1-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
*   **Problem:** Maintaining consistency between related objects without tight coupling; avoiding re-implementing update logic across multiple views or dependents.
*   **When to Use:**
    *   An abstraction has two aspects, one dependent on the other.
    *   A change to one object requires changing others, and you don't know how many need to be changed.
    *   An object should be able to notify others without making assumptions about their identity.
*   **Participants:**
    *   **Subject:** Knows its observers; provides interface for attaching/detaching; sends notification.
    *   **Observer:** Defines an updating interface for objects to be notified of subject changes.
    *   **ConcreteSubject:** Stores state of interest; notifies observers when state changes.
    *   **ConcreteObserver:** Maintains reference to ConcreteSubject; stores state that must stay consistent with subject's; implements Update.
*   **Implementation Notes:**
    *   **Mapping:** Subject can store list of observers explicitly, or use a hash table to save space if subjects are numerous but observers are few.
    *   **Triggering Updates:** Updates can be triggered by state-setting operations in the Subject (automatic but potentially inefficient) or by clients (efficient but error-prone).
    *   **Push vs. Pull:** Pull model (minimal notification, observer queries subject) is more reusable but less efficient. Push model (subject sends detailed info) is efficient but assumes knowledge of observer needs.
    *   **Self-consistency:** Ensure subject state is consistent BEFORE calling `Notify()`. Use Template Method pattern to wrap calls.
    *   **ChangeManager:** A mediator can be used to manage complex update semantics (e.g., redundant updates in DAG dependencies).
*   **Consequences:**
    *   **Abstract Coupling:** Subject and Observer can vary independently and belong to different layers.
    *   **Broadcast Communication:** Notification is sent to all subscribers without specifying receivers.
    *   **Unexpected Updates:** Observers may be blind to the cost of a change, potentially causing cascading updates.
*   **Related Patterns:**
    *   **Mediator:** ChangeManager acts as a mediator.
    *   **Singleton:** ChangeManager is often a singleton.