# Quick Wins — 30 Ngày Đầu
**Ngày:** 2026-03-13 | **Rex 💰 CFO Agent**
**Mục tiêu:** $500–1,500 AUD MRR trong 30 ngày với effort thấp nhất

---

## 🏆 TOP 5 QUICK WINS

### #1 — Tích hợp Stripe vào visa-path-aus [Week 1]
**Revenue potential:** $500–2,000 AUD/tháng
**Effort:** Medium (1-2 ngày dev)
**Action:**
1. Tạo Stripe account (stripe.com) → lấy live keys
2. Tích hợp Stripe Checkout vào Pricing.jsx (thay #payment-section rỗng)
3. Đổi giá sang AUD: Free / $12/mo / $25/mo / $45/mo
4. Implement premium gate cho: MyPlan, EOI Generator, CV Upload, Document Tracker
5. Fix DNS → go live

**Tại sao làm trước:** Pricing page đã có, features đã build → chỉ thiếu payment flow.
**Target:** 10 subscribers tháng 1 = $120-450 AUD MRR

---

### #2 — Launch suong-chat có paid tier [Week 1-2]
**Revenue potential:** $200–800 AUD/tháng
**Effort:** Low (pricing page + Stripe)
**Action:**
1. Tạo landing page đơn giản với pricing: Free (5 req/day) → $9 AUD/tháng (unlimited)
2. Thêm rate limiting vào backend (free tier cap)
3. Integrate Stripe payment link (không cần code phức tạp — chỉ cần Stripe Payment Link)
4. Promote trong các group Facebook sinh viên Việt ở Sydney/Melbourne

**Tại sao làm được nhanh:** Stripe Payment Link không cần code — chỉ cần link chia sẻ.
**Target:** 20-50 sinh viên × $9 = $180–450 AUD/tháng

---

### #3 — Email list capture cho visa-path-aus [Week 1]
**Revenue potential:** Indirect — build audience để monetize sau
**Effort:** Very Low (1-2 giờ)
**Action:**
1. Thêm email signup form vào homepage: "Nhận cập nhật điểm SkillSelect + tin visa mới nhất"
2. Dùng Brevo (free up to 300 emails/day) hoặc Resend
3. Automate welcome email với top 5 tips PR
4. Goal: 500 subscribers trong tháng 1 → foundation cho promotion sau

**Tại sao quan trọng:** Email list = owned audience. 500 subscribers × 5% conversion × $12 = $300 MRR có thể trigger bất cứ lúc nào.

---

### #4 — B2B outreach cherry-longcare cho childcare centres [Week 2-3]
**Revenue potential:** $300–1,500 AUD/tháng (B2B có ARPU cao hơn)
**Effort:** Low-Medium (outreach + pricing page)
**Action:**
1. Identify cherry-longcare-au value prop rõ ràng (automation tool for childcare)
2. Tạo simple B2B pricing: $49/tháng per centre
3. List 20 Vietnamese-run childcare centres ở Sydney
4. Send personalized DM/email: "Tool free 30 ngày, sau đó $49/tháng"
5. Onboard 3-5 paying centres tháng 1

**Tại sao feasible:** Vietnamese community → trust, word of mouth mạnh. 5 centres × $49 = $245/tháng.

---

### #5 — Referral program cho visa-path-aus [Week 3-4]
**Revenue potential:** Multiplier effect — reduce CAC to $0
**Effort:** Low
**Action:**
1. Implement: "Giới thiệu 1 bạn → bạn nhận 1 tháng free, bạn bè được giảm 20%"
2. Vietnamese community share link tự nhiên khi thấy value
3. Track via UTM parameters (Luna sẽ setup)

**Tại sao powerful:** Vietnamese Australians trust recommendations từ cộng đồng hơn ads. Viral coefficient > 1 = organic growth free.

---

## TIMELINE 30 NGÀY

```
Week 1 (13-20/3):
  ✅ Fix DNS visa.longcare.au → live
  ✅ Tích hợp Stripe Checkout vào visa-path-aus
  ✅ Đổi pricing sang AUD
  ✅ Thêm email capture form
  ✅ Tạo Stripe Payment Link cho suong-chat

Week 2 (21-27/3):
  📣 Promote visa-path-aus trong Facebook groups Việt ở Úc
  📣 Promote suong-chat cho sinh viên childcare Sydney
  🔒 Implement premium feature gates
  🍒 Xác định cherry-longcare value prop + B2B pricing

Week 3 (28/3-3/4):
  📧 Welcome email sequence live
  🤝 Outreach 20 childcare centres
  📊 Setup GA4 + conversion tracking (Luna)
  
Week 4 (4-13/4):
  🔄 Review data, tối ưu conversion
  💬 Referral program live
  📈 Target: 30+ paying users tổng cộng
```

---

## REVENUE TARGET THÁNG 1

| Stream | Target users | ARPU | MRR |
|--------|-------------|------|-----|
| visa-path-aus subscriptions | 20 | $15 AUD | $300 |
| suong-chat subscriptions | 30 | $9 AUD | $270 |
| cherry-longcare B2B | 3 | $49 AUD | $147 |
| **Tổng** | | | **$717 AUD/mo** |

**Cost: ~$40 AUD/tháng → Net: ~$677 AUD profit tháng 1**
**Mục tiêu tháng 3: $2,000+ AUD MRR** (khi word of mouth kick in)
