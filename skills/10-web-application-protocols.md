# Web Application Protocols & Principles

**Source:** Web Application Architecture: Principles, Protocols and Practices, 2nd Edition
**Category:** Supplementary (C) — ถ้าอยากเข้าใจ "เว็บ" ระดับโปรโตคอล/หลักการ
**Intention:** core concepts และหลักการทั่วไปของ web application development

---

## Key Skills

### 1. HTTP Protocol Fundamentals
- Understand the request/response cycle
- HTTP methods and their semantics:
  - `GET` — retrieve (safe, idempotent, cacheable)
  - `POST` — create (not idempotent)
  - `PUT` — replace (idempotent)
  - `PATCH` — partial update (not necessarily idempotent)
  - `DELETE` — remove (idempotent)
- Status codes and their meanings:
  - `2xx` success, `3xx` redirect, `4xx` client error, `5xx` server error
- Headers: Content-Type, Authorization, Cache-Control, CORS headers

### 2. Client-Server Architecture
- Separation of concerns: client handles presentation, server handles logic and data
- Stateless communication — each request contains all needed context
- Benefits: independent evolution, scalability, portability

### 3. Caching
- **Browser cache** — Cache-Control, ETag, Last-Modified headers
- **CDN cache** — edge caching for static assets and cacheable responses
- **Application cache** — Redis/Memcached for computed results
- **Database query cache** — frequently accessed query results
- Cache invalidation strategies: TTL, event-based, versioned URLs

### 4. Session Management
- HTTP is stateless — sessions add statefulness
- Server-side sessions (session ID in cookie, data on server)
- Client-side tokens (JWT — data in the token itself)
- Trade-offs: server memory vs. token size, revocation complexity

### 5. Content Delivery & Rendering
- **Server-Side Rendering (SSR)** — HTML generated on server, fast first paint, SEO-friendly
- **Client-Side Rendering (CSR)** — JavaScript renders in browser, rich interactivity
- **Static Site Generation (SSG)** — HTML pre-built at build time, fastest delivery
- **Hybrid approaches** — SSR for first load, CSR for subsequent navigation

### 6. Web Standards & APIs
- REST architectural style and constraints
- WebSocket for bidirectional real-time communication
- Server-Sent Events (SSE) for server-push updates
- CORS — Cross-Origin Resource Sharing policies
- DNS resolution, TCP/TLS handshake, connection reuse

### 7. Performance Fundamentals
- Minimize round trips (HTTP/2 multiplexing, connection reuse)
- Compress responses (gzip, Brotli)
- Optimize asset delivery (minification, bundling, lazy loading)
- Critical rendering path optimization
- Core Web Vitals: LCP, FID/INP, CLS

---

## Practical Application for Web Apps

| Concept | Implementation |
|---------|---------------|
| HTTP methods | RESTful API design following method semantics |
| Caching | Cache-Control headers, CDN for static assets, Redis for API responses |
| Sessions | JWT for stateless auth or server sessions in Redis |
| Rendering | SSR for SEO pages, CSR for app-like dashboards, SSG for marketing |
| Performance | HTTP/2, Brotli compression, lazy loading, image optimization |
| Real-time | WebSocket for chat/collaboration, SSE for live feeds |

---

## Checklist

- [ ] HTTP methods used correctly (GET for reads, POST for creates, etc.)
- [ ] Appropriate status codes returned for all responses
- [ ] Caching strategy defined (browser, CDN, application layers)
- [ ] CORS configured correctly for cross-origin needs
- [ ] Content rendering strategy chosen (SSR/CSR/SSG) based on requirements
- [ ] HTTPS enforced for all communication
- [ ] Compression enabled for responses
- [ ] Static assets served via CDN with cache headers
