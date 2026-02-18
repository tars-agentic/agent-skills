## Chapter 8: Boundaries

### Managing Third-Party Interfaces
- **The Tension**: Providers seek broad applicability; users seek narrow, focused functionality.
- **Hide the Boundary**: Encapsulate third-party objects within a class. Do not pass them liberally throughout the system.
- **Avoid Leaky Abstractions**: Returning a third-party interface forces every caller to depend on that external library.
- **Evolution Buffer**: Wrappers ensure that when APIs change, you only have one place to update.
- **Wrap SDK Clients**: Wrap cloud/AI SDKs behind your own interface so you can swap providers without breaking logic.

### Learning Tests
- **Controlled Experiments**: Write unit tests to explore and verify your understanding of a third-party API.
- **Agent Learning**: Learning tests are even more valuable when an agent is integrating an unfamiliar library—write tests to verify assumptions before building on them.
- **Compatibility Insurance**: Run learning tests against new releases to detect breaking changes or behavioral shifts.
- **ROI**: Learning tests are "better than free"—they encode knowledge into executable documentation.

### Using Code That Does Not Yet Exist
- **Define the Ideal Interface**: Define the interface "you wish you had" based on your application's needs.
- **The Adapter Pattern**: Use an Adapter to bridge the gap between your ideal interface and the actual API.
- **Maintain Control**: Your code stays expressive and focused on its own domain, isolated from the quirks and instability of external systems.

### Summary & Agent Relevance
- **Thin Wrappers**: When generating code that uses a third-party API, prefer thin wrapper functions over scattering raw API calls.
- **Own Your Interfaces**: It is better to depend on something you control than something you don't.
- **Agent Relevance**: Agents integrate libraries they haven't "learned"—they pattern-match from training data. Learning tests and wrapper interfaces protect against stale or incorrect assumptions about API behavior.
