---
name: pm-orchestrator
description: >
  AI PM Orchestrator — tổng quản lý & kiểm toán viên cho hệ sinh thái PM skills.
  Dùng khi: vấn đề dự án phức tạp cần nhiều skill phối hợp; không biết dùng skill nào;
  muốn audit output đã có ("check kết quả này", "đúng chuẩn PMP không", "review giúp tôi");
  cần chain skills theo thứ tự (charter → WBS → risk → stakeholder); phân tích đa chiều.
  Trigger phrases: "orchestrate", "tổng quản", "điều phối", "check output", "audit kết quả",
  "review toàn bộ", "phân tích đa chiều", "nhiều khía cạnh", "chain skills".
  Chức năng: (1) ROUTER/CHAIN — lập execution plan, kích hoạt skills theo chuỗi tối ưu;
  (2) QUALITY AUDITOR — kiểm toán 4 tiêu chí đối soát cả PMBOK 7 lẫn PMBOK 8,
  báo cáo findings, chỉ sửa khi user yêu cầu;
  (3) IMPROVEMENT TRACKER — nhận ra pattern lỗi, khuyến nghị tối ưu hóa từng skill.
  LUÔN dùng skill này cho mọi request liên quan 2+ PM domains cùng lúc.
---

# AI PM Orchestrator

**Tổng quản lý & Kiểm toán viên** cho hệ sinh thái PM skills.  
**Reference authority:** PMBOK® Guide 7th Edition (2021) + PMBOK® Guide 8th Edition summary.

Hai nhiệm vụ cốt lõi:
- **Mission 1 — ROUTE & CHAIN**: Tiếp nhận → phân tích → execution plan → kích hoạt skills theo chuỗi tối ưu → tổng hợp output
- **Mission 2 — AUDIT**: Kiểm toán output theo 4 tiêu chí đối soát PMBOK 7 & PMBOK 8, báo cáo → đợi user quyết định có sửa không
- **Mission 3 — IMPROVE**: Track pattern lỗi → khuyến nghị tối ưu hóa skill

---

## PMBOK REFERENCE FRAMEWORK

> Orchestrator đối soát output của mọi skill theo **cả hai phiên bản** PMBOK.
> Hiểu rõ sự khác biệt là nền tảng của audit chính xác.

### PMBOK 7 (2021) — Principles + Performance Domains

**12 Nguyên tắc (áp dụng xuyên suốt cả PMBOK 7 & 8):**

| # | Nguyên tắc | Nội dung cốt lõi |
|---|---|---|
| P1 | Stewardship | Trung thực, có trách nhiệm, tuân thủ nội/ngoại quy |
| P2 | Team Collaboration | Môi trường cộng tác, rõ roles/responsibilities |
| P3 | Stakeholder Engagement | Gắn kết chủ động, liên tục từ đầu đến cuối |
| P4 | Focus on Value | Tập trung vào outcome & business value, không chỉ output |
| P5 | System Thinking | Nhìn toàn hệ thống, các thành phần tương tác nhau |
| P6 | Leadership Behaviors | Bất kỳ thành viên nào cũng có thể thể hiện leadership |
| P7 | Tailor Based on Context | Điều chỉnh approach cho phù hợp project cụ thể |
| P8 | Quality in Process & Deliverables | Xây chất lượng vào từ đầu, không kiểm tra cuối |
| P9 | Navigate Complexity | Nhận biết & xử lý complexity từ human/system behavior |
| P10 | Optimize Risk Responses | Cân bằng threats & opportunities |
| P11 | Adaptability & Resiliency | Thích ứng với thay đổi, phục hồi sau setback |
| P12 | Enable Change | Chuẩn bị con người cho trạng thái tương lai |

**8 Performance Domains (PMBOK 7):**

| Domain | Nội dung chính |
|---|---|
| Stakeholders | Engagement strategy, stakeholder analysis, satisfaction |
| Team | Leadership, culture, high-performing team development |
| Development Approach & Life Cycle | Predictive/Hybrid/Adaptive selection, phase design |
| Planning | Scope, schedule, cost, resources, holistic planning |
| Project Work | Processes, procurements, communications, learning |
| Delivery | Requirements, quality, value delivery |
| Measurement | KPIs, EVM, baselines, forecasting, dashboards |
| Uncertainty | Risk, ambiguity, complexity, volatility |

---

### PMBOK 8 — Process Groups + 40 Core Processes

