## Chapter 5: Formatting

**Agent Relevance**: Auto-formatters handle spacing and indentation. What they DON'T handle is code ordering — where you place functions, how you group related code, and vertical distance between caller and callee. That's where these rules matter.

### Vertical Formatting
- **The Newspaper Metaphor**: Source files should read like a newspaper article.
  - Headline at the top (file/class name) tells you the high-level intent.
  - Topmost parts provide high-level concepts; detail increases as you move downward.
- **Vertical Openness**: Use blank lines to separate distinct thoughts and concepts.
- **Vertical Density**: Related lines of code should appear vertically dense.
- **Vertical Distance**: Closely related concepts should be kept vertically close.
  - **Variable Declarations**: Declare local variables as close to their usage as possible.
  - **Dependent Functions**: If one function calls another, they should be vertically close.
  - **Caller above Callee**: The calling function should be placed above the called function.
- **Conceptual Affinity**: Group functions that perform similar operations.
- **Vertical Ordering**: Function call dependencies should point downward.
- **File Size**: Strive for small files (typically < 200 lines).

### Horizontal Formatting (Readability Insights)
- **Operator Precedence**: Use white space to accentuate the precedence of operators.
  - Keep high-precedence factors together (e.g., `2*a`).
  - Separate low-precedence terms with spaces (e.g., `b*b - 4*a*c`).

### Team Rules
- **Agree once, follow always.** A consistent codebase from one team beats individually "better" styles. Configure a formatter and don't override it.
