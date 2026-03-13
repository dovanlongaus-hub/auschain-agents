# Dev Team — Agent Workflow v2

## Kiến trúc tổng thể

```
Sếp Long
    │
    │  Yêu cầu (tiếng Việt, có thể mơ hồ)
    ▼
🍡 Mochi (main) — Haiku
    │
    │  Raw request
    ▼
📊 BA Agent (Iris) — Sonnet  ← ĐIỂM VÀO DUY NHẤT
    │   Phân tích, làm rõ, tạo spec
    │   Dispatch tự động
    ▼
📋 PM Agent (Kenji) — Sonnet
    │   Nhận full spec từ Iris
    │   Quản lý tiến độ, blockers
    │
    ├─────────────────────────────────────┐
    │  (song song)                        │
    ▼                                     ▼
🗄️ Database Agent (Fauna)         🔒 Security Agent (Cipher)
   Haiku                             Sonnet (critical!)
   Schema + Migration                Threat model + Auth
    │                                     │
    └──────────────┬──────────────────────┘
                   │
                   ▼
            ⚙️ Backend Agent (Axel) — Haiku
               API + Business Logic
                   │
                   ▼
            🎨 Frontend Agent (Nova) — Haiku
               UI Components
                   │
                   ▼
            🧪 QA Agent (Tessa) — Haiku
               Test + Coverage + Security
                   │
          ┌────────┴────────┐
          │                 │
      ✅ PASS           ❌ FAIL → assign bug về đúng agent
          │
          ▼
    PM → Mochi → Sếp
    "Feature X done!"
```

## Model Assignment (cost-optimised)

| Agent | Tên | Model | Lý do |
|---|---|---|---|
| `ba-agent` | 📊 Iris | **Sonnet** | Reasoning sâu, phân tích yêu cầu phức tạp |
| `pm-agent` | 📋 Kenji | **Sonnet** | Điều phối, quyết định ưu tiên |
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

## Cách Mochi dùng team

### Option A — Qua BA (recommended cho mọi feature mới):
```
sessions_spawn(
  task: "Iris phân tích yêu cầu: [raw input từ Sếp]",
  agentId: "ba-agent"
)
```

### Option B — Thẳng PM (khi spec đã rõ):
```
sessions_spawn(
  task: "Kenji: [spec rõ ràng]",
  agentId: "pm-agent"
)
```

### Option C — Thẳng agent chuyên môn (quick fix):
```
sessions_spawn(
  task: "Fix bug: [mô tả cụ thể]",
  agentId: "backend-agent"
)
```

## Task Template chuẩn CMMI L4

### Khi giao cho PM:
```markdown
## Sprint Task: [Tên]
**Project:** cherry-longcare / new-project / ...
**From:** Iris (BA Analysis v1.0)
**Priority:** P1 / P2 / P3

### User Stories
- As a [user], I want [action] so that [benefit]

### Technical Tasks
| # | Task | Agent | Est | Depends on |
|---|---|---|---|---|
| T1 | Create DB schema | Fauna | 1h | - |
| T2 | Implement API | Axel | 2h | T1 |
| T3 | Security review | Cipher | 1h | T2 |
| T4 | Build UI | Nova | 2h | T2 |
| T5 | QA Testing | Tessa | 1h | T3, T4 |

### Acceptance Criteria
- [ ] AC-1: ...
- [ ] AC-2: ...

### Definition of Done (CMMI L4 gates)
- [ ] Unit test coverage ≥ 80%
- [ ] Security review: 0 critical issues
- [ ] All integration tests pass
- [ ] Code reviewed
- [ ] Docs updated
```

## Agents Directory

| ID | Tên | Workspace |
|---|---|---|
| `ba-agent` | 📊 Iris | agents-team/ba-agent |
| `pm-agent` | 📋 Kenji | agents-team/pm |
| `backend-agent` | ⚙️ Axel | agents-team/backend-agent |
| `security-agent` | 🔒 Cipher | agents-team/security-agent |
| `database-agent` | 🗄️ Fauna | agents-team/database-agent |
| `frontend-agent` | 🎨 Nova | agents-team/frontend-agent |
| `qa-agent` | 🧪 Tessa | agents-team/qa-agent |
