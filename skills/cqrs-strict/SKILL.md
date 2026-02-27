---
name: cqrs-strict
description: Enforce strict CQRS separation between commands and queries in Spring Boot applications.
---

# Strict CQRS Discipline

## Purpose
Maintain a clear separation between write operations (commands) and read operations (queries).

---

## Structure

For each use case:

- Command
- CommandHandler
- Query
- QueryHandler

Controllers must delegate only to handlers.

---

## Command Rules
- Commands modify state.
- Commands must not return domain entities.
- Return identifiers or response DTOs.
- Transactions belong to command handlers.

---

## Query Rules
- Queries must not modify state.
- Queries must be side-effect free.
- Queries return DTOs, not entities.

---

## Architectural Constraints
- No mixed read/write services.
- No shared “Service” class handling everything.
- Each handler handles exactly one use case.

---

## Naming Convention
- `CreateProductCommand`
- `CreateProductCommandHandler`
- `GetProductQuery`
- `GetProductQueryHandler`

---

## Review Checklist
- Are responsibilities separated?
- Is transaction management placed correctly?
- Is any read logic leaking into command handlers?