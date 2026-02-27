---
name: testing-hexagonal
description: Enforce a layered testing strategy aligned with hexagonal architecture.
---

# Hexagonal Testing Strategy

## Domain Tests
- Pure JUnit.
- No Spring context.
- Test invariants and behavior.

---

## Application Tests
- Test handlers.
- Mock ports.
- No database.

---

## Infrastructure Tests
- Focused integration tests.
- Test repository implementations separately.

---

## Rules
- Avoid overusing @SpringBootTest.
- Tests must be deterministic and fast.
- Use clear naming: shouldDoX_whenY.