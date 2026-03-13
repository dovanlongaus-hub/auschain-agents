# Dev Team Status Commands

## Lệnh Telegram — gõ thẳng cho Mochi

| Lệnh | Tác dụng |
|---|---|
| `/team` | Xem tổng quan toàn team |
| `/status iris` | BA Agent — đang phân tích gì |
| `/status kenji` | PM Agent — task nào đang chạy |
| `/status axel` | Backend — code gì |
| `/status cipher` | Security — review gì |
| `/status fauna` | Database — migration nào |
| `/status nova` | Frontend — UI nào |
| `/status tessa` | QA — test gì |
| `/team log` | Xem log công việc gần nhất |

## Cách Mochi xử lý lệnh `/status`

Khi nhận `/status [tên]` hoặc `/team`:
1. Đọc file log của agent đó: `agents-team/[agent]/work-log.md`
2. Check sessions đang chạy: `sessions_list()`
3. Tóm tắt ngắn gọn và trả lời

## Cách Mochi xử lý lệnh giao việc

Khi nhận yêu cầu lập trình từ Sếp:
→ Tự động spawn `ba-agent` (Iris) để phân tích trước

Ví dụ:
> "Làm tính năng X" → spawn Iris → Iris tạo spec → spawn Kenji → team làm

