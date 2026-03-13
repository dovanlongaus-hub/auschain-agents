# SELF_LEARNING.md — Auschain Team Self-Learning Protocol
**Version:** 1.0 | Áp dụng cho tất cả 10 agents

---

## Triết lý

> "Một agent giỏi không chỉ làm đúng việc — mà còn **tự học để làm tốt hơn sau mỗi lần**."

Mỗi agent trong Auschain Team có khả năng:
1. **Nhận ra** khi nào mình thiếu kiến thức hoặc làm chưa tốt
2. **Tự nghiên cứu** các chuẩn mực mới nhất trong lĩnh vực của mình
3. **Tự tạo skill set** dưới dạng files có thể tái sử dụng
4. **Chia sẻ** với team khi học được gì có giá trị chung

---

## Cơ chế Tự Học

### 1. Post-Task Review (sau mỗi task)
Sau khi hoàn thành task, mỗi agent tự hỏi:
```
- Tôi có gặp tình huống không biết cách xử lý không?
- Tôi đã tra cứu gì để hoàn thành task?
- Cách làm của tôi có thể cải thiện không?
- Có pattern nào tái sử dụng được không?
```
→ Ghi vào `skills/skill-log.md`

### 2. Skill Gap Detection (tự phát hiện thiếu sót)
Khi agent gặp task mà:
- Không chắc cách làm tốt nhất
- Phải search/tra cứu nhiều hơn bình thường
- Kết quả bị reject hoặc cần revise nhiều

→ **Trigger tạo skill mới** cho topic đó

### 3. Skill Creation Protocol
```
skills/
  [domain]-[topic]-v1.md    ← skill file
  skill-log.md              ← log tất cả skills đã học
  skill-index.md            ← index để tìm kiếm nhanh
```

### 4. Skill Format chuẩn
```markdown
# Skill: [Tên skill]
Version: 1.0 | Date: YYYY-MM-DD | Agent: [Tên]

## Khi nào dùng skill này
[Mô tả trigger conditions]

## Chuẩn mực / Best Practice
[Kiến thức cốt lõi, cập nhật theo industry standard mới nhất]

## Step-by-step
1. ...
2. ...

## Ví dụ thực tế
[Code snippet, template, example output]

## Common mistakes to avoid
[Những lỗi hay gặp và cách tránh]

## Tham khảo
[Links, specs, docs]

## Changelog
- v1.0: Initial
```

---

## Coding Standards — Chuẩn Lập Trình Chuyên Nghiệp 2025/2026

### Tất cả agents khi viết/review code phải tuân thủ:

#### A. Code Quality Standards
```
✅ Clean Code:
- Function names rõ nghĩa (verbs for functions, nouns for vars)
- Function ≤ 20 lines, single responsibility
- No magic numbers — dùng named constants
- DRY (Don't Repeat Yourself) — extract khi dùng ≥ 3 lần

✅ Error Handling:
- Không bao giờ catch và bỏ qua error
- Log đầy đủ context (không log sensitive data)
- User-facing errors phải friendly, không expose internals

✅ Security by default:
- Input validation mọi endpoint
- Sanitize output (XSS prevention)
- Không hardcode credentials — dùng env vars
- Rate limiting trên tất cả public APIs
```

#### B. Git Standards
```
✅ Commit format (Conventional Commits):
  feat: add Stripe checkout to Pricing page
  fix: resolve localStorage race condition in supabaseClient
  refactor: extract payment logic into usePayment hook
  docs: update README with deployment steps
  test: add unit tests for EOI calculator

✅ Branch naming:
  feature/stripe-checkout
  fix/pricing-page-aud
  refactor/auth-system

✅ PR rules:
- Không merge khi chưa có review
- Tests phải pass
- No secrets in diff
```

#### C. Testing Standards
```
✅ Unit tests: mọi utility function, business logic
✅ Integration tests: API endpoints, database operations
✅ E2E: critical user flows (signup → payment → feature access)
✅ Coverage target: ≥ 80%
✅ Test naming: describe('what'), it('should behavior when condition')
```

#### D. Documentation Standards
```
✅ README.md: setup, run, deploy, env vars
✅ JSDoc/docstring cho mọi public function
✅ Inline comments: WHY không phải WHAT
✅ ADR cho architectural decisions (Zara)
✅ CHANGELOG.md: track changes theo semantic versioning
```

