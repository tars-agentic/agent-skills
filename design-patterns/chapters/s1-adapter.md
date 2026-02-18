## Adapter (Structural)

*   **Intent:** Convert the interface of a class into another interface clients expect, letting incompatible classes work together.
*   **Problem:** A toolkit or legacy class is unusable because its interface doesn't match the domain-specific interface required by an application.
*   **Participants:**
    *   **Target:** Defines the domain-specific interface the Client uses.
    *   **Client:** Collaborates with objects conforming to the Target interface.
    *   **Adaptee:** The existing interface that needs adapting.
    *   **Adapter:** Adapts the Adaptee interface to the Target interface.
*   **When to Use:**
    *   You want to use an existing class with an incompatible interface.
    *   You need a reusable class that cooperates with unforeseen or unrelated classes.
    *   (Object adapter) You need to adapt several existing subclasses without subclassing each one.
*   **Implementation Notes:**
    *   **Class Adapter:** Uses multiple inheritance; inherits Target interface and Adaptee implementation (often private inheritance in C++).
    *   **Object Adapter:** Uses object composition; Adapter contains an instance of Adaptee and delegates requests.
    *   **Pluggable Adapters:** Build interface adaptation into the class itself using abstract operations, delegate objects, or parameterized blocks.
    *   **Two-way Adapters:** Useful for transparency when two different clients need to see an object differently; requires multiple inheritance.
*   **Consequences:**
    *   **Class Adapter:** Commits to a concrete Adaptee; cannot adapt a class and its subclasses; allows overriding Adaptee behavior; no extra indirection.
    *   **Object Adapter:** Adapts Adaptee and all its subclasses; harder to override Adaptee behavior (requires subclassing Adaptee).
    *   **Transparency:** Adapters are generally not transparent to clients expecting the original Adaptee interface.
*   **Related Patterns:**
    *   **Bridge:** Separates interface from implementation (design-time); Adapter changes an existing interface (retrofitting).
    *   **Decorator:** Enhances an object without changing its interface; more transparent than Adapter.
    *   **Proxy:** Provides a surrogate for an object without changing its interface.