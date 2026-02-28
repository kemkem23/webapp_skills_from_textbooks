# OWASP Security Baseline

**Source:** OWASP Top Ten (2025) + OWASP ASVS + OWASP WSTG (v4.2)
**Category:** Security Baseline — อัปเดตเร็วกว่าหนังสือ ใช้คู่กับเล่ม Web Security
**Intention:** awareness list, security checklist, และแนวทาง security testing สำหรับ web apps

---

## Key Skills

### 1. OWASP Top Ten Awareness (2025)
Know the most critical web application security risks:

| # | Risk | Key Defense |
|---|------|-------------|
| A01 | Broken Access Control | Server-side authorization on every request |
| A02 | Cryptographic Failures | HTTPS everywhere, strong encryption, no hardcoded secrets |
| A03 | Injection | Parameterized queries, input validation, output encoding |
| A04 | Insecure Design | Threat modeling, secure design patterns, abuse cases |
| A05 | Security Misconfiguration | Hardened defaults, remove unused features, security headers |
| A06 | Vulnerable Components | Dependency scanning, timely updates, SCA tools |
| A07 | Authentication Failures | MFA, strong passwords, rate limiting, session management |
| A08 | Software & Data Integrity | Verify dependencies, secure CI/CD, code signing |
| A09 | Security Logging & Monitoring | Log security events, alert on attacks, incident response |
| A10 | Server-Side Request Forgery | Validate/sanitize URLs, network segmentation, allowlists |

### 2. ASVS (Application Security Verification Standard)
Use ASVS as a requirements checklist for secure development:

- **Level 1** — Opportunistic: basic security for all applications
  - Input validation, output encoding, basic auth
- **Level 2** — Standard: most applications handling sensitive data
  - Session management, access control, cryptography
- **Level 3** — Advanced: high-value applications (finance, healthcare, critical infrastructure)
  - Defense in depth, advanced threat protection

Key ASVS categories:
- V1: Architecture & Design
- V2: Authentication
- V3: Session Management
- V4: Access Control
- V5: Input Validation
- V6: Cryptography
- V7: Error Handling & Logging
- V8: Data Protection
- V9: Communication Security
- V10: Malicious Code
- V11: Business Logic
- V12: Files & Resources
- V13: API Security
- V14: Configuration

### 3. WSTG (Web Security Testing Guide)
Structured approach to testing web application security:

- **Information Gathering** — fingerprint web server, discover application entry points
- **Configuration Testing** — test default configs, file permissions, HTTP methods
- **Identity Management** — test user registration, account provisioning, enumeration
- **Authentication Testing** — test login, password policies, MFA, session fixation
- **Authorization Testing** — test access controls, privilege escalation, IDOR
- **Session Management** — test cookie attributes, session timeout, CSRF
- **Input Validation** — test XSS, injection, file upload, HTTP parameter pollution
- **Error Handling** — test error codes, stack traces, information leakage
- **Cryptography** — test TLS config, sensitive data in transit and at rest
- **Business Logic** — test workflow bypass, data integrity, rate limiting
- **Client-Side** — test DOM XSS, JavaScript execution, WebSocket security

### 4. Security in Development Lifecycle
- **Design phase** — threat modeling (STRIDE), secure design review
- **Development phase** — secure coding guidelines, code review, SAST
- **Testing phase** — DAST, penetration testing, WSTG-guided testing
- **Deployment phase** — security configuration, hardening, vulnerability scanning
- **Operations phase** — monitoring, incident response, patching

---

## Practical Application for Web Apps

| Resource | How to Use |
|----------|-----------|
| OWASP Top Ten | Awareness training — ensure team knows all 10 risks |
| ASVS Level 1 | Minimum requirements for any web application |
| ASVS Level 2 | Requirements for apps handling user data / PII |
| WSTG | Guide security testing before each release |
| Dependency scanning | Automate with Dependabot, Snyk, or npm audit in CI |
| SAST/DAST | Integrate static and dynamic analysis in CI pipeline |

---

## Checklist for Security Baseline

- [ ] Team is aware of OWASP Top Ten risks
- [ ] ASVS Level 1 requirements are met at minimum
- [ ] Dependency scanning runs in CI (Dependabot, Snyk, npm audit)
- [ ] Security headers configured (CSP, HSTS, X-Frame-Options, etc.)
- [ ] Authentication uses MFA and strong password policies
- [ ] Access control is server-side and tested for bypass
- [ ] Input validation and output encoding prevent injection and XSS
- [ ] Security logging captures authentication events and access failures
- [ ] TLS is enforced with modern configuration
- [ ] Security testing (WSTG-guided) is performed before releases
- [ ] Incident response plan exists and is practiced
