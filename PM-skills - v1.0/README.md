# PM-skills (PRIVATE)

Bộ 9 Claude skill cho Project Manager chuẩn PMP/PMI, bám PMBOK® Guide 8th Edition.
Mỗi skill phải đảm bảo: an toàn dữ liệu, tuân thủ bảo mật, chính xác dữ liệu tuyệt đối (xem `SECURITY.md`).

| Skill | Vai trò |
|---|---|
| pm-router | Chọn skill phù hợp / thứ tự skill |
| pm-orchestrator | Điều phối nhiều skill để tạo output |
| pm-quality-auditor | Kiểm toán output theo PMBOK |
| planning-estimation-engine | Lập kế hoạch, ước lượng |
| quality-delivery-control | Chất lượng, kiểm soát phạm vi, nghiệm thu, DoD |
| stakeholder-intelligence | Quản lý stakeholder |
| risk-management | Quản lý rủi ro |
| governance-value-engine | Quản trị, giá trị, benefits |
| business-analysis-for-pm | BRD/FRD, user story, RTM, UAT |

## Cấu trúc
- `skills/<tên>/SKILL.md` (+ `references/` nếu có) — nguyên văn từ bản đã đồng bộ, chưa chỉnh sửa nội dung.
- `references/pmbok8-index.md` — index số trang PMBOK 8. **PDF không có trong repo**: đặt `pmbok8.pdf` ở máy local, trích bằng `pdftotext -layout -f X -l Y pmbok8.pdf -`.
- `docs/skill-map.md` — quan hệ giữa các skill, 7 performance domains, và các tham chiếu treo.

## Dùng
Copy từng thư mục trong `skills/` vào nơi Claude đọc skill của bạn (hoặc upload qua giao diện skill).
