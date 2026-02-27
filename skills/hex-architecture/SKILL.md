---
name: hex-architecture
description: Enforce hexagonal architecture in Spring Boot. Use when creating modules, adding adapters, or reviewing architecture boundaries.
---

# Hexagonal Architecture Enforcer (Spring Boot)

## Goal
Keep a strict separation between:
- Domain (pure business logic)
- Application (use cases / orchestration)
- Infrastructure (DB, HTTP, frameworks)

## Rules
1. Domain must not depend on Spring/JPA/HTTP.
2. Controllers call application layer only (commands/queries).
3. Repositories are ports in application/domain; JPA repos are adapters.
4. Mapping (DTO <-> Domain) happens at boundaries, not inside domain.
5. No business rules in controllers, mappers, or persistence models.

## When editing code
- Identify the layer of every new class.
- If a dependency crosses boundaries incorrectly, refactor to a port.