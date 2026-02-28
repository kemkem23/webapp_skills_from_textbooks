# DevOps & Deployment Performance

**Source:** The DevOps Handbook + Accelerate (Nicole Forsgren, Jez Humble, Gene Kim)
**Category:** Core Reading
**Intention:** pipeline, team flow, deployment performance, และการวัดผลเชิงสถิติ

---

## Key Skills

### 1. DORA Metrics (Four Key Metrics)
- **Deployment Frequency** — how often code is deployed to production
- **Lead Time for Changes** — time from commit to production
- **Mean Time to Restore (MTTR)** — time to recover from a failure
- **Change Failure Rate** — percentage of deployments causing failures
- These metrics are statistically proven to predict software delivery performance

### 2. Continuous Integration (CI)
- Every developer commits to trunk/main at least daily
- Automated build and test on every commit
- Fix broken builds immediately (within minutes)
- Keep the build fast (under 10 minutes ideally)
- Use trunk-based development or short-lived feature branches

### 3. Continuous Delivery (CD)
- Every commit is a release candidate
- Deployment pipeline: build → unit test → integration test → staging → production
- Automate everything: build, test, deploy, infrastructure provisioning
- Deployments should be routine, low-risk events

### 4. Infrastructure as Code (IaC)
- Define all infrastructure in version-controlled code (Terraform, Pulumi, CloudFormation)
- Environments are reproducible from code
- No manual changes to production infrastructure (cattle, not pets)
- Test infrastructure changes the same way you test application code

### 5. Feedback Loops
- Shorten all feedback loops:
  - Fast tests → developers get results in minutes
  - Production telemetry → teams see impact of changes
  - User feedback → deploy experiments and measure outcomes
- Shift left: catch problems earlier (security scanning in CI, linting, type checking)

### 6. Team Culture & Flow
- Cross-functional teams own the full lifecycle (build it, run it)
- Reduce handoffs between teams (dev → ops → QA = slow)
- Blameless culture encourages learning from failures
- Work in small batches to reduce risk and increase flow
- Limit work in progress (WIP) to improve throughput

### 7. Value Stream Mapping
- Map the entire path from idea to production
- Identify bottlenecks and waste (waiting, handoffs, rework)
- Optimize the constraint (not everything at once)
- Measure and improve continuously

---

## Practical Application for Web Apps

| Practice | Implementation |
|----------|---------------|
| CI pipeline | GitHub Actions / GitLab CI: lint → test → build on every push |
| CD pipeline | Automated deploy to staging on merge, production on approval |
| IaC | Terraform for cloud resources, Docker for app containers |
| DORA metrics | Track in deployment tool or dedicated dashboard |
| Small batches | PRs under 400 lines, deploy multiple times per day |
| Shift left | SAST, linting, type checking in CI; pre-commit hooks locally |

---

## Checklist for DevOps Readiness

- [ ] CI pipeline runs on every commit (lint, test, build)
- [ ] CD pipeline automates deployment to staging and production
- [ ] Infrastructure is defined as code and version-controlled
- [ ] Deployments are automated and repeatable
- [ ] DORA metrics are tracked (even manually to start)
- [ ] Tests run fast enough to not block development flow
- [ ] Team owns the full lifecycle (no separate ops team for deploy)
- [ ] Rollback is automated or trivially easy
- [ ] Feature flags enable decoupling deploy from release
