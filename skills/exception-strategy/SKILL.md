---
name: exception-strategy
description: Enforce a consistent and layered exception handling strategy in Spring Boot hexagonal architectures.
---

# Exception Handling Strategy (Spring Boot + Hexagonal)

## Purpose

Define a consistent, predictable and layered error handling policy.

Goals:

- Separate domain errors from application and infrastructure errors.
- Avoid leaking internal implementation details.
- Provide meaningful HTTP responses.
- Ensure maintainability and observability.

---

# 1. Exception Layers

Exceptions must respect architectural boundaries.

## Domain Layer

Used for business rule violations.

Characteristics:
- Extend DomainException (custom base class).
- Represent business invariants.
- Must not depend on Spring.
- Must not contain HTTP concepts.

Examples:
- ProductAlreadyExistsException
- InvalidPriceException
- OrderCannotBeCancelledException

Domain exceptions represent business truth, not technical failure.

---

## Application Layer

Used for orchestration or use-case level issues.

Characteristics:
- Extend ApplicationException.
- Wrap or translate domain exceptions when needed.
- Represent use-case failure, not HTTP errors.

Example:
- CreateProductFailedException

Application exceptions coordinate between domain and infrastructure.

---

## Infrastructure Layer

Used for technical or external failures.

Characteristics:
- Extend InfrastructureException.
- Represent DB errors, HTTP client failures, IO issues.
- Must not leak vendor-specific details.

Examples:
- DatabaseAccessException
- ExternalServiceUnavailableException

Infrastructure exceptions must be translated before reaching the controller.

---

# 2. HTTP Mapping Strategy

Controllers must not manually handle exceptions.

Use a global @ControllerAdvice to:

- Translate DomainException → 400 / 409
- Translate ApplicationException → 400
- Translate InfrastructureException → 503
- Catch unexpected RuntimeException → 500

Never expose:
- Stack traces
- Internal class names
- SQL details
- Framework-specific messages

---

# 3. Error Response Structure

All error responses must follow a consistent format.

Example structure:

{
  "timestamp": "...",
  "error": "BUSINESS_RULE_VIOLATION",
  "message": "Product already exists",
  "path": "/products"
}

Rules:
- Message must be safe and client-readable.
- No internal debugging details.
- Use error codes when relevant.

---

# 4. Prohibited Patterns

- Throwing generic RuntimeException.
- Returning null instead of throwing meaningful exceptions.
- Catching exceptions silently.
- Using exceptions for control flow.
- Controllers wrapping everything in try/catch blocks.
- Throwing HTTP exceptions inside domain layer.

---

# 5. Logging Policy

- Domain exceptions → INFO or WARN.
- Infrastructure failures → ERROR.
- Unexpected exceptions → ERROR with correlation id.

Logging must not duplicate stack traces in multiple layers.

---

# 6. Design Rules

- Define base abstract classes:
    - DomainException
    - ApplicationException
    - InfrastructureException

- Each exception must have:
    - Clear name
    - Clear intent
    - Single responsibility

- Exceptions must express business meaning, not technical noise.

---

# 7. Review Checklist

When reviewing code:

- Does this exception belong to the correct layer?
- Is the exception name meaningful?
- Is any technical detail leaking to the client?
- Are controllers clean and free of try/catch blocks?
- Are business invariants enforced in domain and not in controller?

---

# 8. Architectural Principle

Exceptions are part of the domain language.

They are not implementation details.
They represent boundaries of correctness in the system.