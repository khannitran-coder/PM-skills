---
name: pm-router
description: >
  Bộ định tuyến cho hệ sinh thái PM skills — quyết định dùng skill nào, theo thứ tự nào,
  khi yêu cầu của user liên quan 2+ mảng công việc PM cùng lúc hoặc user không biết bắt đầu
  từ đâu. Dùng khi: "tôi không biết nên dùng skill nào", "giúp tôi từ đầu đến cuối",
  "điều phối giúp tôi", "workflow hoàn chỉnh cho dự án X", vấn đề phức tạp cần charter +
  WBS + risk + stakeholder cùng lúc, hoặc bất kỳ request nào chạm vào nhiều hơn 1 domain
  PMBOK (Governance/Scope/Schedule/Finance/Stakeholders/Resources/Risk) trong cùng 1 lần hỏi.
  LUÔN dùng skill này TRƯỚC khi tự chọn 1 skill đơn lẻ nếu request có dấu hiệu đa domain.
  KHÔNG dùng skill này để chấm điểm/audit 1 output đã có sẵn — dùng `pm-quality-auditor`
  cho việc đó thay vì tự audit trong skill này.
  Created: 11/09/2026 - v2
---

# PM Router

Bộ định tuyến trung tâm cho hệ sinh thái PM skills. Nhiệm vụ duy nhất: **phân tích request
→ chọn đúng skill/chuỗi skill → tổng hợp output**. Việc chấm chất lượng output thuộc về
`pm-quality-auditor` — skill này **gọi sang** chứ không tự làm, để tránh 2 nơi giữ trùng
logic đối soát PMBOK (nguồn gốc bug đã xảy ra trước đây).

> **Cấu trúc PMBOK 8 đầy đủ (6 nguyên tắc, 7 Performance Domain, tên process chuẩn) sống ở
> `pm-quality-auditor`.** Skill này chỉ giữ tên domain (không giải thích lại chi tiết) để
> phục vụ routing. Nếu cần đối soát sâu, gọi `pm-quality-auditor`.

---

## SKILL MAP — Hệ sinh thái PM Skills

7 Performance Domain của PMBOK 8: **Governance · Scope · Schedule · Finance · Stakeholders ·
Resources · Risk**.

| Skill ID | Tên | PMBOK 8 Domain(s) | Focus Area(s) chính | Kích hoạt khi |
|---|---|---|---|---|
| `governance-value-engine` | Governance & Value | Governance | Initiating → Planning | Business case, charter, ROI, benefits realization |
| `planning-estimation-engine` | Planning & Estimation | Scope + Schedule | Planning | WBS/VBS, schedule, CPM, estimation, development approach |
| `risk-management` | Risk Management | Risk | Planning + M&C | Risk register, RAID, threats/opportunities, overall risk |
| `stakeholder-intelligence` | Stakeholder Intelligence | Stakeholders | Initiating → Executing → M&C | Stakeholder mapping, engagement strategy, communication plan |
| `quality-delivery-control` | Quality & Delivery | Governance *(QA)* + Scope *(QC/Validate)* | Executing + M&C | DoD, CCB/change control, acceptance criteria, phase gate |
| `pm-workflow-engine` | Workflow Engine | Governance *(execution)* + Stakeholders *(comms)* | Executing + M&C | Task extraction, Jira issues, status/progress report |
| `pm-dashboard-builder` | Dashboard Builder | Governance + Schedule + Finance + Risk *(visualization layer)* | M&C | Dashboard trực quan, KPI, EVM, Gantt, risk heatmap |
| `jira-looker-dashboard` | Jira-Looker Pipeline | Governance + Schedule *(reporting)* | M&C | Jira → Sheets → Looker automation |
| `pm-brand-content` | Brand & Content | *(ngoài phạm vi PMBOK)* | — | LinkedIn, content strategy, personal branding |

> **Lưu ý quan trọng — đã sửa 1 bug khi tách skill:** bản gộp cũ (`pm-orchestrator`) có liệt
> kê 1 skill tên `pm-assistant` trong Skill Map nhưng **skill này không tồn tại** trong hệ
> sinh thái hiện tại. Đã loại khỏi bảng. Nếu user cần "quick report, basic Jira task" đơn
> giản, route sang `pm-workflow-engine` (đã cover chức năng đó) thay vì gọi 1 skill ma.

> **`quality-delivery-control` là dual-domain thật sự** (không phải lỗi mapping): PMBOK 8 gộp
> Quality vào domain Scope, nhưng quy trình Quality Assurance (`Manage Quality Assurance`)
> vẫn nằm trong domain Governance, còn Quality Control/Acceptance (`Monitor and Control
> Scope`, `Validate Scope`) nằm trong domain Scope. Skill này hợp lệ khi bắc cầu cả hai.

> `pm-brand-content` nằm ngoài phạm vi PMBOK — router route độc lập, không chain với các
> skill methodology khác trừ khi user yêu cầu rõ (VD: viết bài LinkedIn kể lại 1 dự án vừa
> quản lý — khi đó có thể chain sau khi 1 skill PMBOK khác xong việc).

---

## Step R0 — Intake & Triage

**Layer 1 — Focus Area (PMBOK 8) / giai đoạn dự án đang ở đâu:**
```
[ ] Initiating           → governance-value-engine + stakeholder-intelligence
[ ] Planning             → planning-estimation-engine là trung tâm
[ ] Executing            → pm-workflow-engine / risk-management / stakeholder-intelligence
[ ] Monitoring & Controlling → pm-dashboard-builder / pm-workflow-engine / risk-management
[ ] Closing               → quality-delivery-control / governance-value-engine
[ ] Multi-phase           → xem Reference Chains bên dưới
```

