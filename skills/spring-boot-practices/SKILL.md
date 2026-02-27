---
name: spring-boot-practices
description: Apply Spring Boot best practices aligned with clean architecture.
---

# Spring Boot Best Practices

## Controllers
- Thin controllers.
- Only mapping + delegation.
- No business logic.

---

## Transactions
- Use @Transactional only in command handlers or application services.
- Never in controllers.

---

## DTO Mapping
- Never expose JPA entities.
- Use dedicated mappers.
- Mapping belongs at boundaries.

---

## Configuration
- Use configuration properties.
- Avoid hardcoded values.
- Use profiles correctly.

---

## Validation
- Validate at boundaries.
- Domain must enforce invariants independently.

---

## Dependency Injection
- Constructor injection only.