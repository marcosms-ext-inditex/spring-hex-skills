---
name: hex-architecture
description: Enforce strict hexagonal (ports and adapters) architecture in Spring Boot projects.
---

# Hexagonal Architecture Enforcement

## Layers

- Domain
- Application
- Infrastructure

---

## Dependency Rule
Dependencies must always point inward:

Infrastructure → Application → Domain

Domain must depend on nothing external.

---

## Ports
- Defined in application or domain.
- Represent contracts to the outside world.

---

## Adapters
- Infrastructure implements ports.
- Controllers are inbound adapters.
- Repositories are outbound adapters.

---

## Prohibited Patterns
- Domain importing Spring annotations.
- Controllers accessing repositories directly.
- Application layer depending on JPA entities.

---

## Review Questions
- Does any layer depend on outer frameworks?
- Is domain pure and framework-independent?