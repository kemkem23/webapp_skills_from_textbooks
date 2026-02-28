# Production Readiness & Stability

**Source:** Release It! 2nd Edition (Michael Nygard)
**Category:** Core Reading
**Intention:** ออกแบบระบบให้ล้มแล้วฟื้นได้ เน้น failure modes, stability patterns, และบริบท DevOps/cloud-native

---

## Key Skills

### 1. Failure Mode Analysis
- Identify potential failure points (integration points, chain reactions, cascading failures)
- Understand that failures in production are inevitable — design for resilience
- Map dependencies and their failure characteristics

### 2. Stability Patterns
- **Circuit Breaker** — stop calling a failing service, allow recovery time
- **Bulkhead** — isolate failures so one component doesn't take down the whole system
- **Timeout** — never wait forever; always set timeouts on external calls
- **Retry with Backoff** — retry transient failures with exponential backoff and jitter
- **Steady State** — prevent resource leaks (logs, disk, memory, connections)
- **Handshaking** — let services negotiate load and health

### 3. Anti-Patterns to Avoid
- **Integration Point Traps** — unprotected calls to external services
- **Chain Reactions** — one failure triggering sequential failures across nodes
- **Cascading Failures** — failures propagating across system boundaries
- **Blocked Threads** — thread pools exhausted by slow responses
- **Unbounded Result Sets** — queries returning unlimited data

### 4. Deployment & Operations
- Design for zero-downtime deployment (rolling deploys, blue-green, canary)
- Implement health checks and readiness probes
- Plan for capacity and load management
- Use feature flags for safe rollouts

### 5. Transparency & Observability
- Log meaningful events, not just errors
- Implement structured logging for machine parsing
- Design dashboards that show system health at a glance
- Create runbooks for common failure scenarios

---

## Practical Application for Web Apps

| Skill | When to Apply |
|-------|---------------|
| Circuit breakers | Every external API call, database connection, third-party service |
| Timeouts | All network calls — HTTP, database, message queue |
| Bulkheads | Separate thread/connection pools per dependency |
| Health checks | Every service must expose health and readiness endpoints |
| Steady state | Log rotation, connection pool limits, cache eviction policies |

---

## Checklist Before Deploying to Production

- [ ] All external calls have timeouts configured
- [ ] Circuit breakers protect against cascading failures
- [ ] Connection pools are bounded and monitored
- [ ] Health check endpoints are implemented
- [ ] Deployment supports zero-downtime rollouts
- [ ] Rollback procedure is documented and tested
- [ ] Logging is structured and includes correlation IDs
- [ ] Resource cleanup is automated (logs, temp files, sessions)
