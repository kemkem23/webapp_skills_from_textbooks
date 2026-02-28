# Twelve-Factor App Methodology

**Source:** The Twelve-Factor App (Adam Wiggins / Heroku)
**Category:** Core Reading
**Intention:** หลักการสำคัญก่อน deploy — config แยกจากโค้ด, dev/prod parity, logs, process model, portability

---

## Key Skills

### 1. Codebase Management
- **One codebase, many deploys** — single repo tracked in version control, deployed to multiple environments
- Never share code between apps by copying; use libraries/packages instead

### 2. Dependency Management
- **Explicitly declare and isolate dependencies** — use package managers (pip, npm, go mod)
- Never rely on system-wide packages being pre-installed
- Lock dependency versions for reproducible builds

### 3. Configuration
- **Store config in environment variables** — never hardcode credentials, URLs, or environment-specific values
- Config varies between deploys; code does not
- Validate config at startup, fail fast on missing values

### 4. Backing Services
- **Treat backing services as attached resources** — databases, caches, queues, email services
- Swap local for third-party services without code changes
- Connect via URL/credentials stored in config

### 5. Build, Release, Run
- **Strictly separate build, release, and run stages**
- Build: compile code + bundle dependencies
- Release: combine build + config
- Run: execute the release in the environment

### 6. Processes
- **Execute the app as stateless processes** — store nothing in local memory/filesystem between requests
- Use backing services (database, cache) for persistent state
- Sticky sessions violate twelve-factor

### 7. Port Binding
- **Export services via port binding** — the app is self-contained and listens on a port
- No reliance on runtime injection of a web server

### 8. Concurrency
- **Scale out via the process model** — scale by running multiple processes, not by threading within one large process
- Different process types for different workloads (web, worker, scheduler)

### 9. Disposability
- **Maximize robustness with fast startup and graceful shutdown**
- Handle SIGTERM gracefully
- Design for crash-only software (safe to kill at any time)

### 10. Dev/Prod Parity
- **Keep development, staging, and production as similar as possible**
- Same backing services, same OS, same dependencies
- Reduce time gap, personnel gap, and tools gap between environments

### 11. Logs
- **Treat logs as event streams** — write to stdout, let the environment handle collection
- Never write to or manage log files within the app
- Use structured logging (JSON) for machine parsing

### 12. Admin Processes
- **Run admin/management tasks as one-off processes** — migrations, REPL, data fixes
- Run in the same environment with the same codebase and config

---

## Practical Application for Web Apps

| Factor | Implementation Example |
|--------|----------------------|
| Config | Use `.env` files locally, environment variables in production |
| Backing services | Database URL as env var, swappable between local and cloud |
| Stateless processes | Store sessions in Redis/database, not in-memory |
| Logs as streams | Write to stdout, use log aggregator (ELK, CloudWatch, Loki) |
| Dev/prod parity | Use Docker to replicate production environment locally |
| Disposability | Implement graceful shutdown handlers in your web server |

---

## Checklist Before Deploying

- [ ] No hardcoded config — all config comes from environment variables
- [ ] Dependencies are explicitly declared and locked
- [ ] App is stateless — no local file/memory state between requests
- [ ] Logs go to stdout/stderr
- [ ] App starts fast and shuts down gracefully
- [ ] Build, release, and run stages are separated
- [ ] Dev environment mirrors production (Docker, same services)
- [ ] Admin tasks (migrations) run as one-off processes
