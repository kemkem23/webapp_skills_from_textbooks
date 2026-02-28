# Evolutionary Architecture

**Source:** Building Evolutionary Architectures, 2nd Edition (Neal Ford, Rebecca Parsons, Patrick Kua)
**Category:** Supplementary (B) — ถ้าจะออกแบบระบบให้เปลี่ยนง่ายระยะยาว
**Intention:** evolutionary design, automated governance, fitness functions เพื่อให้สถาปัตยกรรมปรับตัวตามธุรกิจได้

---

## Key Skills

### 1. Evolutionary Design Principles
- Architecture should evolve incrementally, not be designed upfront in full
- Support **guided change** — evolution with guardrails, not chaos
- Design for change: make it easy to modify, replace, and extend components
- Avoid the "big rewrite" — evolve continuously instead

### 2. Architectural Fitness Functions
- Automated tests that verify architecture characteristics are maintained
- Examples:
  - **Performance fitness function** — response time stays below threshold
  - **Coupling fitness function** — no circular dependencies between modules
  - **Security fitness function** — no known vulnerabilities in dependencies
  - **Scalability fitness function** — load test passes at expected capacity
- Run fitness functions in CI/CD pipeline to catch architectural drift
- Treat architecture rules like code — test them automatically

### 3. Incremental Change
- Make small, reversible architectural changes
- Use **expand and contract** (parallel change) for breaking changes:
  1. Expand: add new implementation alongside old
  2. Migrate: move consumers to new implementation
  3. Contract: remove old implementation
- Feature flags to safely deploy architectural changes
- Strangler fig pattern for gradual migration from legacy systems

### 4. Appropriate Coupling
- Not all coupling is bad — intentional coupling is fine
- Reduce **inappropriate coupling** — dependencies that make change hard
- Use contracts (APIs, schemas) to manage coupling between services
- Understand different coupling types: implementation, temporal, spatial, semantic

### 5. Governance Through Automation
- Replace manual architecture review with automated checks
- ArchUnit / dependency-cruiser for enforcing dependency rules
- Custom linters for project conventions
- Automated dependency update scanning (Dependabot, Renovate)
- Architecture Decision Records (ADRs) for documenting choices

### 6. Managing Technical Debt
- Identify and categorize technical debt
- Use fitness functions to prevent new debt accumulation
- Allocate time for debt reduction in each iteration
- Distinguish between deliberate and accidental debt

---

## Practical Application for Web Apps

| Technique | Implementation |
|-----------|---------------|
| Fitness functions | CI checks for performance budgets, dependency rules, security scans |
| Expand and contract | Database migrations: add new column → migrate data → drop old column |
| Strangler fig | Route new features to new service, old features still on monolith |
| Automated governance | ArchUnit tests, ESLint rules, import restrictions |
| ADRs | Markdown files in `docs/decisions/` tracked in version control |

---

## Checklist for Evolutionary Architecture

- [ ] Architecture characteristics are identified and prioritized
- [ ] Fitness functions validate key characteristics automatically
- [ ] Fitness functions run in CI/CD pipeline
- [ ] Breaking changes use expand-and-contract pattern
- [ ] Architecture decisions are recorded in ADRs
- [ ] Dependency rules are enforced automatically
- [ ] Technical debt is tracked and addressed regularly
- [ ] Architecture can evolve without "big bang" rewrites
