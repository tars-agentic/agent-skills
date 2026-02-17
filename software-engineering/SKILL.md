# Software Engineering Principles

A dense reference of timeless software engineering principles distilled from Hans van Vliet's *Software Engineering: Principles and Practice* (2007). This is not a tutorial — it is a lookup reference for AI coding agents who need to understand **why** codebases are structured the way they are.

## When to Use This Skill

- When working on existing codebases and needing to understand architectural patterns, design decisions, or quality attributes
- When planning task decomposition, risk assessment, or change management
- When reviewing code for quality, maintainability, or test coverage
- When interpreting ambiguous requirements or specifications
- When making design trade-offs (coupling vs cohesion, performance vs maintainability)

## Source

Van Vliet, H. (2007). *Software Engineering: Principles and Practice* (3rd ed.). Wiley.

Distilled through the lens of: what timeless SE wisdom still applies when agents — not humans — are writing, reviewing, and managing code?

## Chapters

| # | Title | Focus |
|---|-------|-------|
| 1 | Foundations of Software Engineering | Core principles, failure case studies, ethics |
| 2 | Systems Thinking and Project Discipline | Systems view, change control, quality-as-built-in |
| 3 | Software Process Models and Evolution | Lifecycle models, XP/TDD, Lehman's Laws |
| 4 | Configuration Management | SCM, branching, CI/CD, baselines |
| 5 | Coordination and Communication | Scaling laws, coordination mechanisms, agent patterns |
| 6 | Software Quality | Quality models, metrics, reviews, inspections |
| 7 | Complexity and Effort Scaling | Diseconomy of scale, Brooks' Law, estimation |
| 8 | Task Planning, Decomposition, and Risk | WBS, critical path, risk management, project taxonomy |
| 9 | Requirements Understanding | Requirement types, seven sins, MoSCoW, traceability |
| 10 | Structural and Behavioral Modeling | OO concepts, state machines, data flow, CRC |
| 11 | Software Architecture | Architectural styles, views, ATAM, trade-offs, ADRs |
| 12 | Software Design | Information hiding, cohesion/coupling, patterns, metrics |
| 13 | Software Testing | Coverage criteria, TDD, integration, regression |
| 14 | Maintenance, Evolution, Technical Debt | Code smells, Lehman's Laws, refactoring, evolution analysis |
| 15 | Tool Philosophy and Composition | UNIX philosophy, tool integration, methodology primacy |

## Usage

Load individual chapters as needed — do not load all 15 at once. Start with the chapter most relevant to the current task:

- **Writing new code?** → ch11 (Architecture) + ch12 (Design)
- **Reviewing code?** → ch06 (Quality) + ch14 (Maintenance/Smells)
- **Writing tests?** → ch13 (Testing)
- **Planning work?** → ch08 (Planning) + ch09 (Requirements)
- **Managing changes?** → ch04 (Config Management)
- **Debugging process issues?** → ch03 (Process Models) + ch07 (Complexity)

Chapter files are in `chapters/ch01.md` through `chapters/ch15.md`.