**Layer 2 — Domain(s) liên quan (7 domain PMBOK 8):**
```
[ ] Governance             → governance-value-engine (charter/benefits) hoặc
                              quality-delivery-control (QA/change control)
[ ] Scope                  → planning-estimation-engine (WBS/VBS) hoặc
                              quality-delivery-control (validate scope/DoD)
[ ] Schedule                → planning-estimation-engine
[ ] Finance                 → planning-estimation-engine hoặc pm-dashboard-builder (EVM)
[ ] Stakeholders             → stakeholder-intelligence
[ ] Resources                → (chưa có skill riêng — flag MISSING nếu user cần sâu về
                                team building/resource leveling, không ép vào skill khác)
[ ] Risk                     → risk-management
```

**Layer 3 — Complexity:**
```
1 domain   → Route trực tiếp đến 1 skill, không cần Execution Plan
2 domains  → Chain 2 skills, chạy luôn rồi gọi pm-quality-auditor audit kết quả cuối
3+ domains → Lập Execution Plan, đợi user confirm trước khi chạy chuỗi
```

---

## Step R1 — Execution Plan (dùng khi 2+ skills)

```
🎯 EXECUTION PLAN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Yêu cầu: [tóm tắt 1 dòng]
PMBOK 8 domain(s): [Governance / Scope / ... liệt kê domain liên quan]

Step 1 → [skill-name]
  Mục tiêu: [output cụ thể]
  Input: [dữ liệu sẽ dùng]

Step 2 → [skill-name]
  Mục tiêu: [output cụ thể]
  Input: [output từ Step 1 + bổ sung nếu có]

[Step N nếu có]

Output tổng hợp: [mô tả deliverable cuối]
Audit: sau khi hoàn tất chuỗi (hoặc sau mỗi step nếu là dự án rủi ro cao), gọi
       pm-quality-auditor đối soát trước khi giao cho user.

Tiến hành? Hoặc cần điều chỉnh chuỗi?
```

---

## Reference Chains (đã đối soát domain PMBOK 8)

**Chain A — Project Initiation Package** *(Governance → Stakeholders → Scope/Schedule → Risk)*
```
governance-value-engine → stakeholder-intelligence → planning-estimation-engine → risk-management
```

**Chain B — Planning Cycle** *(Scope/Schedule → Risk → Quality)*
```
planning-estimation-engine → risk-management → quality-delivery-control
```

**Chain C — Execution Health Check** *(Governance/Stakeholders → M&C visualization → Risk)*
```
pm-workflow-engine → pm-dashboard-builder → risk-management
```

**Chain D — Stakeholder Crisis** *(Stakeholders → Risk → Governance/Stakeholders execution)*
```
stakeholder-intelligence → risk-management → pm-workflow-engine
```

**Chain E — Delivery Gate / Phase Closing** *(Scope validate → Governance execution → Governance closing)*
```
quality-delivery-control → pm-workflow-engine → governance-value-engine
```

Sau khi 1 chain chạy xong, **luôn đề nghị user gọi `pm-quality-auditor`** để đối soát output
tổng hợp trước khi coi là final — router không tự chấm điểm.

---

## Audit-Only Requests → chuyển hẳn sang pm-quality-auditor

Nếu user paste 1 output đã có sẵn và chỉ muốn "check/audit/review" (không cần tạo mới gì),
đây **không phải việc của router**. Nói rõ và chuyển hướng:
```
User: "Check kết quả này: [output]"
→ Đây là audit-only, không cần routing. Dùng pm-quality-auditor cho việc này.
```

---

## QUICK REFERENCE

```
Nhận request
      │
      ▼
Chỉ audit 1 output có sẵn? ──[Có]──→ Chuyển sang pm-quality-auditor, dừng ở đây
      │[Không — cần TẠO/LÀM gì đó]
      ▼
Đếm domain PMBOK 8 liên quan
      │
  1 → Route trực tiếp, không chain
  2 → Chain ngắn, chạy luôn
 3+ → Execution Plan → user confirm → chạy chuỗi
      │
      ▼
Xong chuỗi → gọi pm-quality-auditor đối soát output tổng hợp
      │
Phát hiện domain không có skill nào cover? → flag MISSING, đề xuất build skill mới
```

---

## GUARDRAILS

1. **Không override user intent** — user chỉ định skill cụ thể → execute đúng skill đó, không
   tự ý đổi sang skill khác "vì router nghĩ hợp hơn".
2. **Không tự audit nội bộ** — audit chất lượng luôn chuyển sang `pm-quality-auditor`, kể cả
   khi router tự chạy 1 chain — không viết lại logic 4-tiêu-chí ở đây.
3. **Domain không có skill cover → nói thẳng** — log là `MISSING`, đề xuất build skill mới,
   không ép request vào 1 skill không phù hợp chỉ để "có gì đó trả lời".
4. **Không route đến skill không tồn tại** — luôn đối chiếu Skill Map ở trên trước khi gọi
   tên 1 skill; nếu nghi ngờ 1 skill đã bị xóa/đổi tên, kiểm tra trước khi route.
5. **Transparent về Execution Plan** — với 3+ domain, luôn đợi user confirm trước khi chạy,
   không tự ý chạy hết rồi mới báo cáo.
