# Site Reliability Engineering (SRE)

**Source:** Google SRE Book + SRE Workbook
**Category:** Core Reading
**Intention:** คิดเรื่อง reliability ตอน run production — SLO, monitoring, alerting, incident response, postmortem, canary

---

## Key Skills

### 1. Service Level Objectives (SLOs)
- Define **SLI** (Service Level Indicator) — measurable metric (latency, error rate, throughput)
- Set **SLO** (Service Level Objective) — target value for SLI (e.g., 99.9% availability)
- Understand **SLA** (Service Level Agreement) — contractual commitment with consequences
- Calculate **error budget** — allowed downtime/errors before breaching SLO
- Use error budget to balance reliability work vs. feature development

### 2. Monitoring & Observability
- Implement the **four golden signals**:
  - **Latency** — response time for successful and failed requests
  - **Traffic** — requests per second, concurrent users
  - **Errors** — error rate (5xx, failed requests)
  - **Saturation** — resource utilization (CPU, memory, disk, connections)
- Use metrics, logs, and traces (the three pillars of observability)
- Build dashboards showing system health at a glance

### 3. Alerting
- Alert on **symptoms**, not causes (e.g., high error rate, not high CPU)
- Every alert must be **actionable** — if no one needs to act, don't alert
- Reduce alert fatigue — tune thresholds, suppress flapping
- Define escalation policies and on-call rotations
- Use multi-window, multi-burn-rate alerting for SLO-based alerts

### 4. Incident Response
- Define incident severity levels (SEV1-SEV4)
- Establish clear incident roles (Incident Commander, Communications Lead, Operations Lead)
- Use a structured incident response process:
  1. Detect and triage
  2. Mitigate (restore service first)
  3. Investigate root cause
  4. Resolve and verify
- Communicate status clearly during incidents (status page, Slack updates)

### 5. Postmortems
- Write **blameless postmortems** for every significant incident
- Include: timeline, root cause, impact, mitigation, action items
- Focus on systemic improvements, not individual blame
- Track action items to completion
- Share learnings across the organization

### 6. Canary & Safe Deployments
- Deploy changes to a small subset of traffic first (canary)
- Monitor canary metrics against baseline
- Automate rollback if canary metrics degrade
- Progressive rollout: canary → percentage rollout → full deployment

### 7. Capacity Planning
- Model capacity based on traffic projections
- Load test to find system limits before production tells you
- Plan for peak traffic (not just average)
- Maintain headroom for unexpected spikes

---

## Practical Application for Web Apps

| Practice | Implementation |
|----------|---------------|
| SLOs | Define availability and latency targets for each service |
| Golden signals | Instrument with Prometheus/Grafana or cloud-native monitoring |
| Alerting | PagerDuty/Opsgenie with SLO-based burn rate alerts |
| Incident response | Documented runbooks, on-call schedule, status page |
| Postmortems | Template in shared docs, reviewed in team meeting |
| Canary deploys | Feature flags or traffic splitting in deployment pipeline |

---

## Checklist for Production Readiness

- [ ] SLIs and SLOs defined for the service
- [ ] Monitoring covers the four golden signals
- [ ] Alerts are symptom-based and actionable
- [ ] On-call rotation is established
- [ ] Incident response process is documented
- [ ] Postmortem template and process exist
- [ ] Deployment includes canary or progressive rollout
- [ ] Capacity planning accounts for peak traffic
- [ ] Runbooks exist for common operational scenarios
