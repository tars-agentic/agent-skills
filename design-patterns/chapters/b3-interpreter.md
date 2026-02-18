## Interpreter (Behavioral)

### Intent
- Define a representation for a language's grammar and an interpreter to evaluate sentences within that language.

### Problem
- A specific type of problem occurs frequently enough that it is better expressed as sentences in a simple language (e.g., regular expressions, boolean logic, SQL-like filters).
- Hard-coding algorithms for every variation of the problem is inefficient.

### When to Use
- The grammar is simple (complex grammars are better handled by parser generators).
- Efficiency is not a primary concern (direct tree interpretation is slower than bytecode or state machine execution).
- You need to represent statements as Abstract Syntax Trees (AST).

### Participants
- **AbstractExpression**: Declares an `Interpret(Context)` interface common to all nodes.
- **TerminalExpression**: Implements interpretation for terminal symbols (the "leaves" of the grammar).
- **NonterminalExpression**: Implements rules in the grammar; maintains sub-expressions and calls their `Interpret` operations recursively.
- **Context**: Stores global state/information required during interpretation (e.g., input string, symbol table).
- **Client**: Builds the AST and triggers the `Interpret` operation.

### Implementation Notes
- **AST Construction**: The pattern doesn't define how to parse; ASTs can be built by a separate parser or manually by the client.
- **Extending Behavior**: Use the **Visitor** pattern to add new operations (e.g., type-checking, pretty-printing) without changing grammar classes.
- **Efficiency**: For many terminal symbols, use **Flyweight** to share instances (e.g., constant values or common variables).
- **Mapping Rules**: Typically, one class is created per grammar rule.

### Consequences
- **Pros**: Easy to change/extend the grammar via inheritance; easy to implement basic grammars.
- **Cons**: Complex grammars lead to massive, unmanageable class hierarchies.

### Related Patterns
- **Composite**: The AST itself is usually a Composite.
- **Flyweight**: Useful for sharing terminal symbols.
- **Iterator**: Used to traverse the AST.
- **Visitor**: Encapsulates multiple "interpretations" (operations) on the AST.
