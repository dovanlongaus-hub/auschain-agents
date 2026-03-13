# Revenue Audit — Auschain Projects
**Ngày:** 2026-03-13 | **Tác giả:** Rex 💰 (CFO Agent)

---

## TÓM TẮT ĐIỀU HÀNH

| Dự án | Stage | Revenue hiện tại | Potential/mo | Priority |
|-------|-------|-----------------|--------------|----------|
| visa-path-aus | MVP Live | $0 | $2,000–8,000 AUD | 🔴 P1 |
| suong-chat | Live (private) | $0 | $500–2,000 AUD | 🟡 P2 |
| cherry-longcare-au | Live (school tool) | $0 | $300–1,500 AUD | 🟡 P2 |
| An Lạc | Planning | $0 | $1,000–5,000 AUD | 🟢 P3 |

**Total addressable revenue nếu monetize đầy đủ:** $3,800–16,500 AUD/tháng

---

## 1. VISA-PATH-AUS 🛂

### Hiện trạng
- **URL:** visa.longcare.au (DNS pending)
- **Sản phẩm:** React SPA hỗ trợ người Việt ở Úc tìm hiểu lộ trình PR
- **Pricing page:** Đã có! Nhưng chưa có payment gateway tích hợp
- **AI:** DeepSeek (giá rẻ, ~$0.14/1M tokens)
- **Storage:** localStorage (không cần server DB)

### Pricing model đã thiết kế
| Plan | Giá/tháng (VND) | Giá AUD tương đương |
|------|-----------------|---------------------|
| Free | 0 | $0 |
| Cơ bản | 199,000 VND | ~$12 AUD |
| Chuyên nghiệp | 399,000 VND | ~$25 AUD |
| Chuyên gia | 699,000 VND | ~$45 AUD |

### Vấn đề cốt lõi
1. **Pricing page có nhưng không connect Stripe** — buttons chỉ scroll đến #payment-section trống
2. **DNS chưa live** — visa.longcare.au chưa resolve → không ai vào được
3. **Không có auth system** — không thể gate premium features
4. **Market confusion:** Giá bằng VND cho thị trường Úc — cần AUD

### Revenue leaks
- Mất 100% revenue vì không có checkout flow
- Giá VND không phù hợp thị trường Úc (người Việt ở Úc dùng AUD)
- Không có email capture → không build audience

### Sức mạnh
- Niche rõ ràng: Vietnamese Australians + PR/visa — pain point thực sự
- AI chat feature có value rõ ràng
- EOI Calculator, CV Upload, Document Tracker — premium features đã build
- Tốn AI cost rất thấp (DeepSeek)

---

## 2. SUONG-CHAT 💬

### Hiện trạng
- **URL:** suong.longcare.au
- **Sản phẩm:** AI study helper cho sinh viên Diploma Childcare ở Sydney
- **Tech:** Node.js, OpenClaw agent backend
- **Users hiện tại:** Không rõ — không có analytics

### Vấn đề
1. **Không có monetization gì** — hoàn toàn free
2. **Target hẹp:** Sinh viên Diploma Childcare tại Sydney — nhưng đây là niche có giá trị
3. **Không có user tracking** — không biết có bao nhiêu người dùng

### Potential
- Assignment writing + study help là **high-value service** cho sinh viên quốc tế
- Sinh viên Việt ở Úc thường trả tiền cho tutoring ($30-60/hr)
- Model: AI study companion $9-15 AUD/tháng vs. tutor $30/hr → obvious value

---

## 3. CHERRY-LONGCARE-AU 🍒

### Hiện trạng
- **URL:** cherry.longcare.au
- **Sản phẩm:** School notification/management tool (school-agent.js)
- **Tech:** Node.js server + data processing
- **Users:** Có vẻ là internal tool hoặc dùng cho 1 trường cụ thể

### Vấn đề
1. **Unclear value prop** — cần xem kỹ hơn để đánh giá
2. **Không có public-facing pricing**
3. **Potential B2B:** Nếu là tool cho trường → charge per school/centre

### Potential B2B play
- Childcare centres ở Úc có ngân sách IT
- Tool automation cho giáo viên/admin → $50-200 AUD/tháng per centre
- Niche: Vietnamese-run childcare centres ở Sydney

---

## 4. AN LẠC (Wellness App) 🌿

### Hiện trạng
- Đang planning, chưa có code
- Concept: meditation, mental health, wellness

### Revenue model phù hợp (khi build)
- Subscription $9.99 AUD/tháng
- Target: Vietnamese Australians có nhu cầu mental wellness
- USP: Nội dung tiếng Việt + cultural context

---

## COST STRUCTURE HIỆN TẠI

| Chi phí | Ước tính/tháng |
|---------|----------------|
| GCP VPS | ~$30 AUD |
| DeepSeek API | ~$1-5 AUD (hiện tại) |
| Domain longcare.au | ~$2 AUD |
| **Tổng** | **~$33-37 AUD/tháng** |

**Break-even:** Chỉ cần 3-4 user trả $12/tháng là đã cover toàn bộ infra cost!
