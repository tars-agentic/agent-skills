## Chapter 1: Clean Code

- **Code is the final truth**: Even “requirements” and DSLs become formal, executable specifications. You can’t abstract away precision.
- **LeBlanc’s Law**: “Later equals never.” Deferring cleanup is usually permanent.
- **Speed Paradox**: The only way to go fast is to stay clean; messes slow you immediately and compound.
- **The 10:1 Ratio**: We spend ~10× more time reading than writing. Optimize for readability.
- **Continuous improvement (Boy Scout Rule)**: Leave code cleaner than you found it; avoid “grand redesign” fantasies.
- **What clean code feels like (Cunningham)**: Each routine is “pretty much what you expected.” Surprise is a smell.
- **What clean code contains (Beck’s rules)**: Runs tests → no duplication → expresses intent → minimal entities.
- **Code-sense**: Recognizing clean code isn’t enough; you need disciplined, behavior-preserving refactoring to get there.

**Agent relevance:**
Agents are prone to ship a working mess and move on. Treat readability + tests as the constraint, not a nice-to-have; small cleanups per change beat “we’ll refactor later.”
