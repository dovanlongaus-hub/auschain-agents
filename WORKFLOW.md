# Auschain — Agent Workflow v5

## Kiến trúc tổng thể

```
Sếp Long
    │
    ▼
🍡 Mochi (main) — Haiku
    │
    ├────────────┬──────────────┬──────────────┐
    │ Feature    │ Marketing    │ Revenue/Fin  │ AI/Data
    ▼            ▼              ▼              ▼
📊 Iris(BA)  📣 Luna       💰 Rex(CFO)  📊 Sage(Data)
   Sonnet       Sonnet          Sonnet         Sonnet
    │            │               │              │
    ▼            └──────┬────────┘              │
🏗️ Zara(SA)           🌐 Hana(L10n)      🤖 Neo(AI/ML)
   ARCH GATE           Review copy           Prompt opt
    │
    ▼
📋 Kenji(PM)
    │
    ├──────────────────────────────────┐
    ▼                                  ▼
🗄️ Fauna(DB)  🔒 Cipher(Sec)     🚀 Kane(DevOps)
    │               │                  CI/CD, infra
    └────────┬───────┘
             ▼
      ⚙️ Axel(Backend)
             ▼
      🎨 Nova(Frontend)
             ▼
      🧪 Tessa(QA) ──────── 🎧 Aria(CX)
             │               Onboarding
      ✅ PASS / ❌ FAIL
             ▼
      Kenji → Mochi → Sếp Long
```

## Model Assignment (cost-optimised)

| Agent | Tên | Model | Lý do |
|---|---|---|---|
| `ba-agent` | 📊 Iris | **Sonnet** | Reasoning sâu, phân tích yêu cầu phức tạp |
| `pm-agent` | 📋 Kenji | **Sonnet** | Điều phối, quyết định ưu tiên |
| `solution-architect` | 🏗️ Zara | **Sonnet** | Architecture decisions cần deep reasoning |
| `marketing-agent` | 📣 Luna | **Sonnet** | Creative + analytical balance |
| `cfo-agent` | 💰 Rex | **Sonnet** | Revenue modeling, financial reasoning |
| `devops-agent` | 🚀 Kane | **Sonnet** | Infrastructure decisions, incident response |
| `data-agent` | 📊 Sage | **Sonnet** | Analytics, statistical reasoning |
| `ai-agent` | 🤖 Neo | **Sonnet** | Prompt engineering, model evaluation |
| `localisation-agent` | 🌐 Hana | **Sonnet** | Cultural + linguistic nuance |
| `customer-success-agent` | 🎧 Aria | **Haiku** | Fast support responses |
| `backend-agent` | ⚙️ Axel | **Haiku** | Code gen nhanh, pattern lặp lại |
| `security-agent` | 🔒 Cipher | **Sonnet** | Critical — không tiết kiệm ở đây |
| `database-agent` | 🗄️ Fauna | **Haiku** | SQL/schema gen, Haiku đủ mạnh |
| `frontend-agent` | 🎨 Nova | **Haiku** | Component code, Haiku nhanh |
| `qa-agent` | 🧪 Tessa | **Haiku** | Test template gen, nhanh |

**Escalate lên Opus khi:**
- Architecture decision ảnh hưởng toàn hệ thống
- Security vulnerability nghiêm trọng (P0)
- Performance bottleneck phức tạp
- BA gặp yêu cầu rất mơ hồ cần phân tích sâu

## Khi nào gọi Solution Architect (Zara)

- **Dự án mới:** Zara thiết kế architecture TRƯỚC khi team bắt đầu code
- **Major refactor:** Thay đổi database, đổi framework, thêm service
- **Scale issue:** App chậm, cần tối ưu infra
- **Cost review:** Đánh giá lại chi phí infra, đề xuất tiết kiệm
- **Tech debt:** Lên kế hoạch giải quyết nợ kỹ thuật

## Khi nào gọi CFO Agent (Rex)

- **Dự án mới:** Rex audit revenue opportunity TRƯỚC khi build
- **Feature mới:** "Cái này có thể monetize không? ROI bao nhiêu?"
- **Pricing:** Thiết kế pricing model, A/B test giá
- **Monthly:** Review P&L, cập nhật revenue roadmap
- **Khi đang tốn tiền mà chưa thu được:** Rex diagnose và fix

## ⚡ Quy tắc CTA Bắt buộc (Revenue First)

> **Lệnh từ Sếp Long (2026-03-13):** Mọi lần Nova (Frontend) cập nhật giao diện, BẮT BUỘC phải:
> 1. Tham vấn **Luna (Marketing)** về copy & vị trí CTA
> 2. Tham vấn **Rex (CFO)** về pricing trigger & conversion logic
> 3. Deploy ít nhất 1 nút/banner khuyến khích user đăng ký dịch vụ trả phí

### CTA Standards (tất cả projects)
- **Chat limit reached** → Hiển thị modal nâng cấp với nút "Đăng ký ngay" → email payment@{domain}
- **Premium feature** → Lock icon + "Mở khóa với Premium" button
- **After session 3+** → Inline banner: "Bạn đang dùng phiên bản miễn phí — Nâng cấp để tiếp tục"
- **Footer** → Luôn có pricing link + payment email visible
- **AI message block** → CTA cuối mỗi lần AI bị giới hạn

### Workflow khi Nova build/update UI:
```
1. Nova builds component
2. Nova gọi Luna: "Review CTA placement cho [component]"
3. Nova gọi Rex: "Confirm pricing trigger và conversion logic"
4. Nova deploy với CTA đã được 3 bên approve
```