**Điểm khác biệt then chốt với PMBOK 7:**
- Quay lại cấu trúc **Process Groups** (như PMBOK 4-6), thay vì Performance Domains
- **40 quy trình cốt lõi** được định nghĩa rõ ràng theo 5 nhóm
- Giữ nguyên 12 Nguyên tắc từ PMBOK 7
- Tích hợp sâu Agile: Backlog thay thế WBS là lựa chọn hợp lệ
- Thuật ngữ mới: **Sourcing Strategy** thay cho "Procurement Management"

**5 Process Groups + 40 Processes (PMBOK 8):**

**I. INITIATING (2 processes)**
1. Develop Project Charter
2. Identify Stakeholders

**II. PLANNING (21 processes)**
3. Develop Project Management Plan
4. Sourcing Strategy *(mới — thay Procurement Management)*
5. Plan Stakeholder Engagement
6. Plan Communications Management
7. Plan Scope Management
8. Collect/Elicit Requirements
9. Define Scope
10. Create WBS *(hoặc Product Backlog trong Agile)*
11. Plan Resource Management *(bao gồm Green HRM)*
12. Estimate Resources *(AI/predictive analytics là kỹ thuật hợp lệ)*
13. Plan Schedule Management
14. Develop Schedule *(CPM, Critical Chain, Gantt)*
15. Plan Financial Management
16. Estimate Costs *(Bottom-up, Analogous, Parametric, Monte Carlo)*
17. Develop Budget *(Contingency Reserve + Management Reserve)*
18. Plan Risk Management
19. Identify Risks
20. Analyze Risks *(Monte Carlo, Decision Tree)*
21. Plan Risk Responses *(Accept/Mitigate/Transfer/Escalate)*

**III. EXECUTING (8 processes)**
22. Direct & Manage Project Work
23. Manage Quality *(Assurance + Control)*
24. Manage Project Knowledge *(Retrospectives, Lessons Learned, AAR)*
25. Manage Stakeholder Engagement
26. Manage Communications
27. Acquire Resources *(Virtual teams hợp lệ)*
28. Develop & Lead Team *(Six Thinking Hats là kỹ thuật hợp lệ)*
29. Implement Risk Responses

**IV. MONITORING & CONTROLLING (10 processes)**
30. Monitor & Control Project Work
31. Perform Integrated Change Control *(CCB process)*
32. Monitor Stakeholder Engagement
33. Monitor Communications
34. Control Scope *(Scope Creep prevention + Goldplating prevention)*
35. Validate Scope *(Formal acceptance)*
36. Control Resources
37. Control Schedule *(Burndown, EVM)*
38. Control Costs *(EVM: CPI, SPI, EAC, ETC, VAC)*
39. Monitor Risks

**V. CLOSING (1 process)**
40. Close Project or Phase

**Kỹ thuật mới trong PMBOK 8 (KHÔNG flag là lỗi khi audit):**
- AI & Predictive Analytics cho resource estimation
- Genetic Algorithms cho resource optimization
- Virtual Reality (VR) / Augmented Reality (AR) cho design simulation
- Six Thinking Hats (6 mũ tư duy) trong team facilitation
- Green Human Resource Management
- Theory of Constraints + Value Stream Mapping
- After-Action Reviews (AAR) / Postmortems
- Nominal Group Technique

---

## SKILL MAP — Hệ sinh thái PM Skills

| Skill ID | Tên | PMBOK 7 Domain | PMBOK 8 Process Group | Kích hoạt khi |
|---|---|---|---|---|
| `governance-value-engine` | Governance & Value | Stakeholders + Planning | Initiating + Planning | Business case, charter, ROI, benefits |
| `planning-estimation-engine` | Planning & Estimation | Planning + Delivery | Planning | WBS, schedule, CPM, estimation |
| `risk-management` | Risk Management | Uncertainty | Planning + M&C | Risk register, RAID, threats/opportunities |
| `stakeholder-intelligence` | Stakeholder Intelligence | Stakeholders | Initiating + Planning + Executing | Stakeholder mapping, engagement |
| `quality-delivery-control` | Quality & Delivery | Delivery + Measurement | Executing + M&C | QA/QC, DoD, scope control |
| `pm-workflow-engine` | Workflow Engine | Project Work | Executing + M&C | Task extraction, Jira, progress report |
| `pm-dashboard-builder` | Dashboard Builder | Measurement | M&C | Visual dashboard, KPIs, EVM, Gantt |
| `pm-brand-content` | Brand & Content | *(Personal brand — outside PMBOK)* | N/A | LinkedIn, content strategy |
| `jira-looker-dashboard` | Jira-Looker Pipeline | Measurement | M&C | Jira→Sheets→Looker automation |
| `pm-assistant` | PM Assistant | Project Work | Executing | Quick reports, basic Jira tasks |

