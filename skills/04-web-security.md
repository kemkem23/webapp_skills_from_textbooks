# Web Security for Developers

**Source:** Web Security for Developers (Malcolm McDonald)
**Category:** Core Reading
**Intention:** ความปลอดภัยเว็บแบบ practical — ครอบคลุม SQL injection, XSS, CSRF, auth/session/encryption

---

## Key Skills

### 1. Injection Prevention
- **SQL Injection** — always use parameterized queries / prepared statements; never concatenate user input into SQL
- **Command Injection** — avoid shell commands with user input; use safe APIs instead
- **LDAP / NoSQL Injection** — validate and sanitize input for all query languages

### 2. Cross-Site Scripting (XSS) Defense
- **Reflected XSS** — sanitize input echoed back in responses
- **Stored XSS** — sanitize all user-generated content before storage and rendering
- **DOM-based XSS** — avoid `innerHTML`, use safe DOM APIs
- **Content Security Policy (CSP)** — deploy CSP headers to restrict script sources
- Always encode output based on context (HTML, JavaScript, URL, CSS)

### 3. Cross-Site Request Forgery (CSRF) Protection
- Use anti-CSRF tokens in all state-changing forms
- Validate `Origin` and `Referer` headers
- Use `SameSite` cookie attribute
- Require re-authentication for sensitive actions

### 4. Authentication & Session Management
- Hash passwords with bcrypt/scrypt/Argon2 (never MD5/SHA1)
- Implement multi-factor authentication (MFA)
- Use secure session management:
  - Set `HttpOnly`, `Secure`, `SameSite` flags on cookies
  - Regenerate session ID after login
  - Implement session timeout and idle timeout
- Protect against brute force (rate limiting, account lockout)

### 5. Encryption & Transport Security
- Enforce HTTPS everywhere (HSTS headers)
- Use TLS 1.2+ with strong cipher suites
- Encrypt sensitive data at rest
- Never store secrets in code or version control

### 6. Authorization & Access Control
- Implement principle of least privilege
- Validate authorization on every request (server-side)
- Protect against Insecure Direct Object References (IDOR)
- Use role-based or attribute-based access control

### 7. Security Headers
- `Content-Security-Policy` — restrict resource loading
- `X-Content-Type-Options: nosniff` — prevent MIME sniffing
- `X-Frame-Options: DENY` — prevent clickjacking
- `Strict-Transport-Security` — enforce HTTPS
- `Referrer-Policy` — control referrer information leakage

---

## Practical Application for Web Apps

| Threat | Defense |
|--------|---------|
| SQL Injection | Parameterized queries, ORM with safe defaults |
| XSS | Output encoding, CSP headers, no `innerHTML` |
| CSRF | Anti-CSRF tokens, SameSite cookies |
| Broken Auth | bcrypt + MFA + secure session cookies |
| Sensitive Data Exposure | HTTPS everywhere, encrypt at rest, no secrets in code |
| IDOR | Server-side authorization checks on every resource access |

---

## Checklist Before Deploying

- [ ] All database queries use parameterized statements
- [ ] User input is validated and output is encoded
- [ ] CSP and security headers are configured
- [ ] CSRF protection is active on all state-changing endpoints
- [ ] Passwords are hashed with bcrypt/Argon2
- [ ] Sessions use HttpOnly, Secure, SameSite cookies
- [ ] HTTPS is enforced with HSTS
- [ ] Authorization is checked server-side on every request
- [ ] No secrets or credentials in source code
- [ ] Rate limiting is in place for authentication endpoints
