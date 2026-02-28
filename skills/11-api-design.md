# API Design

**Source:** Designing Web APIs (Brenda Jin, Saurabh Sahni, Amir Shevat)
**Category:** Supplementary (D) — ถ้า API เป็นหัวใจของระบบ
**Intention:** design API ให้ใช้งานง่ายและดูแลต่อได้

---

## Key Skills

### 1. API Paradigm Selection
- **REST** — resource-based, HTTP methods, widely understood, best for CRUD-heavy APIs
- **GraphQL** — client specifies exact data needed, good for complex frontends
- **gRPC** — binary protocol, high performance, good for service-to-service
- **WebSocket** — bidirectional, real-time communication
- Choose based on use case, not trend

### 2. RESTful API Design
- Use **nouns** for resources, not verbs (`/users`, not `/getUsers`)
- Use HTTP methods for actions (GET, POST, PUT, PATCH, DELETE)
- Use plural resource names (`/users/{id}`, `/orders/{id}/items`)
- Nest resources to show relationships (`/users/{id}/orders`)
- Use query parameters for filtering, sorting, pagination (`?status=active&sort=created_at&page=2`)

### 3. Request & Response Design
- Use consistent response format across all endpoints
- Include pagination metadata (total count, next/prev links)
- Return appropriate HTTP status codes
- Use JSON as default format with `Content-Type: application/json`
- Envelope responses consistently: `{ "data": [...], "meta": { "total": 100 } }`

### 4. Error Handling
- Return structured error responses:
  ```json
  {
    "error": {
      "code": "VALIDATION_ERROR",
      "message": "Email is required",
      "details": [{ "field": "email", "reason": "required" }]
    }
  }
  ```
- Use appropriate HTTP status codes (400, 401, 403, 404, 422, 500)
- Provide actionable error messages
- Never expose internal details (stack traces, SQL errors) in production

### 5. Versioning
- Version your API from day one
- **URL versioning** — `/api/v1/users` (most common, easiest)
- **Header versioning** — `Accept: application/vnd.api+json;version=1`
- Support previous versions during migration period
- Deprecation strategy: announce → sunset period → removal

### 6. Authentication & Authorization
- Use standard auth mechanisms:
  - **API keys** — simple, for server-to-server
  - **OAuth 2.0** — delegated authorization for third-party apps
  - **JWT** — stateless tokens for authenticated sessions
- Rate limit by API key / user to prevent abuse
- Scope-based permissions for fine-grained access control

### 7. Documentation
- Document every endpoint with: method, URL, parameters, request/response examples
- Use OpenAPI (Swagger) specification
- Provide interactive documentation (Swagger UI, Redoc)
- Include authentication guide and getting started tutorial
- Keep docs in sync with code (generate from spec or annotations)

### 8. Pagination, Filtering & Sorting
- **Offset pagination** — `?page=2&per_page=20` (simple, inconsistent with mutations)
- **Cursor pagination** — `?cursor=abc123&limit=20` (consistent, better for real-time data)
- Filter: `?status=active&created_after=2025-01-01`
- Sort: `?sort=created_at&order=desc`

---

## Practical Application for Web Apps

| Decision | Guidance |
|----------|----------|
| Public API | REST with OpenAPI docs, versioned URLs, OAuth 2.0 |
| Internal services | gRPC for performance or REST for simplicity |
| Complex frontend | GraphQL to reduce over/under-fetching |
| Real-time features | WebSocket or SSE alongside REST |
| Pagination | Cursor-based for feeds/timelines, offset for admin tables |

---

## Checklist for API Design

- [ ] API paradigm chosen based on use case
- [ ] Resource naming follows conventions (plural nouns, nested for relationships)
- [ ] Consistent response format across all endpoints
- [ ] Error responses are structured and actionable
- [ ] API is versioned from the start
- [ ] Authentication and rate limiting are in place
- [ ] Pagination is implemented for list endpoints
- [ ] API documentation is generated from spec (OpenAPI)
- [ ] Breaking changes go through deprecation process
