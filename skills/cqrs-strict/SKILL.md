---
name: cqrs-strict
description: Apply strict CQRS: separate commands from queries and handlers. Use when adding endpoints or use cases.
---

# Strict CQRS for Spring Boot

## Structure
- Command + CommandHandler for writes
- Query + QueryHandler for reads
- DTOs at the edges (controller/request/response)

## Rules
1. Commands never return domain entities; return ids or response DTOs.
2. Queries are side-effect free.
3. One handler per command/query.
4. Transactions only in command handlers (or application services).

## Checklist
- Naming consistent: CreateXCommand, CreateXHandler, GetXQuery, GetXHandler
- No “service god class”