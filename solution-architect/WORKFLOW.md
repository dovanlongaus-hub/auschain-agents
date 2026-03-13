# WORKFLOW — Solution Architect (Zara) 🏗️

## Architecture Review Process

### Phase 1: Discovery (30 phút)
```
Input từ PM/BA:
  - Project brief + goals
  - Expected user volume + growth
  - Budget constraint
  - Timeline
  - Existing tech stack (nếu có)

Output:
  - discovery-questions.md (nếu cần làm rõ thêm)
  - constraints-summary.md
```

### Phase 2: Design (1-2 tiếng)
```
Tạo 2-3 architecture options:
  Option A: Conservative — minimal cost, proven tech
  Option B: Balanced — best fit for scale + budget
  Option C: Advanced — future-proof, higher complexity

Mỗi option có:
  - Architecture diagram (Mermaid)
  - Tech stack list
  - Cost estimate $/month
  - Pros/Cons
  - Implementation complexity (1-5)
```

### Phase 3: Decision & Documentation
```
Output:
  - architecture-decision.md: recommended option + rationale
  - adr/ADR-001-[topic].md: formal Architecture Decision Record
  - system-diagram.md: Mermaid diagrams
  - cost-model.md: detailed cost breakdown
  - implementation-roadmap.md: phased approach
```

---

## ADR Format (Architecture Decision Record)
```markdown
# ADR-XXX: [Title]

## Status
[Proposed | Accepted | Deprecated | Superseded]

## Context
[What is the issue / why do we need to decide]

## Decision
[What we decided]

## Rationale
[Why we chose this over alternatives]

## Consequences
**Positive:** ...
**Negative:** ...
**Risks:** ...

## Alternatives Considered
1. [Alt A] — rejected because ...
2. [Alt B] — rejected because ...

## Cost Impact
Estimated: $X/month at Y users
```

---

## Architecture Patterns by Project Type

### Type A: Static App + AI Chat (e.g., visa-path-aus)
```
Browser → Nginx (static) → /var/www/
                 ↓
           AI API (DeepSeek/Claude)
           LocalStorage (offline)

Cost: $0 (self-hosted VPS already paid)
Upgrade path: + Supabase when need persistence
```

### Type B: Full-stack App (e.g., cherry-longcare-au)
```
Browser → Nginx → Node.js API (PM2)
                      ↓
              PostgreSQL / SQLite
              + Redis (cache, optional)

Cost: VPS only ($0 extra)
```

### Type C: Multi-tenant SaaS
```
Browser → CDN (Cloudflare free)
              ↓
         Load Balancer (Nginx)
              ↓
    [App Server 1] [App Server 2]
              ↓
    PostgreSQL (managed) + Redis
    + Object Storage (S3/R2)
    + Monitoring (Grafana)

Cost: $30-100/month
```

### Type D: AI-heavy App (e.g., An Lạc)
```
Browser → API Gateway (Nginx)
              ↓
    [Chat API] [Content API] [Analytics API]
              ↓
    PostgreSQL + pgvector (RAG)
    + Redis (session + queue)
    + AI API (DeepSeek/Claude)

Cost: VPS + AI API usage
```

---

## Cost Reference (2025/2026)

| Service | Free Tier | Paid from |
|---------|-----------|-----------|
| Supabase | 500MB DB, 50k rows/month | $25/mo |
| Vercel | 100GB bandwidth | $20/mo |
| Cloudflare R2 | 10GB storage, 1M req | $0.015/GB |
| Railway | $5 credit/month | $5/mo |
| Fly.io | 3 shared VMs | $2/mo |
| Render | 1 free service (sleeps) | $7/mo |
| Upstash Redis | 10k req/day | $0.2/100k |
| DeepSeek API | — | $0.14/M tokens |
| Claude Haiku | — | $0.25/M tokens |
| Self-hosted VPS (current) | Already paid | ~$30/mo est |

---

## Tech Stack Recommendations (2026)

### Frontend
- **React + Vite:** ✅ Fast build, excellent DX
- **Next.js:** When need SSR/SEO
- **TailwindCSS:** ✅ Utility-first, fast
- **shadcn/ui:** ✅ Copy-paste components, no vendor lock

### Backend
- **Node.js + Express:** Simple APIs, fast iteration
- **FastAPI (Python):** AI/ML endpoints
- **Hono:** Edge/serverless, ultra-lightweight

### Database
- **PostgreSQL:** ✅ Default choice for almost everything
- **SQLite:** Single-server, <10k users, zero-ops
- **Redis:** Cache, queues, real-time pub/sub
- **pgvector:** RAG/AI search (avoid separate vector DB for small scale)

### Infra (self-hosted like current setup)
- **Docker Compose:** ✅ Simple, reproducible
- **Nginx:** ✅ Reverse proxy + static serve
- **PM2:** Node.js process manager
- **Certbot:** SSL, free

### AI
- **DeepSeek:** ✅ Cost-effective, good quality
- **Claude Haiku:** Fast, cheap for classification/extraction
- **Claude Sonnet:** Complex reasoning, architecture decisions
