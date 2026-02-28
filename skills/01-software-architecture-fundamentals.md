# Software Architecture Fundamentals

**Source:** Fundamentals of Software Architecture (Mark Richards, Neal Ford)
**Category:** Core Reading
**Intention:** ปูพื้นฐานเรื่อง architectural characteristics, patterns, และการตัดสินใจเชิงสถาปัตย์ก่อนออกแบบโครงเว็บแอปทั้งระบบ

---

## Key Skills

### 1. Architectural Characteristics Analysis
- Identify quality attributes (performance, scalability, availability, security, maintainability)
- Prioritize characteristics based on business requirements
- Understand trade-offs between competing characteristics

### 2. Architecture Patterns
- **Layered Architecture** — separation of concerns across presentation, business, persistence, database layers
- **Microkernel Architecture** — plugin-based extensibility
- **Event-Driven Architecture** — asynchronous communication via events
- **Microservices Architecture** — independently deployable services
- **Service-Based Architecture** — coarser-grained services as a practical middle ground

### 3. Architectural Decision Making
- Document decisions using Architecture Decision Records (ADRs)
- Evaluate trade-offs systematically (no perfect architecture exists)
- Understand the "least worst" approach to choosing patterns

### 4. Component Design
- Identify and define components from business requirements
- Determine component boundaries and communication styles
- Balance cohesion and coupling

### 5. Architecture Governance
- Define fitness functions to validate architecture characteristics
- Establish review processes for architectural changes
- Monitor architectural drift over time

---

## Practical Application for Web Apps

| Skill | When to Apply |
|-------|---------------|
| Characteristics analysis | Before starting any new project — define what matters most |
| Pattern selection | When deciding monolith vs. microservices vs. hybrid |
| ADRs | Every significant technical decision (database choice, framework, API style) |
| Component design | When structuring modules, services, or packages |
| Fitness functions | In CI/CD pipelines to enforce architecture rules |

---

## Checklist Before Building

- [ ] Define top 3-5 architectural characteristics for the system
- [ ] Choose an architecture pattern that supports those characteristics
- [ ] Document the decision and trade-offs in an ADR
- [ ] Identify major components and their responsibilities
- [ ] Define communication patterns between components
- [ ] Plan how to validate architecture over time (fitness functions)
