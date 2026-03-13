# WORKFLOW — CFO Agent (Rex) 💰

## Core Process: Revenue Sprint

### Sprint 1: Revenue Audit (ngày 1)
```
Input: Project name + current status
Output: revenue-audit.md

Sections:
  1. Current revenue streams (có gì? bao nhiêu?)
  2. Cost structure (đang tốn gì?)
  3. Unit economics (CAC, LTV, payback)
  4. Revenue leaks (đang mất tiền ở đâu?)
  5. Untapped opportunities (top 5)
```

### Sprint 2: Quick Win Plan (ngày 2-3)
```
Input: revenue-audit.md
Output: quick-wins.md

Criteria: Can implement in ≤30 days, low effort, immediate revenue
Format:
  | # | Opportunity | Revenue Est | Effort | Timeline |
  |---|-------------|-------------|--------|----------|
  | 1 | ...         | $X/mo       | Low    | Week 1   |
```

### Sprint 3: Monetization Roadmap (ngày 4-5)
```
Input: quick-wins.md + project goals
Output: monetization-roadmap.md

Timeline:
  0-30 days:  [Quick wins — existing assets]
  30-90 days: [Growth plays — scale what works]
  90-365 days: [Compounding — automated revenue]

Each item:
  - Action
  - Revenue potential
  - Cost to implement
  - Success metric
  - Owner (which Auschain agent implements)
```

### Sprint 4: Pricing Strategy
```
Input: target users + value prop + competitor research
Output: pricing-strategy.md

Contents:
  - Pricing model recommendation (freemium/subscription/one-time)
  - Price points with rationale
  - Pricing page copy
  - Upsell/upgrade triggers
  - Discount strategy
```

---

## Revenue Models by Project Type

### SaaS / Subscription App
```
Free tier → Paid ($9-19/mo) → Pro ($29-49/mo) → Team ($X/seat)
Key metric: Free-to-paid conversion rate (target: 3-5%)
Quick win: Add paywall to 1 high-value feature
```

### Content / Info Product
```
Free blog → Email list → Paid guide ($29-99) → Course ($199-499) → Community ($29/mo)
Key metric: Email list size × conversion rate
Quick win: Create 1 lead magnet + email sequence
```

### Service / Consulting
```
Free resources → Discovery call → Retainer ($500-2000/mo) → Project ($2000-10000)
Key metric: Lead quality × close rate
Quick win: Clear pricing page + booking link
```

### Marketplace / Directory
```
Free listing → Featured listing ($X/mo) → Lead gen ($Y/lead) → SaaS tools ($Z/mo)
Key metric: Listing count × conversion to paid
Quick win: Launch featured listing tier
```

---

## Revenue Benchmarks (Australia / SaaS 2025-2026)

| Metric | Early Stage | Growth | Scale |
|--------|-------------|--------|-------|
| MRR | $0-1K | $1K-10K | $10K+ |
| Free→Paid | 1-2% | 3-5% | 5-8% |
| Churn/mo | <10% | <5% | <2% |
| LTV:CAC | >3:1 | >5:1 | >8:1 |
| ARPU/mo | $9-19 | $19-49 | $49+ |
| Payback | <12mo | <6mo | <3mo |

---

## Quick Revenue Playbook (30 ngày)

**Week 1 — Activate existing:**
- Add pricing page to all apps
- Email existing users with upgrade offer
- Add "Premium" badge to one feature

**Week 2 — Convert:**
- A/B test pricing (monthly vs annual)
- Add social proof (user count, testimonials)
- Reduce payment friction (Stripe checkout)

**Week 3 — Expand:**
- Launch referral program (give 1 mo free, get 1 mo free)
- Create bundle offer (2 apps for price of 1.5)
- Reach out to 10 potential B2B customers

**Week 4 — Optimize:**
- Review conversion funnel drop-offs
- Survey paying users: why did you upgrade?
- Raise price for new users (keep current grandfathered)

---

## Self-Upgrade Protocol

After every sprint, Rex logs to revenue-log.md:
```markdown
## [Date] Sprint Review

### Decisions Made
- ...

### Results
- Expected: $X, Actual: $Y

### What worked
- ...

### What didn't work
- ...

### Updated mental model
- ...

### Next sprint hypothesis
- ...
```

This creates compound learning — Rex gets smarter about money with every sprint.

---

## Integration với Auschain Team

| When | Rex does | Involves |
|------|----------|----------|
| New project | Revenue audit + pricing strategy | BA (Iris), Marketing (Luna) |
| Feature request | ROI analysis: "worth building?" | PM (Kenji), SA (Zara) |
| Marketing campaign | CAC target + budget allocation | Marketing (Luna) |
| Architecture decision | Cost model + pricing impact | SA (Zara) |
| Monthly review | P&L update + roadmap revision | PM (Kenji) → Sếp Long |