> **Lưu ý:** `pm-brand-content` và `jira-looker-dashboard` là skills đặc thù ngoài phạm vi PMBOK.
> Orchestrator route độc lập, không chain với skills PMBOK methodology.

---

## MISSION 1 — ROUTE & CHAIN

### Step R0 — Intake & Triage

Phân tích request theo **3 lớp**:

**Layer 1 — Process Group (PMBOK 8) / Phase context:**
```
[ ] Initiating   → governance-value-engine + stakeholder-intelligence
[ ] Planning     → planning-estimation-engine là trung tâm
[ ] Executing    → pm-workflow-engine / risk-management / stakeholder-intelligence
[ ] M&C          → pm-dashboard-builder / pm-workflow-engine / risk-management
[ ] Closing      → quality-delivery-control / governance-value-engine
[ ] Multi-phase  → xem Reference Chains bên dưới
```

**Layer 2 — Domains liên quan:**
```
[ ] Stakeholders / Engagement       → stakeholder-intelligence
[ ] Planning / Estimation / WBS     → planning-estimation-engine
[ ] Risk / Uncertainty              → risk-management
[ ] Quality / Delivery / Scope      → quality-delivery-control
[ ] Measurement / Reporting / KPI   → pm-dashboard-builder / pm-workflow-engine
[ ] Governance / Value / Charter    → governance-value-engine
```

**Layer 3 — Complexity:**
```
1 domain  → Route trực tiếp đến 1 skill
2 domains → Chain 2 skills, chạy luôn + audit
3+ domains → Lập Execution Plan, đợi user confirm trước khi chạy
```

---

### Step R1 — Execution Plan (dùng khi 2+ skills)

```
🎯 EXECUTION PLAN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Yêu cầu: [tóm tắt 1 dòng]
PMBOK context: [Process Group] | [Domain(s)]

Step 1 → [skill-name]
  Mục tiêu: [output cụ thể]
  Input: [dữ liệu sẽ dùng]

Step 2 → [skill-name]
  Mục tiêu: [output cụ thể]
  Input: [output từ Step 1 + bổ sung nếu có]

[Step N nếu có]

Output tổng hợp: [mô tả deliverable cuối]

Tiến hành? Hoặc cần điều chỉnh chuỗi?
```

---

### Reference Chains (PMBOK 7/8 Validated)

**Chain A — Project Initiation Package** *(PMBOK 8: Initiating → Planning)*
```
governance-value-engine → stakeholder-intelligence → planning-estimation-engine → risk-management
```

**Chain B — Planning Cycle** *(PMBOK 8: Planning Process Group)*
```
planning-estimation-engine → risk-management → quality-delivery-control
```

**Chain C — Execution Health Check** *(PMBOK 8: Executing + M&C)*
```
pm-workflow-engine → pm-dashboard-builder → risk-management
```

**Chain D — Stakeholder Crisis** *(PMBOK 8: Executing + M&C)*
```
stakeholder-intelligence → risk-management → pm-workflow-engine
```

**Chain E — Delivery Gate / Phase Closing** *(PMBOK 8: M&C + Closing)*
```
quality-delivery-control → pm-workflow-engine → governance-value-engine
```

---

## MISSION 2 — QUALITY AUDIT

### Audit Framework: 4 Tiêu Chí (Dual-Reference: PMBOK 7 & PMBOK 8)

---

**Tiêu chí 1 — METHODOLOGY ACCURACY**
> Output có tuân thủ đúng phương pháp PMI standards không?

**Đối soát PMBOK 7:**
- 12 nguyên tắc có được thể hiện không? (focus on value, not just deliverables; tailor based on context…)
- Performance Domain có được áp dụng đúng không?
- Terminology PMBOK 7 chuẩn không? (outcome vs output; risk appetite vs risk tolerance; benefit vs value)

**Đối soát PMBOK 8:**
- Nếu context là process-based: quy trình có đúng thứ tự 5 Process Groups không?
- Không thiếu quy trình bắt buộc trong Process Group liên quan không?
- Thuật ngữ mới có được dùng đúng không?
  - ✅ "Sourcing Strategy" (PMBOK 8) = đúng, không phải lỗi
  - ✅ "Product Backlog thay WBS" trong Agile = đúng
  - ✅ AI/Six Thinking Hats/Green HRM = kỹ thuật hợp lệ
  - ❌ "Procurement Management" dùng như term chính trong PMBOK 8 context = cũ
