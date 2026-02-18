## Command (Behavioral)

*   **Intent**: Encapsulate a request as an object, letting you parameterize clients with different requests, queue or log requests, and support undoable operations.
*   **Problem**: Issuing requests to objects without knowing the operation being requested or the receiver of the request (e.g., a menu item needs to perform an action on a document it doesn't know).
*   **Participants**:
    *   **Command**: Declares an interface for executing an operation (`Execute`).
    *   **ConcreteCommand**: Defines binding between a Receiver and an action; implements `Execute` by invoking operations on the Receiver.
    *   **Client**: Creates ConcreteCommand and sets its Receiver.
    *   **Invoker**: Asks the command to carry out the request.
    *   **Receiver**: Knows how to perform the work associated with the request.
*   **When to Use**:
    *   Parameterize objects by an action (object-oriented replacement for callbacks).
    *   Specify, queue, and execute requests at different times (independent lifetimes).
    *   Support undo/redo by storing state for reversing effects (`Unexecute`).
    *   Support logging changes for recovery after system crashes.
    *   Structure a system around high-level operations built on primitives (transactions).
*   **Implementation Notes**:
    *   **Intelligence**: Commands vary from simple bindings (delegating to Receiver) to implementing everything themselves (if no receiver exists).
    *   **Undo/Redo**: Requires storing state (Receiver, arguments, original values). A history list manages multiple levels. Commands may need to be copied (Prototype pattern) before being stored.
    *   **MacroCommands**: Use a composite command to manage a sequence of subcommands.
    *   **Templates (C++)**: Can be used for simple, non-undoable commands to avoid subclassing for every action/receiver pair.
*   **Consequences**:
    *   **Decouples** the invoker from the object that performs the operation.
    *   Commands are **first-class objects**; they can be manipulated and extended.
    *   Easy to add new commands without changing existing classes.
    *   Commands can be assembled into **Composite Commands**.
*   **Related Patterns**:
    *   **Composite**: Used to implement MacroCommands.
    *   **Memento**: Can keep state required for undo without exposing Receiver internals.
    *   **Prototype**: Commands that must be copied before joining a history list.
