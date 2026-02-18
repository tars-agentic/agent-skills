## Chapter 3: Functions

### Core Philosophy
- **Functions should be small.** Then smaller than that.
- **Do One Thing.** A function does one thing if it performs only those steps that are one level below the stated name.
- **One Level of Abstraction.** All statements in a function must stay at the same level. If you can extract a function with a meaningful name, the original had mixed levels.
- **The Stepdown Rule.** Code should read like a top-down narrative. Every function should be followed by those at the next level of abstraction.
- **Sections are a smell.** If a function has distinct sections (setup, logic, cleanup), it's doing more than one thing.

### Size and Structure
- **Length:** Ideally 2–4 lines. Rarely more than 20.
- **Blocks:** `if`, `else`, and `while` blocks should be one line long (usually a function call).
- **Indentation:** Functions should not be large enough to hold nested structures. Max indent level: 1 or 2.

### Naming
- **Be Descriptive:** A long, descriptive name is better than a short, enigmatic one or a comment.
- **Use Verbs:** Functions are verbs; name them as verb/noun pairs (e.g., `writeField(name)`).
- **Consistency:** Use the same phrases, nouns, and verbs across the module (e.g., `includeSetupPage`, `includeTeardownPage`).

### Function Arguments
- **Ideal Count:** 0 (niladic) is best, followed by 1 (monadic) and 2 (dyadic).
- **Avoid Triads:** 3 arguments are hard; 4+ (polyadic) require special justification and should generally be avoided.
- **Flag Arguments:** Never pass booleans into a function. It loudly proclaims the function does more than one thing.
  - *Bad:* `render(boolean isSuite)`
  - *Good:* `renderForSuite()`, `renderForSingleTest()`
- **Argument Objects:** If a function needs 2–3+ arguments, wrap some in a class.
  - *Bad:* `makeCircle(double x, double y, double radius)`
  - *Good:* `makeCircle(Point center, double radius)`
- **Varargs:** If variable arguments are treated identically, they're equivalent to a single `List` argument. Use sparingly.

### Side Effects (Hidden Lies)
- **Promises:** A function must not do hidden things (e.g., modifying globals or session state) not implied by its name.
- **Temporal Coupling:** Side effects often force a caller to call functions in a specific order.
- **Output Arguments:** Avoid them. If a state must change, change the state of the owning object.
  - *Bad:* `appendFooter(report)`
  - *Good:* `report.appendFooter()`

### Command Query Separation (CQS)
- **Principle:** Functions should either *do* something (command) or *answer* something (query), but not both.
- *Bad (Ambiguous):* `if (set("username", "unclebob"))` — Is it checking if set or performing the set?
- *Good:*
  ```java
  if (attributeExists("username")) {
      setAttribute("username", "unclebob");
  }
  ```

### Error Handling
- **Prefer Exceptions:** Don't return error codes. Error codes force the caller to deal with the error immediately, leading to nested `if` structures.
- **Error Handling is "One Thing":** A function that handles errors should do nothing else.
- **Extract Try/Catch:** Extract the bodies of try/catch blocks into their own functions.
  ```java
  public void delete(Page page) {
      try {
          deletePageAndAllReferences(page);
      } catch (Exception e) {
          logError(e);
      }
  }
  ```

### Switch Statements
- **The Problem:** Switch statements inherently do "N things" and violate SRP/OCP.
- **The Rule:** Bury switch statements in a low-level factory to create polymorphic objects; never repeat them.

### Duplication (DRY)
- **Principle:** Duplication is the root of all evil in software. Eliminate it via subroutines, base classes, or modules.

### How to Write Clean Functions
1. **First Draft:** Write it to work. It will be long, messy, and complex.
2. **Refine:** Massage, split functions, rename, and eliminate duplication.
3. **Requirement:** Maintain a suite of unit tests to ensure the code stays functional during refactoring.