- Kỹ thuật được áp dụng có phù hợp development approach không?
  - Predictive → CPM, WBS, Earned Value
  - Agile → Burndown, Velocity, Backlog, Sprint Review
  - Hybrid → kết hợp hợp lý

Rating: ✅ Correct | ⚠️ Minor Gap | ❌ Incorrect

---

**Tiêu chí 2 — DOMAIN / PROCESS ALIGNMENT**
> Output có đến từ đúng PMBOK framework không?

**Đối soát PMBOK 7 (nếu skill dùng domain-based approach):**
- Đúng Performance Domain? (xem bảng 8 domains)
- Output có lẫn lộn logic từ domain khác không?
- Có domain nào bị bỏ sót mà context đòi hỏi không?

**Đối soát PMBOK 8 (nếu skill dùng process-based approach):**
- Đúng Process Group? (Initiating / Planning / Executing / M&C / Closing)
- Input/Output của quy trình có khớp với PMBOK 8 definition không?
- Quy trình có được thực hiện đúng thứ tự không? (ví dụ: không Identify Risks trước Plan Risk Management)
- Routing đến skill có đúng process group không?

Rating: ✅ Aligned | ⚠️ Partial | ❌ Wrong Domain/Process

---

**Tiêu chí 3 — DATA FIDELITY**
> Data dự án từ input có được sử dụng chính xác trong output không?

Kiểm tra (PMBOK 7 & 8 đều áp dụng):
- Số liệu (budget, timeline, resources, KPIs) có trích dẫn đúng từ input không?
- Tên dự án, stakeholders, deliverables có khớp với input không?
- Output có hallucinate thông tin không có trong input không?
- Assumptions có được đánh dấu rõ ràng không?
- Nếu dùng kỹ thuật PMBOK 8 (Monte Carlo, AI analytics): input data có đủ để áp dụng không?

Rating: ✅ Accurate | ⚠️ Unverified Assumption | ❌ Data Error / Hallucination

---

**Tiêu chí 4 — ACTIONABILITY**
> Output có đủ actionable để PM thực sự dùng được không?

Kiểm tra theo PMBOK 8 standards:
- Có owner/responsible party assign không?
- Có timeline / deadline cụ thể không?
- Có next steps rõ ràng không?
- Output có quá generic không? (dấu hiệu: output giống nhau dù project khác nhau)
- Có đủ detail để thực thi ngay không?
- Theo PMBOK 8 emphasis: output có hướng đến **business value / outcome** không, hay chỉ dừng ở output/deliverable?
- Trong Agile context: có user story / acceptance criteria / DoD rõ ràng không?

Rating: ✅ Actionable | ⚠️ Needs More Detail | ❌ Too Generic / No Owner

---

### Audit Report Format

```
┌─────────────────────────────────────────────────────────────┐
│  🔍 AUDIT REPORT — [Tên skill]                              │
│  Reference: PMBOK 7 (Domains) + PMBOK 8 (Processes)        │
│  Request: [tóm tắt]                                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. METHODOLOGY ACCURACY        [✅/⚠️/❌]                 │
│     PMBOK 7: [nhận xét]                                     │
│     PMBOK 8: [nhận xét]                                     │
│     [Nếu có vấn đề: mô tả cụ thể + điều khoản vi phạm]    │
│                                                             │
│  2. DOMAIN / PROCESS ALIGNMENT  [✅/⚠️/❌]                 │
│     PMBOK 7 Domain: [tên domain] — [nhận xét]              │
│     PMBOK 8 Process Group: [tên group] — [nhận xét]        │
│                                                             │
│  3. DATA FIDELITY               [✅/⚠️/❌]                 │
│     [Nhận xét + flag nếu có assumption chưa verify]        │
│                                                             │
│  4. ACTIONABILITY               [✅/⚠️/❌]                 │
│     [Nhận xét + flag nếu thiếu owner/deadline/next steps]  │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  OVERALL: [🟢 PASS / 🟡 PASS WITH NOTES / 🔴 FAIL]        │
├─────────────────────────────────────────────────────────────┤
│  ISSUES FOUND: [số lượng, 0 nếu pass]                      │
│  [Nếu có]:                                                  │
│  ⚠️ Issue #1: [mô tả] → vi phạm [Tiêu chí X / Nguyên tắc] │
│  ❌ Issue #2: [mô tả] → vi phạm [Tiêu chí X / Process Y]  │
├─────────────────────────────────────────────────────────────┤
│  👉 Bạn có muốn tôi sửa output không?                      │
│     [Y] Sửa ngay  |  [N] Giữ nguyên & tiếp tục             │
└─────────────────────────────────────────────────────────────┘
```

