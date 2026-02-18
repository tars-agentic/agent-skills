## Chapter 4: Comments

- Comments are compensations for failure to express intent in code. The code is the only source of truth; comments age and mislead.
- Priority: invest energy in expressive naming and function extraction rather than explaining messes with comments.

### Good Comments
- **Legal Requirements**: Necessary headers for copyright, authorship, and licensing.
- **Informative**: Describing the return of an abstract method or a complex regex pattern.
- **Explanation of Intent**: Documenting the "why" behind a specific, non-obvious design choice.
- **Clarification**: Translating obscure arguments or return values from external libraries.
- **Warning of Consequences**: Alerting developers to side effects (e.g., "Thread-unsafe," "Slow").
- **TODO Reminders**: Marking tasks for future work (must be scanned and cleared regularly).
- **Amplification**: Emphasizing the critical importance of a seemingly minor piece of logic.
- **Public API Documentation**: Javadocs/Docstrings for shared libraries and public APIs.
- **Rationale & Constraints**: Explaining algorithm choice or mathematical/logic limits.

### Bad Comments
- **Redundant & Obvious**: Restating code (`i++`), noise, or mandated boilerplate.
- **Misleading & Rotting**: Inaccurate information, cut-paste errors, or decaying comments.
- **Visual Clutter**: Position markers (`// --- //`), HTML tags, or labeling closing braces.
- **Version Control Junk**: Journals, author bylines, or commented-out code (use Git instead).
- **Vague Mumbling**: Notes lacking context, nonlocal system data, or inobvious connections.
- **Procedural Crutches**: Using comments to explain messy logic instead of refactoring it.
- **Information Overload**: Irrelevant historical trivia, RFC specs, or technical lessons.
- **Venting & Unprofessionalism**: Emotional rants or complaints; improve the code instead.

### Agent relevance
AI agents systematically over-comment. Common anti-patterns: generating boilerplate docstrings for self-explanatory functions, adding "// increment i" style comments, and writing JSDoc for every getter/setter.
Rule of thumb: if the function name and signature fully describe what it does, skip the docstring.
