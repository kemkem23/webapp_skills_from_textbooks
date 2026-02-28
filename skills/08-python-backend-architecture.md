# Python Backend Architecture

**Source:** Architecture Patterns with Python (Harry Percival, Bob Gregory)
**Category:** Supplementary (A) — ถ้าเน้น Python backend architecture
**Intention:** patterns แบบ Pythonic, testability, DDD, event-driven services, ลดการผูกกับ framework มากเกินไป

---

## Key Skills

### 1. Domain-Driven Design (DDD) in Python
- Define the **domain model** as plain Python objects (no framework dependencies)
- Use **value objects** for immutable concepts (Money, Email, Address)
- Use **entities** for objects with identity and lifecycle (User, Order)
- Define **aggregates** — consistency boundaries around related entities
- Keep domain logic in the model, not in views/controllers/services

### 2. Repository Pattern
- Abstract data access behind a repository interface
- Domain model doesn't know about the database
- Repository handles persistence (ORM, raw SQL, etc.)
- Enables easy testing with in-memory fakes
- Example: `class AbstractRepository(abc.ABC)` with `add()` and `get()` methods

### 3. Service Layer
- Thin orchestration layer between API/views and the domain model
- Handles use cases: coordinate domain objects, call repositories, manage transactions
- Entry point for the application — views call service functions
- Keep it thin: business logic belongs in the domain, not the service layer

### 4. Unit of Work Pattern
- Manage transactions and commit/rollback as a unit
- Tie together repository operations under a single transaction
- Ensures atomicity of business operations
- Example: `with unit_of_work: ... uow.commit()`

### 5. Dependency Inversion
- High-level modules (domain) don't depend on low-level modules (database, framework)
- Both depend on abstractions (interfaces/protocols)
- Framework is a detail — the domain is the core
- Makes the codebase testable and framework-agnostic

### 6. Event-Driven Architecture
- Use **domain events** to decouple side effects from core logic
- Events represent things that happened: `OrderPlaced`, `PaymentReceived`
- **Event handlers** react to events asynchronously
- Enables eventual consistency between bounded contexts
- Use a message bus for internal event dispatch

### 7. Testing Strategy
- **Unit tests** — test domain model in isolation (no database, no framework)
- **Integration tests** — test repositories and services with a real database
- **End-to-end tests** — test the full stack through the API
- Test pyramid: many unit tests, fewer integration, fewest e2e
- Use fakes and in-memory implementations for fast unit tests

---

## Practical Application for Web Apps

| Pattern | When to Use |
|---------|-------------|
| Domain model | When business logic is complex enough to justify separation |
| Repository | Always — even simple apps benefit from abstracting data access |
| Service layer | When you have multiple entry points (API, CLI, background jobs) |
| Unit of Work | When operations span multiple repositories |
| Events | When actions trigger side effects (emails, notifications, analytics) |
| Dependency inversion | When you want testability and framework independence |

---

## Project Structure Example

```
src/
  domain/           # Pure Python domain model (no imports from framework/ORM)
    model.py        # Entities, value objects, aggregates
    events.py       # Domain events
  service_layer/    # Use case orchestration
    services.py     # Service functions
    unit_of_work.py # Transaction management
  adapters/         # Infrastructure implementations
    repository.py   # Database access (implements abstract repo)
    orm.py          # ORM mapping (SQLAlchemy, etc.)
  entrypoints/      # External interfaces
    api.py          # Flask/FastAPI routes
    cli.py          # Command-line interface
tests/
  unit/             # Fast tests against domain model
  integration/      # Tests with real database
  e2e/              # Full API tests
```

---

## Checklist

- [ ] Domain model is free of framework/ORM dependencies
- [ ] Repositories abstract all database access
- [ ] Service layer orchestrates use cases
- [ ] Business logic lives in the domain, not in views or services
- [ ] Tests can run against the domain model without a database
- [ ] Events decouple side effects from core business logic
- [ ] Project structure reflects architectural boundaries