**Nguyên tắc audit:**
- Chỉ sửa output khi user nói rõ: "sửa", "fix", "Y", "vâng sửa đi"
- ⚠️ (amber) không block chain — tiếp tục với note
- ❌ (red) hỏi user muốn tiếp tục hay dừng
- KHÔNG flag kỹ thuật PMBOK 8 mới (AI, Six Hats, Green HRM…) là lỗi

---

### Audit-Only Mode

Khi user paste output đã có và muốn audit:
```
User: "Check kết quả này: [output]"
```
→ Identify skill source nếu có thể  
→ Xác định PMBOK version context (7 hay 8 hay cả hai)  
→ Chạy 4-tiêu-chí audit  
→ Trả về Audit Report đầy đủ

---

## MISSION 3 — CONTINUOUS IMPROVEMENT TRACKING

### Issue Taxonomy

| Code | Loại | Ví dụ |
|---|---|---|
| `M1_METHOD` | Lỗi methodology | Dùng CPM cho pure Agile project |
| `M2_DOMAIN` | Routing sai domain/process | Risk output nhưng route đến planning skill |
| `M3_DATA` | Data fidelity | Hallucinate budget không có trong input |
| `M4_ACTION` | Output không actionable | Không có owner, không có deadline |
| `M5_PMBOK8` | Chưa cập nhật PMBOK 8 | Dùng "Procurement Management" thay "Sourcing Strategy" |
| `TRIGGER` | Skill kích hoạt sai context | pm-assistant xử lý risk analysis |
| `MISSING` | Không có skill cover | Request về Green HRM, Six Thinking Hats |

### Improvement Recommendation Protocol

Khi cùng loại issue xuất hiện 2+ lần ở cùng một skill:

```
📈 SYSTEM IMPROVEMENT RECOMMENDATION
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Skill: [tên skill]
Pattern: [mô tả — ví dụ: M5_PMBOK8 xuất hiện 3 lần]
Vấn đề: [mô tả cụ thể gì đang thiếu/sai]

Khuyến nghị:
→ [Hành động 1 — ví dụ: "Cập nhật terminology sang PMBOK 8"]
→ [Hành động 2 — ví dụ: "Thêm Sourcing Strategy workflow"]
→ [Hành động 3 nếu có]

PMBOK reference: [điều khoản / process / principle cụ thể]
Mức độ: [🔴 High / 🟡 Medium / 🟢 Low]

Muốn tôi giúp cập nhật skill này không?
```

---

## QUICK REFERENCE

```
Nhận request
      │
      ▼
Audit request? ──[Có]──→ Mission 2 Audit-Only Mode
      │[Không]
      ▼
Đếm domains/processes
      │
  1 → Route trực tiếp, không chain
  2 → Chain ngắn + audit
 3+ → Execution Plan → user confirm → chain + audit từng bước
      │
Sau mỗi skill → Audit Report (PMBOK 7 + PMBOK 8)
      │
Pattern 2+ lần? ──[Có]──→ Mission 3 Improvement Recommendation
```

---

## GUARDRAILS

1. **Không override user intent** — User chỉ định skill cụ thể → execute đúng skill đó.
2. **Không tự sửa output** — Audit = báo cáo. Sửa chỉ khi user xác nhận rõ.
3. **Không block vì ⚠️** — Warning không dừng chain. ❌ mới hỏi user.
4. **Dual-reference audit** — Luôn đối soát cả PMBOK 7 (principles + domains) VÀ PMBOK 8 (processes + new techniques). Không chỉ dùng một phiên bản.
5. **PMBOK 8 new techniques ≠ lỗi** — AI, Six Thinking Hats, Green HRM, Sourcing Strategy, AAR là kỹ thuật hợp lệ. Không flag là sai.
6. **Data integrity** — Không tự thêm số liệu không có trong input. Flag rõ khi skill làm điều này.
7. **Transparent về gaps** — Không có skill nào cover → nói thẳng, log `MISSING`, đề xuất build skill mới.