#### E. Performance Standards
```
✅ API response: < 200ms p95 (non-AI)
✅ AI response: streaming required cho > 500ms
✅ Frontend: Lighthouse score ≥ 90 (Performance, Accessibility)
✅ Bundle size: < 500KB gzipped (warning), < 1MB (hard limit)
✅ Database: explain analyze mọi query trên production data
```

---

## Skill Sets Theo Agent

### 📊 Iris (BA Agent) — Core Skills
- requirements-elicitation.md: Kỹ thuật khai thác yêu cầu từ brief mơ hồ
- user-story-writing.md: Chuẩn INVEST, BDD Given/When/Then
- acceptance-criteria.md: Viết AC đo được, testable
- market-research.md: Research user needs cho Vietnamese Australian market

### 📋 Kenji (PM Agent) — Core Skills
- sprint-planning.md: Ước tính effort, velocity tracking
- blocker-resolution.md: Xử lý blockers nhanh
- stakeholder-communication.md: Report cho Sếp Long
- risk-management.md: Identify & mitigate project risks

### ⚙️ Axel (Backend Agent) — Core Skills
- nodejs-api-patterns.md: Express/Hono patterns, middleware
- auth-implementation.md: JWT, session, OAuth2 với Supabase
- database-access-patterns.md: Queries, transactions, migrations
- async-patterns.md: Promise, async/await, queue patterns

### 🔒 Cipher (Security Agent) — Core Skills
- owasp-top10-2025.md: Latest OWASP vulnerabilities + mitigations
- threat-modeling.md: STRIDE methodology
- auth-security.md: Password hashing, token security, CSRF
- api-security.md: Rate limiting, input validation, CORS

### 🗄️ Fauna (Database Agent) — Core Skills
- postgresql-optimization.md: Indexes, query optimization, EXPLAIN ANALYZE
- schema-design-patterns.md: Normalization, polymorphic associations, JSONB
- migration-patterns.md: Safe zero-downtime migrations
- supabase-rls.md: Row Level Security patterns

### 🎨 Nova (Frontend Agent) — Core Skills
- react-patterns-2025.md: Server components, hooks best practices
- tailwind-design-system.md: Consistent UI patterns
- accessibility.md: WCAG 2.1 AA standards
- performance-optimization.md: Code splitting, lazy loading, memoization

### 🧪 Tessa (QA Agent) — Core Skills
- test-strategy.md: Unit/Integration/E2E pyramid
- vitest-patterns.md: React Testing Library, mocking
- playwright-e2e.md: E2E test patterns cho React apps
- bug-reporting.md: Chuẩn bug report với reproduction steps

### 📣 Luna (Marketing Agent) — Core Skills
- seo-technical-audit.md: Core Web Vitals, schema markup, sitemap
- content-brief-template.md: Brief chuẩn trước khi viết
- ga4-setup-guide.md: Event tracking, funnels, conversions
- social-media-formats.md: Specs theo platform (2025/2026)

### 🏗️ Zara (Solution Architect) — Core Skills
- adr-template.md: Architecture Decision Record format
- cost-modeling.md: Infrastructure cost calculation
- architecture-patterns-2025.md: Current best practices
- migration-planning.md: Safe system migration strategies

### 💰 Rex (CFO Agent) — Core Skills
- revenue-model-templates.md: SaaS, marketplace, B2B pricing
- unit-economics.md: CAC, LTV, payback, churn calculation
- pricing-psychology.md: Anchoring, decoy, value-based pricing
- stripe-integration-guide.md: Checkout, subscriptions, webhooks

---

## Self-Upgrade Trigger Events

Agent tự động update skills khi:

| Trigger | Action |
|---------|--------|
| Task completed với điều gì mới học | Append to skill-log.md |
| Phát hiện better approach | Create/update skill file |
| Industry standard thay đổi | Update relevant skill file + note version |
| Bug caused by knowledge gap | Create "lessons-learned" entry |
| PM reject output | Document why + update process |
| Peer review feedback | Incorporate into skill file |

---

## Cross-Team Knowledge Sharing

Khi 1 agent tạo skill có giá trị cho team khác:
1. Copy skill file vào `agents-team/shared-skills/`
2. Notify PM (Kenji) với summary
3. Kenji announce trong WORKFLOW.md update

### Shared Skills Library
`agents-team/shared-skills/` — kho kiến thức chung của Auschain Team

---

## Quality Gate — Skill Review

Trước khi skill được dùng trong production:
- [ ] Tested on at least 1 real task
- [ ] Reviewed by 1 peer agent (hoặc Mochi)
- [ ] Version tagged (v1.0, v1.1, ...)
- [ ] Added to skill-index.md
