---
name: clean-java
description: Enforce clean, readable and maintainable Java code. Apply when creating or refactoring classes, methods, or business logic.
---

# Clean Java Conventions

## Purpose
Ensure Java code is readable, maintainable, intention-revealing, and aligned with professional enterprise standards.

## Core Principles
- Code must express intent clearly.
- Avoid cleverness and implicit behavior.
- Prefer clarity over abstraction.
- Small, cohesive classes and methods.

---

## Naming Rules
- Class names must represent business concepts.
- Method names must describe actions precisely.
- Avoid generic names like `process`, `handle`, `data`, `manager`.
- Boolean methods must read naturally (`isActive`, `hasPermission`).

---

## Method Rules
- One responsibility per method.
- Prefer guard clauses over nested conditionals.
- Avoid boolean flags as parameters.
- Extract complex logic into private methods with meaningful names.
- No methods longer than ~20-30 lines unless justified.

---

## Object Design
- Prefer immutability when possible.
- Use constructor injection.
- Avoid field injection.
- Avoid exposing internal mutable state.
- Do not return null; use Optional where appropriate.

---

## Code Smells to Prevent
- God classes
- Feature envy
- Long parameter lists
- Primitive obsession
- Anemic domain models (when domain logic is expected)

---

## When Reviewing Code
- Can a new developer understand this in minutes?
- Does each class have a clear responsibility?
- Are dependencies justified?