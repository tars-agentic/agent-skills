# Design Patterns — Agent Skill

> Distilled from *Design Patterns: Elements of Reusable Object-Oriented Software* by Gamma, Helm, Johnson, Vlissides (1994).
> 23 patterns condensed into actionable reference material for AI coding agents.

## When to Use This Skill

Load this skill (or specific patterns) when:
- Designing class relationships and object interactions
- Choosing between inheritance and composition
- Decoupling components for flexibility and testability
- Recognizing a recurring structural or behavioral problem
- Reviewing generated code for pattern opportunities

## Pattern Catalog

### Creational Patterns — *How objects get created*

| Pattern | File | Lines | One-Line Intent |
|---------|------|-------|-----------------|
| Abstract Factory | c1-abstract-factory.md | 28 | Create families of related objects without specifying concrete classes |
| Builder | c2-builder.md | 36 | Separate construction of a complex object from its representation |
| Factory Method | c3-factory-method.md | 40 | Let subclasses decide which class to instantiate |
| Prototype | c4-prototype.md | 24 | Create objects by cloning a prototypical instance |
| Singleton | c5-singleton.md | 22 | Ensure a class has only one instance with a global access point |

### Structural Patterns — *How objects compose into larger structures*

| Pattern | File | Lines | One-Line Intent |
|---------|------|-------|-----------------|
| Adapter | s1-adapter.md | 25 | Convert one interface into another that clients expect |
| Bridge | s2-bridge.md | 31 | Decouple abstraction from implementation so both can vary |
| Composite | s3-composite.md | 30 | Treat individual objects and compositions uniformly via tree structures |
| Decorator | s4-decorator.md | 38 | Attach additional responsibilities dynamically without subclassing |
| Facade | s5-facade.md | 35 | Provide a unified interface to a set of interfaces in a subsystem |
| Flyweight | s6-flyweight.md | 29 | Use sharing to support large numbers of fine-grained objects efficiently |
| Proxy | s7-proxy.md | 26 | Provide a surrogate or placeholder to control access to an object |

### Behavioral Patterns — *How objects communicate and distribute responsibility*

| Pattern | File | Lines | One-Line Intent |
|---------|------|-------|-----------------|
| Chain of Responsibility | b1-chain-of-responsibility.md | 25 | Pass a request along a chain until some handler processes it |
| Command | b2-command.md | 30 | Encapsulate a request as an object for parameterization and undo |
| Interpreter | b3-interpreter.md | 36 | Define a grammar representation and an interpreter for sentences in it |
| Iterator | b4-iterator.md | 35 | Access elements of a collection sequentially without exposing internals |
| Mediator | b5-mediator.md | 37 | Define an object that encapsulates how a set of objects interact |
| Memento | b6-memento.md | 35 | Capture an object's state externally so it can be restored later |
| Observer | b7-observer.md | 25 | Notify dependents automatically when an object's state changes |
| State | b8-state.md | 23 | Let an object alter its behavior when its internal state changes |
| Strategy | b9-strategy.md | 28 | Define a family of interchangeable algorithms behind a common interface |
| Template Method | b10-template-method.md | 27 | Define an algorithm skeleton, deferring some steps to subclasses |
| Visitor | b11-visitor.md | 43 | Define new operations on a structure without changing its element classes |

## Problem-Based Navigation

**"I need to create objects flexibly"** → Abstract Factory, Factory Method, Builder, Prototype
**"I need exactly one instance"** → Singleton
**"I need to adapt an incompatible interface"** → Adapter
**"I need to add behavior without modifying classes"** → Decorator, Visitor
**"I need to simplify a complex subsystem"** → Facade
**"I need to represent part-whole hierarchies"** → Composite
**"I need to decouple abstraction from implementation"** → Bridge
**"I need to handle requests without coupling to a handler"** → Chain of Responsibility, Command
**"I need undo/redo or transaction logging"** → Command, Memento
**"I need to notify many objects of state changes"** → Observer
**"I need an object to change behavior based on state"** → State, Strategy
**"I need to iterate a collection without exposing structure"** → Iterator
**"I need to reduce coupling between many interacting objects"** → Mediator
**"I need to optimize memory for many similar objects"** → Flyweight
**"I need to control access to an object"** → Proxy

## Core Design Principles (from Introduction)

1. **Program to an interface, not an implementation** — depend on abstract types, not concrete classes
2. **Favor object composition over class inheritance** — composition is more flexible and avoids fragile hierarchies
3. **Encapsulate what varies** — identify the aspects that change and separate them from what stays the same

See `chapters/00-introduction.md` for the full design principles reference.

## File Structure

```
design-patterns/
├── SKILL.md                          ← this file
└── chapters/
    ├── 00-introduction.md            ← principles, taxonomy, mechanisms
    ├── c1-abstract-factory.md        ← Creational patterns (c1-c5)
    ├── c2-builder.md
    ├── c3-factory-method.md
    ├── c4-prototype.md
    ├── c5-singleton.md
    ├── s1-adapter.md                 ← Structural patterns (s1-s7)
    ├── s2-bridge.md
    ├── s3-composite.md
    ├── s4-decorator.md
    ├── s5-facade.md
    ├── s6-flyweight.md
    ├── s7-proxy.md
    ├── b1-chain-of-responsibility.md ← Behavioral patterns (b1-b11)
    ├── b2-command.md
    ├── b3-interpreter.md
    ├── b4-iterator.md
    ├── b5-mediator.md
    ├── b6-memento.md
    ├── b7-observer.md
    ├── b8-state.md
    ├── b9-strategy.md
    ├── b10-template-method.md
    └── b11-visitor.md
```