### Email routing đã xác nhận (2026-03-13)
- anlac.online → payment@anlac.online (thanh toán), admin@blockID.au (liên hệ khác)
- visa-path-aus.com → payment@visa-path-aus.com (thanh toán), admin@blockID.au (liên hệ khác)
- cherry/suong/các app khác → admin@blockID.au

## Khi nào gọi Marketing Agent (Luna)

- **Launch mới:** Cần landing page copy, App Store description
- **SEO:** Technical audit, content strategy, keyword research
- **Social campaign:** Content calendar, post templates, hashtag strategy
- **Analytics setup:** GA4, tracking plan, UTM framework, KPI dashboard
- **Growth:** Funnel optimization, CTA testing, user acquisition
- **🆕 CTA Review:** Bắt buộc review mỗi khi Frontend update UI (xem Quy tắc CTA ở trên)

## Cách Mochi dùng team

### Option A — Qua BA (recommended cho mọi feature mới):
```
sessions_spawn(task: "Iris phân tích yêu cầu: [raw input từ Sếp]", agentId: "ba-agent")
```

### Option B — Qua Solution Architect (cho tech decisions):
```
sessions_spawn(task: "Zara: thiết kế kiến trúc cho [dự án/feature]", agentId: "solution-architect")
```

### Option C — CFO Agent (cho revenue/pricing/financial decisions):
```
sessions_spawn(task: "Rex: revenue audit cho [dự án] / thiết kế pricing / P&L review", agentId: "cfo-agent")
```

### Option D — Marketing Agent (cho content/SEO/analytics):
```
sessions_spawn(task: "Luna: [content brief / SEO task / analytics setup]", agentId: "marketing-agent")
```

### Option E-new — DevOps (cho deploy/infra/monitoring):
```
sessions_spawn(task: "Kane: [deploy task / server issue / CI setup]", agentId: "devops-agent")
```

### Option E-new — AI/ML (cho prompt/model optimisation):
```
sessions_spawn(task: "Neo: [prompt optimisation / model benchmark / RAG tuning]", agentId: "ai-agent")
```

### Option E-new — Data/Analytics:
```
sessions_spawn(task: "Sage: [analytics report / A/B test / conversion analysis]", agentId: "data-agent")
```

### Option E-new — Localisation:
```
sessions_spawn(task: "Hana: [translation / cultural review / UI strings]", agentId: "localisation-agent")
```

### Option E-new — Customer Success:
```
sessions_spawn(task: "Aria: [support script / onboarding flow / churn analysis]", agentId: "customer-success-agent")
```

### Option F — Thẳng PM (khi spec đã rõ):
```
sessions_spawn(task: "Kenji: [spec rõ ràng]", agentId: "pm-agent")
```

### Option G — Thẳng agent chuyên môn (quick fix):
```
sessions_spawn(task: "Fix bug: [mô tả cụ thể]", agentId: "backend-agent")
```

## Task Template chuẩn CMMI L4

### Khi giao cho PM:
```markdown
## Sprint Task: [Tên]
**Project:** cherry-longcare / new-project / ...
**From:** Iris (BA Analysis v1.0) + Zara (Architecture v1.0)
**Priority:** P1 / P2 / P3

### Architecture Decision (từ Zara)
- Stack: [tech stack]
- Pattern: [architecture pattern]
- Cost estimate: $X/month

### User Stories
- As a [user], I want [action] so that [benefit]

### Technical Tasks
| # | Task | Agent | Est | Depends on |
|---|---|---|---|---|
| T1 | Architecture review | Zara | 1h | - |
| T2 | Create DB schema | Fauna | 1h | T1 |
| T3 | Implement API | Axel | 2h | T2 |
| T4 | Security review | Cipher | 1h | T3 |
| T5 | Build UI | Nova | 2h | T3 |
| T6 | QA Testing | Tessa | 1h | T4, T5 |
| T7 | Marketing assets | Luna | 2h | T6 |

### Acceptance Criteria
- [ ] AC-1: ...
- [ ] AC-2: ...

### Definition of Done (CMMI L4 gates)
- [ ] Architecture approved by Zara
- [ ] Unit test coverage ≥ 80%
- [ ] Security review: 0 critical issues
- [ ] All integration tests pass
- [ ] Code reviewed
- [ ] Docs updated
- [ ] Marketing/SEO assets ready (nếu có launch)
```

## Agents Directory

| # | ID | Tên | Emoji | Workspace |
|---|---|---|---|---|
| 1 | `ba-agent` | Iris | 📊 | agents-team/ba-agent |
| 2 | `pm-agent` | Kenji | 📋 | agents-team/pm |
| 3 | `backend-agent` | Axel | ⚙️ | agents-team/backend-agent |
| 4 | `security-agent` | Cipher | 🔒 | agents-team/security-agent |
| 5 | `database-agent` | Fauna | 🗄️ | agents-team/database-agent |
| 6 | `frontend-agent` | Nova | 🎨 | agents-team/frontend-agent |
| 7 | `qa-agent` | Tessa | 🧪 | agents-team/qa-agent |
| 8 | `marketing-agent` | Luna | 📣 | agents-team/marketing-agent |
| 9 | `solution-architect` | Zara | 🏗️ | agents-team/solution-architect |
| 10 | `cfo-agent` | Rex | 💰 | agents-team/cfo-agent |
| 11 | `devops-agent` | **Kane** | 🚀 | agents-team/devops-agent |
| 12 | `data-agent` | **Sage** | 📊 | agents-team/data-agent |
| 13 | `localisation-agent` | **Hana** | 🌐 | agents-team/localisation-agent |
| 14 | `ai-agent` | **Neo** | 🤖 | agents-team/ai-agent |
| 15 | `customer-success-agent` | **Aria** | 🎧 | agents-team/customer-success-agent |
