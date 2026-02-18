## Chapter 7: Error Handling

### 1. Prefer Exceptions to Return Codes
- Return codes force the caller to handle errors immediately, cluttering business logic.
- Exceptions allow a clean separation of concerns: the algorithm vs. error handling.
- Using exceptions avoids the "forgetting to check" failure mode inherent in return codes.
- Caller code remains focused on the happy path, improving readability and maintainability.

### 2. The Try-Catch-Finally Structure
- Treat `try` blocks as transactions; the `catch` must leave the system in a consistent state.
- Write the `try-catch-finally` statement first when developing logic that can fail.
- This defines the scope of the operation and what the user should expect on failure.
- Use TDD to force exceptions early, ensuring handlers are robust before adding logic.

### 3. Use Unchecked Exceptions
- Checked exceptions violate the Open/Closed Principle (OCP).
- A low-level change (adding a `throws`) forces signature changes through all calling layers.
- This breaks encapsulation as every intermediate function must know about the error.
- Most modern languages (C#, Python, Ruby) succeed without checked exceptions.
- Reserve checked exceptions only for critical libraries where recovery is mandatory.

### 4. Provide Meaningful Context
- Every exception should convey the intent of the operation that failed, not just a stack trace.
- Create informative error messages including the operation name and failure type.
- Ensure enough information is passed to allow effective logging at the catch site.

### 5. Define Exceptions by Caller Needs
- Classify exceptions based on how they are caught rather than how they are generated.
- Wrap third-party APIs to translate their diverse exceptions into a single, usable type.
- Wrapping minimizes dependencies, makes mocking easier, and allows a custom, cleaner API.
- Only create unique exception classes if you need to catch them differently.

### 6. The Special Case Pattern (Normal Flow)
- Avoid "awkward" error handling that interrupts logic to handle missing data/logic.
- Instead of catching an exception to handle a default, return a Special Case object.
- The Special Case object (or Null Object) implements the interface with default behavior.
- This moves error handling to the edges and keeps the main algorithm unadorned.

### 7. Eliminate Null (The Billion Dollar Mistake)
- **Don't Return Null**: It forces callers to implement repetitive, brittle null checks.
- One missing null check leads to a `NullPointerException` and application instability.
- Instead of returning null, throw an exception or return a Special Case/Empty Collection.
- Use `Collections.emptyList()` or similar language features to handle missing sets.
- **Don't Pass Null**: Passing null is worse than returning it; it invites runtime errors.
- Assertions are "documentation" but don't solve the runtime risk; forbid null inputs by default.
- If an API returns null, wrap it immediately to prevent null from leaking into your core.

### 8. Robust AI Design Summary
- Treat error handling as a cross-cutting concern to be reasoned about independently.
- Clean code is robust; robustness comes from separation of concerns.
- Prioritize exception-based flow over conditional error checking.
- Enforce null-safety at the boundaries to prevent internal pollution.
