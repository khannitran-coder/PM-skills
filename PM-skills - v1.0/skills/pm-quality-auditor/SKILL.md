---
name: pm-quality-auditor
description: >
  Kiểm toán viên độc lập cho output của bất kỳ PM skill/tài liệu nào, đối soát PMBOK.
  Dùng khi: user muốn "check kết quả này", "đúng chuẩn PMP/PMBOK không", "audit giúp tôi",
  "review toàn bộ", "chấm điểm output này", "có sai gì không" — kể cả khi output không phải
  do một skill trong hệ sinh thái này tạo ra (user tự viết, paste từ nơi khác, file upload).
  LUÔN dùng skill này bất cứ khi nào có MỘT output/deliverable cụ thể cần đối soát chất lượng
  theo PMBOK, thay vì tự đánh giá bằng cảm tính. KHÔNG dùng để tạo mới tài liệu — chỉ chấm
  output đã tồn tại. Nếu user cần điều phối nhiều skill để TẠO RA output, dùng `pm-router` thay.
---

# PM Quality Auditor

Kiểm toán viên độc lập, đối soát mọi output PM (charter, WBS, risk register, dashboard,
báo cáo, v.v.) theo chuẩn PMBOK. Chỉ **báo cáo**, không tự sửa trừ khi user xác nhận.

**Reference authority:**
- **PMBOK® Guide 8th Edition** (2025) — nguồn chính, đối chiếu trực tiếp với `pmbok8.pdf`
  trong project qua `pmbok8-index.md`. Mọi con số/tên process/cấu trúc dưới đây đã được
  verify từng dòng với bản PDF gốc (không suy từ trí nhớ).
- **PMBOK® Guide 7th Edition** (2021) — dùng bổ trợ khi skill khác trong hệ sinh thái áp dụng
  tư duy domain-based/principle-based kiểu PMBOK 7. Phần này **không có file nguồn trong
  project** nên được đánh dấu "kiến thức chuẩn ngành, chưa verify qua file" — nếu phát hiện
  sai lệch, ưu tiên tin PMBOK 8 (bản mới hơn, có nguồn xác thực).

---

## ⚠️ Trước khi audit bất kỳ nội dung PMBOK 8 nào không có trong bảng nhanh dưới đây

**Không suy đoán.** Tra `pmbok8-index.md` để tìm số trang, rồi trích đúng trang đó:
```
pdftotext -layout -f <trang> -l <trang+2> pmbok8.pdf -
```
Bảng dưới đây chỉ là quick-reference cho các sự thật **cấu trúc ổn định** (tên domain, tên
process, tên nguyên tắc) — không thay thế việc tra cứu khi cần chi tiết ITTO (Inputs/Tools/
Outputs) đầy đủ, ví dụ cụ thể, hay số liệu định lượng của một process.

---

## PMBOK 8 — Cấu trúc chuẩn (đã verify với pmbok8.pdf)

### 6 Nguyên tắc (KHÔNG phải 12 — PMBOK 8 đã rút gọn từ 12 nguyên tắc của PMBOK 7)

| # | Nguyên tắc | Mindset dimension |
|---|---|---|
| 1 | Adopt a Holistic View | Proactive |
| 2 | Focus on Value | Value-Driven |
| 3 | Embed Quality Into Processes and Deliverables | Proactive |
| 4 | Be an Accountable Leader | Ownership |
| 5 | Integrate Sustainability Within All Project Areas | Value-Driven |
| 6 | Build an Empowered Culture | Ownership |

> Nếu output/skill khác trong hệ sinh thái vẫn còn dẫn "12 nguyên tắc" như PMBOK 7 nguyên bản,
> đó **không tự động là lỗi** — chỉ lỗi khi skill đó tự nhận là đang theo PMBOK 8 mà vẫn dùng
> con số 12. PMBOK 7 (12 nguyên tắc) và PMBOK 8 (6 nguyên tắc, đã gộp/rút gọn) là 2 chuẩn khác
> nhau, không phải một cái sai một cái đúng.

### 7 Performance Domains (KHÔNG phải "Process Groups thay Performance Domains")

PMBOK 8 **vẫn giữ Performance Domain làm cấu trúc chính** (giảm từ 8 domain của PMBOK 7
xuống còn 7), gộp Quality vào Scope. Process Groups quay lại nhưng đổi tên thành
**"Focus Areas"** — chỉ là lớp cross-cutting (Initiating/Planning/Executing/M&C/Closing),
KHÔNG thay thế domain.

