---
name: ddd-tactical
description: Apply Domain-Driven Design tactical patterns in the domain layer.
---

# DDD Tactical Patterns

## Purpose
Model business logic using rich domain models instead of anemic structures.

---

## Entities
- Must have identity.
- Must protect invariants.
- No public setters that break consistency.

---

## Value Objects
- Immutable.
- Equality based on value.
- Validate consistency at creation.

---

## Aggregates
- Enforce invariants inside the aggregate root.
- External objects must modify state only through the root.
- Keep aggregates small and consistent.

---

## Domain Services
- Only when logic does not naturally belong to an entity or value object.
- Must represent real business concepts.

---

## Repositories
- Defined as interfaces in domain/application.
- Infrastructure provides implementation.
- Repositories return aggregates, not persistence models.

---

## Anti-Patterns to Avoid
- Anemic models.
- Exposing JPA entities directly.
- Business rules inside controllers.