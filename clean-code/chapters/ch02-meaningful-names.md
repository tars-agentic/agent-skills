## Chapter 2: Meaningful Names

### Use Intention-Revealing Names
*   The name should answer: why it exists, what it does, and how it is used.
*   If a name requires a comment, it has failed to reveal intent.
    *   Bad: `int d; // elapsed time in days`
    *   Good: `int elapsedTimeInDays;`
*   Avoid "implicity"—context must be explicit in the code itself.
    *   Bad: `if (x[0] == 4)` (Magic numbers/indices)
    *   Good: `if (cell.isFlagged())`

### Avoid Disinformation
*   Avoid words with specific technical meanings if you aren't using that structure.
    *   Bad: `accountList` (if it’s actually a Set or Map)
    *   Good: `accountGroup` or `accounts`
*   Avoid subtle naming differences that are hard to distinguish at a glance.
    *   Bad: `XYZControllerForEfficientHandlingOfStrings` vs. `XYZControllerForEfficientStorageOfStrings`
*   Avoid look-alike characters.
    *   Bad: Using `l` (lower-case L) or `O` (upper-case O) as variable names.

### Make Meaningful Distinctions
*   Don't just change a name to satisfy the compiler; make it mean something different.
*   Avoid "noise words" that add no information.
    *   Bad: `ProductInfo`, `ProductData`, `CustomerObject`
    *   Good: `Product`, `Customer`
*   Avoid number-series naming.
    *   Bad: `copyChars(char a1[], char a2[])`
    *   Good: `copyChars(char source[], char destination[])`

### Use Pronounceable and Searchable Names
*   If you can't pronounce it, you can't discuss it.
    *   Bad: `genymdhms`
    *   Good: `generationTimestamp`
*   Single-letter names and numeric constants are hard to find in a codebase.
*   The length of a name should correspond to the size of its scope.
    *   Bad: `for (int j=0; j<34; j++) s += (t[j]*4)/5;`
    *   Good: `for (int j=0; j < NUMBER_OF_TASKS; j++) { ... }`

### Avoid Encodings
*   Modern IDEs and type systems make Hungarian Notation and member prefixes obsolete.
    *   Bad: `m_description`, `s_name`, `iPhoneNumber`
    *   Good: `description`, `name`, `phoneNumber`
*   Don't encode interface-ness in the name; encode the implementation if necessary.
    *   Bad: `IShapeFactory`
    *   Good: `ShapeFactory` (Interface) and `ShapeFactoryImpl` (Concrete)

### Class and Method Naming
*   **Classes:** Use nouns or noun phrases. Avoid generic suffixes like `Manager` or `Data`.
    *   Good: `Customer`, `WikiPage`, `AddressParser`
*   **Methods:** Use verbs or verb phrases.
    *   Good: `postPayment`, `deletePage`, `save`
*   **Standardize:** Use `get`, `set`, and `is` for accessors/mutators/predicates.
*   **Static Factories:** Use descriptive static methods over overloaded constructors.
    *   Good: `Complex.FromRealNumber(23.0)` vs `new Complex(23.0)`

### One Word per Concept
*   Pick one term for a specific abstract concept and stick with it across classes.
    *   Bad: Mixing `fetch`, `retrieve`, and `get` for the same operation in different classes.
    *   Bad: Mixing `Manager`, `Controller`, and `Driver` for the same architectural role.
*   **Avoid Puns:** Don't use the same word for two different semantic actions.
    *   Bad: Using `add` for both "mathematical addition" and "inserting into a collection".

### Use Solution and Problem Domain Names
*   Use technical (CS) terms when appropriate for the implementation (Solution Domain).
    *   Good: `AccountVisitor`, `JobQueue`, `BinarySearch`
*   Use domain-specific terms when the logic is business-centric (Problem Domain).
    *   Good: `PostageRate`, `ClaimAudit`

### Add Meaningful Context
*   Wrap variables in well-named classes or functions to provide context.
    *   Bad: `state` (used alone, could be address state or machine state)
    *   Good: `address.state` or `Address` class fields.
*   **Avoid Gratuitous Context:** Don't add redundant prefixes to every class in a project.
    *   Bad: `GSDAccountAddress` in a "Gas Station Deluxe" app.
    *   Good: `Address`