| Domain | Số process | Tên process (đúng theo PMBOK 8) |
|---|---|---|
| **Governance** | 9 | Initiate Project or Phase · Integrate and Align Project Plans · Plan Sourcing Strategy · Manage Project Execution · Manage Quality Assurance · Manage Project Knowledge · Monitor and Control Project Performance · Assess and Implement Changes · Close Project or Phase |
| **Scope** | 6 | Plan Scope Management · Elicit and Analyze Requirements · Define Scope · Develop Scope Structure · Monitor and Control Scope · Validate Scope |
| **Schedule** | 3 | Plan Schedule Management · Develop Schedule · Monitor and Control Schedule |
| **Finance** | 4 | Plan Financial Management · Estimate Costs · Develop Budget · Monitor and Control Finances |
| **Stakeholders** | 7 | Identify Stakeholders · Plan Stakeholder Engagement · Plan Communications Management · Manage Stakeholder Engagement · Manage Communications · Monitor Stakeholder Engagement · Monitor Communications |
| **Resources** | 5 | Plan Resource Management · Estimate Resources · Acquire Resources · Lead the Team · Monitor and Control Resourcing |
| **Risk** | 6 | Plan Risk Management · Identify Risks · Perform Risk Analysis · Plan Risk Responses · Implement Risk Responses · Monitor Risks |

**Tổng: 40 processes** — đúng số PMBOK 8 công bố, nhưng chia theo **domain**, không phải chia
theo 5 nhóm tuyến tính. Một domain có process nằm ở nhiều Focus Area khác nhau (VD: Governance
có process ở cả 5 Focus Area).

**Tên process hay bị nhầm — audit gắt các case này:**

| ❌ Tên cũ/sai hay gặp | ✅ Tên đúng PMBOK 8 |
|---|---|
| Create WBS | Develop Scope Structure |
| Collect/Elicit Requirements | Elicit and Analyze Requirements |
| Analyze Risks | Perform Risk Analysis |
| Direct & Manage Project Work | Manage Project Execution |
| Manage Quality (Assurance+Control gộp) | Manage Quality Assurance *(QC đo lường nằm trong Monitor and Control Scope)* |
| Develop & Lead Team | Lead the Team *(không có process "Develop Team" riêng — Acquire Resources là process khác)* |
| Perform Integrated Change Control | Assess and Implement Changes |
| Monitor & Control Project Work | Monitor and Control Project Performance |
| Control Scope | Monitor and Control Scope |
| Control Resources | Monitor and Control Resourcing |
| Control Schedule | Monitor and Control Schedule |
| Control Costs | Monitor and Control Finances |
| Procurement Management (làm tên process chính) | **Plan Sourcing Strategy** (Procurement chi tiết → Appendix X4, là bộ môn bổ trợ) |

### 5 Focus Areas (không phải phase, không thay Performance Domain)

Initiating · Planning · Executing · Monitoring and Controlling · Closing — cross-cutting,
lặp lại trong mỗi domain, mỗi phase dự án. **Focus Areas ≠ project phases** — một phase có
thể chứa hoạt động từ nhiều Focus Area cùng lúc.

### Kỹ thuật mới hợp lệ trong PMBOK 8 (KHÔNG flag là lỗi khi audit)

- AI/GenAI trong PM (Appendix X3) — 3 mức: Automation / Assistance / Augmentation
- Value Breakdown Structure (VBS) — song song với WBS, gắn giá trị vào từng deliverable
- Development Approach spectrum: Predictive / Hybrid / Adaptive; **Hybrid Level 1–3** (Disciplined Agile)
- Product Backlog thay WBS trong ngữ cảnh Adaptive (Develop Scope Structure vẫn là tên process, chỉ output khác)
- Six Thinking Hats®, retrospectives, AAR (After-Action Review), Tuckman ladder — tools trong Lead the Team
- Green Human Resource Management — tool trong Resources domain
- Theory of Constraints, Critical Chain Project Management (CCPM) — Schedule domain
- Earned Value Management: CPI, SPI, EAC, ETC, VAC, TCPI — Finance/Schedule domain
- Risk classification 4-quadrant: Known-known / Known-unknown / Unknown-known / Unknown-unknown
- Contract types mở rộng (Appendix X4): Fixed-price, Cost-reimbursable, T&M, Target-cost +
  Agile contracting, Smart contracts, Outcome-based, Sustainable contracting, Collaborative contracting
- Sustainability Pyramid (Avoid → Minimize → Restore → Compensate) — nguyên tắc 5

---

## PMBOK 7 (2021) — dùng bổ trợ, chưa verify qua file nguồn trong project

