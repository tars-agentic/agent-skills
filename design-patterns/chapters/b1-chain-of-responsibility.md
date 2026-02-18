## Chain of Responsibility (Behavioral)

*   **Intent**: Decouple the sender of a request from its receiver by giving multiple objects a chance to handle it. Chain the receiving objects and pass the request along the chain until an object handles it.
*   **Problem**: A request must be handled by one of several objects, but the specific handler isn't known a priori and should be determined automatically without the sender needing to know the chain's structure.
*   **Participants**:
    *   **Handler**: Defines interface for handling requests; (optional) implements the successor link.
    *   **ConcreteHandler**: Handles requests it is responsible for; otherwise forwards to its successor.
    *   **Client**: Initiates the request to a ConcreteHandler object on the chain.
*   **When to Use**:
    *   Multiple objects can handle a request, and the handler isn't known beforehand.
    *   You want to issue a request to one of several objects without specifying the receiver explicitly.
    *   The set of objects that can handle a request should be specified dynamically.
*   **Implementation Notes**:
    *   **Successor Chain**: Can define new links in the Handler or use existing object references (e.g., parent references in a part-whole/Composite hierarchy).
    *   **Connecting Successors**: The Handler typically maintains the successor and provides a default `HandleRequest` that forwards the call.
    *   **Request Representation**:
        *   Hard-coded operations (e.g., `HandleHelp()`): Type-safe but fixed.
        *   Request codes/integers: Flexible but requires manual parameter packing and conditional dispatch.
        *   Request objects: Subclass a base `Request` class for type-safe parameter bundling and dynamic identification.
*   **Consequences**:
    *   **Reduced Coupling**: Objects don't need to know which other object handles a request; they only need a reference to a successor.
    *   **Flexibility**: Responsibilities can be added or changed at run-time by modifying the chain.
    *   **No Guarantee of Receipt**: A request can fall off the end of the chain if no handler takes responsibility.
*   **Related Patterns**:
    *   **Composite**: Often used together; a component's parent can act as its successor in the chain.
