---
name: testing-hexagonal
description: Enforce a hexagonal testing strategy (domain/application/infrastructure). Use when writing or reviewing tests.
---

# Hexagonal Testing Strategy (Spring Boot)

## Levels
1. Domain tests: pure JUnit, no Spring.
2. Application tests: handlers with mocked ports.
3. Infrastructure tests: adapters (JPA, HTTP clients) with focused integration tests.

## Rules
- Avoid @SpringBootTest unless it's an end-to-end test.
- Tests must be fast, deterministic, and isolated.
- Arrange-Act-Assert, clear naming, no shared mutable fixtures.