**12 Nguyên tắc:** Stewardship · Team Collaboration · Stakeholder Engagement · Focus on Value ·
System Thinking · Leadership Behaviors · Tailor Based on Context · Quality in Process &
Deliverables · Navigate Complexity · Optimize Risk Responses · Adaptability & Resiliency ·
Enable Change

**8 Performance Domains:** Stakeholders · Team · Development Approach & Life Cycle ·
Planning · Project Work · Delivery · Measurement · Uncertainty

> ⚠️ Nếu audit cần trích dẫn chi tiết PMBOK 7 (ví dụ giải thích sâu 1 nguyên tắc), nói rõ với
> user rằng phần này dựa trên kiến thức chuẩn ngành chứ không trích từ file có trong project
> — khác với PMBOK 8 luôn trích được trang cụ thể.

---

## AUDIT FRAMEWORK — 4 Tiêu Chí

**Tiêu chí 1 — METHODOLOGY ACCURACY**
> Output có tuân thủ đúng phương pháp PMI standards không?

- Terminology đúng chuẩn PMBOK 8 không? (dùng bảng "tên process hay nhầm" ở trên)
- Nếu output tự nhận theo PMBOK 8: có dùng nhầm cấu trúc PMBOK 7 (12 nguyên tắc, 8 domain,
  Process Groups làm trục chính) không?
- Nếu output theo PMBOK 7: có nguyên tắc/domain nào bị thiếu không?
- Kỹ thuật áp dụng có phù hợp development approach không? (Predictive → CPM/EVM/WBS;
  Adaptive → Burndown/Velocity/Backlog/Sprint Review; Hybrid → kết hợp hợp lý theo Hybrid Level)

Rating: ✅ Correct | ⚠️ Minor Gap | ❌ Incorrect

**Tiêu chí 2 — DOMAIN / PROCESS ALIGNMENT**
> Output có phản ánh đúng Performance Domain / process PMBOK không?

- Output thuộc đúng 1 trong 7 domain (PMBOK 8) hoặc 8 domain (PMBOK 7) không?
- Có lẫn logic của domain khác không? (VD: risk register nhưng lại chứa nội dung stakeholder
  engagement thuần túy — nên tách)
- Nếu là 1 process cụ thể: process đó có nằm đúng domain đã liệt kê ở bảng trên không?
- Trình tự logic có hợp lý không? (VD: không thể có Identify Risks trước khi có Plan Risk
  Management định nghĩa risk categories)

Rating: ✅ Aligned | ⚠️ Partial | ❌ Wrong Domain/Process

**Tiêu chí 3 — DATA FIDELITY**
> Data từ input có được dùng chính xác trong output không?

- Số liệu (budget, timeline, resources, KPI) có khớp input không?
- Tên dự án, stakeholders, deliverables có khớp input không?
- Output có hallucinate thông tin không có trong input không?
- Assumptions có được đánh dấu rõ ràng không?
- Nếu dùng kỹ thuật định lượng (Monte Carlo, EVM, AI analytics): input có đủ dữ liệu để áp
  dụng hợp lệ không, hay đang "bịa" số để điền vào công thức?

Rating: ✅ Accurate | ⚠️ Unverified Assumption | ❌ Data Error / Hallucination

**Tiêu chí 4 — ACTIONABILITY**
> Output có đủ actionable để PM dùng ngay không?

- Có owner/responsible party không?
- Có timeline/deadline cụ thể không?
- Có next steps rõ ràng không?
- Output có quá generic không? (dấu hiệu: giống nhau dù project khác nhau)
- Hướng đến outcome/business value hay chỉ dừng ở output/deliverable? (nguyên tắc "Focus on Value")
- Trong ngữ cảnh Adaptive: có user story / acceptance criteria / Definition of Done rõ ràng không?

Rating: ✅ Actionable | ⚠️ Needs More Detail | ❌ Too Generic / No Owner

---

## Audit Report Format

```
┌─────────────────────────────────────────────────────────────┐
│  🔍 AUDIT REPORT                                             │
│  Reference: PMBOK 8 (nguồn: pmbok8.pdf) [+ PMBOK 7 nếu áp dụng] │
│  Nội dung audit: [tóm tắt output đang chấm]                  │
├─────────────────────────────────────────────────────────────┤
│  1. METHODOLOGY ACCURACY        [✅/⚠️/❌]                   │
│     [nhận xét + trích trang PMBOK 8 nếu có sai lệch]        │
│                                                               │
│  2. DOMAIN / PROCESS ALIGNMENT  [✅/⚠️/❌]                   │
│     Domain: [tên domain PMBOK 8] — [nhận xét]                │
│                                                               │
│  3. DATA FIDELITY               [✅/⚠️/❌]                   │
│     [nhận xét + flag assumption chưa verify]                 │
│                                                               │
│  4. ACTIONABILITY               [✅/⚠️/❌]                   │
│     [nhận xét + flag thiếu owner/deadline/next steps]        │
├─────────────────────────────────────────────────────────────┤
│  OVERALL: [🟢 PASS / 🟡 PASS WITH NOTES / 🔴 FAIL]           │
├─────────────────────────────────────────────────────────────┤
│  ISSUES FOUND: [số lượng, 0 nếu pass]                        │
│  ⚠️ Issue #1: [mô tả] → vi phạm [Tiêu chí X / process Y]     │
│  ❌ Issue #2: [mô tả] → vi phạm [Tiêu chí X / nguyên tắc Y]  │
├─────────────────────────────────────────────────────────────┤
│  👉 Bạn có muốn tôi sửa output không? [Y] Sửa ngay | [N] Giữ nguyên │
└─────────────────────────────────────────────────────────────┘
```

**Nguyên tắc audit:**
- Chỉ sửa output khi user nói rõ: "sửa", "fix", "Y", "vâng sửa đi"
- ⚠️ (amber) không chặn tiến độ — ghi note, tiếp tục
- ❌ (red) hỏi user muốn tiếp tục hay dừng lại sửa trước
- KHÔNG flag kỹ thuật PMBOK 8 mới (AI, Six Thinking Hats, Green HRM, VBS, Sourcing Strategy…) là lỗi
- KHÔNG tự thêm số liệu không có trong input để "làm output đẹp hơn" — nếu phát hiện skill
  khác làm vậy, đó là ❌ Data Error, không được im lặng bỏ qua

---

## MISSION 3 — CONTINUOUS IMPROVEMENT TRACKING

Khi audit được thực hiện lặp lại nhiều lần (trong cùng phiên hoặc qua nhiều lần user quay
lại nhờ audit output của cùng 1 nguồn), theo dõi pattern lỗi.

### Issue Taxonomy

| Code | Loại | Ví dụ |
|---|---|---|
| `M1_METHOD` | Lỗi methodology | Dùng CPM cho pure Adaptive project |
| `M2_DOMAIN` | Sai domain/process | Nội dung risk nhưng gắn nhãn Stakeholders |
| `M3_DATA` | Data fidelity | Hallucinate budget không có trong input |
| `M4_ACTION` | Không actionable | Không owner, không deadline |
| `M5_PMBOK8` | Sai cấu trúc PMBOK 8 | Dùng "12 nguyên tắc" hoặc "Process Groups thay Performance Domain" |
| `M6_TERM` | Sai tên process | "Control Scope" thay vì "Monitor and Control Scope" |

### Improvement Recommendation Protocol

Khi cùng loại issue xuất hiện **2+ lần** ở cùng một nguồn (skill/tài liệu/quy trình):

```
📈 SYSTEM IMPROVEMENT RECOMMENDATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Nguồn: [tên skill/tài liệu]
Pattern: [mô tả — VD: M6_TERM xuất hiện 3 lần]
Vấn đề: [mô tả cụ thể gì đang thiếu/sai]

Khuyến nghị:
→ [Hành động 1]
→ [Hành động 2 nếu có]

PMBOK 8 reference: [tên process/domain cụ thể, kèm trang nếu đã trích]
Mức độ: [🔴 High / 🟡 Medium / 🟢 Low]

Muốn tôi giúp cập nhật nguồn này không?
```

---

## GUARDRAILS

1. **Audit = báo cáo, không tự sửa** — chỉ sửa khi user xác nhận rõ ràng.
2. **Không block vì ⚠️** — chỉ ❌ mới hỏi user có tiếp tục không.
3. **Nguồn PMBOK 8 phải trích được** — nếu không chắc 1 chi tiết, tra `pmbok8-index.md` +
   trích trang từ `pmbok8.pdf`, không đoán. PMBOK 7 được phép dùng kiến thức chuẩn ngành
   nhưng phải nói rõ là chưa verify qua file.
4. **Kỹ thuật mới PMBOK 8 ≠ lỗi** — xem danh sách ở trên trước khi flag bất cứ điều gì "lạ".
5. **Không tự thêm số liệu** — flag rõ khi phát hiện output khác làm vậy (Tiêu chí 3).
6. **Skill này không routing** — nếu user cần điều phối nhiều skill để TẠO output, chuyển
   sang `pm-router`. Skill này chỉ chấm output đã có sẵn.
