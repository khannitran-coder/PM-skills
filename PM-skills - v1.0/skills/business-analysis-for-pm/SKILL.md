---
name: business-analysis-for-pm
description: >
  BA (Business Analysis) skill scoped for a PM owner — requirements
  elicitation, BRD/FRD, Agile user story & backlog writing (INVEST,
  Gherkin acceptance criteria), and Requirements Traceability Matrix
  (RTM) with UAT support.
  Use when: elicit/structure requirements; write/review BRD/FRD/PRD;
  write user stories, split epics, groom backlog; define acceptance
  criteria (Given/When/Then) or check INVEST; build RTM (requirements →
  stories → tests → UAT); prepare/run UAT.
  Says: "viết BRD/FRD", "user story", "backlog", "acceptance criteria",
  "INVEST", "Gherkin", "RTM", "ma trận truy vết", "UAT", "thu thập/phân
  tích yêu cầu", "tách story".
  Three workflows: (A) Elicitation & BRD/FRD, (B) User story & backlog
  (Agile-first), (C) RTM + UAT. Use for any part of this pipeline — PM-
  appropriate depth (no BPMN/data modeling), routes to planning-
  estimation-engine, quality-delivery-control, stakeholder-intelligence,
  risk-management, governance-value-engine, pm-workflow-engine.
---

# Business Analysis for PM

## Purpose

Give a **Project Manager acting as BA owner** decision-quality requirements
artifacts, without requiring BA-specialist depth:
- Elicit and structure requirements so nothing critical is missed
- Turn requirements into a backlog the delivery team can actually build from
- Keep an unbroken thread from *business need* → *story* → *test* → *sign-off*

> **Scope boundary (read this first):** This skill produces PM-level BA
> artifacts: BRD/FRD (lean), user stories, acceptance criteria, RTM, UAT
> support. It does **not** replace a dedicated BA for deep process
> re-engineering, formal BPMN 2.0 modeling, or relational data modeling —
> flag it plainly if the user's ask clearly needs that level and suggest
> looping in a BA/architect.

Three workflows:
- **Workflow A** — Requirements Elicitation & BRD/FRD
- **Workflow B** — User Story & Backlog Writing (Agile-first)
- **Workflow C** — Requirements Traceability Matrix (RTM) + UAT Support

---

## Step 0 — Context Intake

Extract from input first (existing charter, notes, meeting transcript, Jira
board). Ask only for what's missing, **all at once**:

```
Để làm BA cho dự án này, mình cần:

1. Mục tiêu/bài toán nghiệp vụ — vấn đề gì đang cần giải quyết?
2. Phương pháp triển khai — Agile/Scrum, Waterfall, hay Hybrid?
3. Đối tượng dùng kết quả — đội dev/QA nội bộ, vendor ngoài, hay khách hàng?
4. Nguồn thông tin sẵn có — có charter, notes họp, JD nghiệp vụ nào chưa?
5. Mức độ chi tiết cần — nháp nhanh để trao đổi, hay tài liệu chính thức để ký?
```

If the user already gave enough (e.g. pasted meeting notes + said "Agile"),
don't re-ask — extract, confirm the key parameters in one line, and proceed.

---

## Workflow A — Requirements Elicitation & BRD/FRD

### When to use
User needs to gather requirements from raw input (notes, interviews,
transcripts) and turn them into a structured requirements document.

### A1 — Elicitation Techniques (pick based on input type)

| Input available | Technique |
|---|---|
| Raw meeting notes / transcript | Extract explicit asks + read between lines for implied needs |
| Access to stakeholders | Structured interview (open questions first, closed to confirm) |
| Existing process, no docs | Observation / walkthrough — ask "show me how you do it today" |
| Vague or conflicting asks | 5 Whys — trace each ask back to the business problem it solves |
| Multiple stakeholder groups | Workshop framing — capture points of agreement AND conflict explicitly |

Always distinguish a **stated want** from the **underlying business need** —
write both down. A request like "thêm nút xuất Excel" might really mean
"sponsor cần báo cáo tuần cho ban giám đốc" — document the real need so the
solution isn't over/under-built.

### A2 — Requirements Categorization (BABOK-aligned, PM-simplified)

| Category | Definition | Example |
|---|---|---|
| **Business** | Why the project exists — goals, objectives, KPIs | "Giảm 30% thời gian xử lý đơn hàng" |
| **Stakeholder** | What a stakeholder group needs from the solution | "Kế toán cần xuất báo cáo VAT theo quý" |
| **Solution — Functional** | What the system must *do* | "Hệ thống phải gửi email xác nhận trong 5 phút" |
| **Solution — Non-functional** | How well it must do it (performance, security, usability) | "Trang phải load < 2s với 500 người dùng đồng thời" |
| **Transition** | What's needed to go live (data migration, training, cutover) | "Migrate dữ liệu khách hàng từ hệ thống cũ trước go-live" |

### A3 — Prioritization (MoSCoW)

| Tier | Meaning | Rule of thumb |
|---|---|---|
| **Must have** | Solution fails without it | Legal/contractual, core business need |
| **Should have** | Important, not fatal if delayed | Workaround exists but painful |
| **Could have** | Nice to have | Cut first under time/budget pressure |
| **Won't have (this time)** | Explicitly out of scope | State it — prevents scope creep arguments later |

### A4 — BRD/FRD Output (lean format)

Default to the **lean** version unless the user explicitly wants a full
formal BRD/FRD for sign-off (client contract, regulated environment):

```
# Business Requirements Document — [Project Name]
Version: [x] | Date: [date] | Owner (PM): [name]

## 1. Business Context
- Problem statement:
- Business objective(s) / success metric:
- In scope / Out of scope:

## 2. Stakeholder Requirements
| # | Stakeholder | Requirement | Priority (MoSCoW) |
|---|---|---|---|

## 3. Functional Requirements
| # | Requirement | Priority | Linked Business Need |
|---|---|---|---|

## 4. Non-Functional Requirements
| # | Requirement (performance/security/usability/...) | Target/Threshold |
|---|---|---|

## 5. Assumptions & Constraints
## 6. Transition / Go-live Requirements
## 7. Open Questions
```

For a **full formal BRD/FRD** (Waterfall/contractual), expand with: revision
history, approval sign-off block, glossary, and a dedicated FRD section
mapping each functional requirement to a system component. Ask before
producing the long version — it's a different deliverable, not just "more
detail."

After output: *"BRD/FRD nháp xong — chuyển sang Workflow B để viết user
story/backlog từ tài liệu này?"*

---

## Workflow B — User Story & Backlog Writing (Agile-first)

### When to use
User needs user stories, epics, or a groomed backlog — either from scratch
or derived from Workflow A's requirements.

> **PM-level framing:** every story must trace back to a requirement or
> business need (see Workflow C). A story with no traceable "why" is a
> red flag, not just a formatting gap.

### B1 — Story Format

```
As a [role/persona], I want [goal/capability], so that [business benefit].
```

Keep the persona specific ("kế toán viên AP", not "user"). If the "so
that" is missing or generic ("so that it works better"), that's a signal
the underlying business need wasn't captured — go back to Workflow A.

### B2 — INVEST Quality Check

Run every story through this before it enters the backlog:

| Letter | Check | Fails if... |
|---|---|---|
| **I**ndependent | Can be built/shipped without waiting on another story | Hard-blocked by an unscheduled story |
| **N**egotiable | Describes outcome, not implementation | Story dictates exact UI/tech instead of the need |
| **V**aluable | Delivers value to a user or the business on its own | It's a technical task disguised as a story |
| **E**stimable | Team can size it with reasonable confidence | Too vague, or hides unknowns |
| **S**mall | Fits in a sprint, ideally a few days | Spans multiple sprints — split it (see B4) |
| **T**estable | Has clear pass/fail acceptance criteria | "Should be user-friendly" (unverifiable) |

### B3 — Acceptance Criteria (Gherkin, Given/When/Then)

```
Scenario: [short name of the behavior]
Given [starting context/state]
When [action taken]
Then [expected outcome]
```

Write at least: one **happy path**, one **edge case**, one **error/negative
case** per story. A story without a negative-case AC is under-specified.

Example:
```
Story: As a kế toán viên, I want to xuất báo cáo công nợ theo khoảng ngày,
so that tôi có thể đối soát cuối tháng mà không cần lọc thủ công.

Scenario: Xuất báo cáo thành công
Given tôi đã chọn khoảng ngày hợp lệ có dữ liệu
When tôi bấm "Xuất Excel"
Then hệ thống tải file .xlsx đúng dữ liệu trong khoảng ngày đã chọn

Scenario: Khoảng ngày không có dữ liệu
Given tôi chọn khoảng ngày không có giao dịch nào
When tôi bấm "Xuất Excel"
Then hệ thống hiển thị thông báo "Không có dữ liệu" thay vì file rỗng

Scenario: Ngày bắt đầu sau ngày kết thúc
Given tôi nhập ngày bắt đầu > ngày kết thúc
When tôi bấm "Xuất Excel"
Then hệ thống chặn và báo lỗi validate, không cho xuất
```

### B4 — Story Splitting (when INVEST "Small" fails)

| Technique | How |
|---|---|
| Workflow steps | Split by sequential steps of the process (step 1 = story 1, step 2 = story 2...) |
| Business rules | One story per rule variant (e.g. domestic vs international shipping) |
| CRUD | Create / Read / Update / Delete as separate stories |
| Data variations | Split by data type/source (e.g. import from Excel vs manual entry) |
| Happy path vs edge cases | Ship happy path first as its own story, edge cases as follow-ups |

Never split by technical layer alone (e.g. "backend story" + "frontend
story") — each split must still be independently valuable (INVEST "I"
and "V").

### B5 — Definition of Ready (entry gate for this skill's output)

A story is "Ready" for sprint planning when it has: role/goal/benefit,
priority, at least 3 acceptance criteria (happy/edge/error), and no open
blocking question. (Definition of *Done* — the exit gate — is owned by
**quality-delivery-control**; don't duplicate it here, just flag when a
story needs one.)

### B6 — Backlog Output

```
# Product Backlog — [Project/Epic Name]

## Epic: [Epic name]
Business need: [link to BRD section / business objective]

| # | Story | Priority | Story Points (if known) | Status |
|---|---|---|---|---|
| 1 | As a... I want... so that... | Must | — | Ready |

### Story 1 — [short title]
[Full story + acceptance criteria per B3]
```

After output: *"Backlog xong — chạy Workflow C để lập RTM và chuẩn bị
UAT test case cho các story Must-have?"*

---

## Workflow C — Requirements Traceability Matrix (RTM) + UAT Support

### When to use
User needs to prove/verify every requirement is covered by a story and a
test, and/or needs UAT test cases and a sign-off structure.

> **Why this matters for a PM:** RTM is your defense when a stakeholder
> says "we asked for X and didn't get it" — and it's how you catch orphan
> requirements (no story) and orphan stories (no traceable requirement)
> before go-live, not after.

### C1 — RTM Structure

```
# Requirements Traceability Matrix — [Project Name]

| Req ID | Business Requirement | Story ID(s) | Test Case ID(s) | UAT Status | Owner |
|---|---|---|---|---|---|
| BR-01 | [from BRD Workflow A] | US-03, US-04 | TC-05 | Not Started | [name] |
```

**Integrity rules:**
- Every requirement row must have at least one story ID — no story means
  no plan to deliver it. Flag orphans explicitly.
- Every story should trace back to a requirement ID — a story with no
  requirement link is scope that was never approved. Flag it.
- UAT Status values: `Not Started / In Progress / Passed / Failed / Blocked / Deferred`

### C2 — UAT Test Case Template

```
Test Case ID: TC-[#]
Linked Requirement / Story: [Req ID / Story ID]
Precondition: [what must be true before testing]
Steps:
1. ...
2. ...
Expected Result: [derived directly from the story's acceptance criteria]
Actual Result: [filled during execution]
Status: Pass / Fail
Tester: [name] | Date: [date]
```

Generate UAT test cases directly from each story's Gherkin acceptance
criteria (B3) — happy path, edge case, and error case each become a test
case. Don't invent new scenarios UAT wasn't scoped for.

### C3 — UAT Entry/Exit Criteria

| | Criteria |
|---|---|
| **Entry** | All Must-have stories at "Ready", test environment stable, test data prepared, test cases reviewed |
| **Exit** | All Must-have test cases Passed, all Failed items triaged (fixed & retested or formally deferred with sponsor sign-off) |

### C4 — UAT Sign-off Output

```
# UAT Sign-off — [Project Name]
Date: [date]

Summary: [X/Y test cases passed, Z deferred with reason]

| Req ID | Status | Deferred reason (if any) | Approved by |
|---|---|---|---|

Sign-off:
[ ] Business Owner — Name / Date
[ ] Project Manager — Name / Date
```

After output: *"RTM + UAT plan xong — cần đẩy sang risk-management nếu có
requirement bị Failed/Deferred có ảnh hưởng go-live không?"*

---

## Inter-Skill Routing

Surface at end of workflow — never interrupt primary output:

| Condition | Routing Action |
|---|---|
| BRD/FRD done, need WBS/estimate | *"Requirements đã rõ — chạy **planning-estimation-engine** để làm WBS/estimate?"* |
| Backlog done, need to log stories as Jira issues | *"Backlog sẵn sàng — chạy **pm-workflow-engine** để tạo Jira issue?"* |
| Story needs a Definition of Done or acceptance sign-off process | *"Cần DoD chuẩn — dùng **quality-delivery-control** để định nghĩa?"* |
| Elicitation reveals a new/unmapped stakeholder | *"Phát hiện stakeholder chưa có trong register — chạy **stakeholder-intelligence** Workflow A?"* |
| UAT reveals a Failed/Deferred item with delivery impact | *"Item Failed/Deferred có thể ảnh hưởng go-live — log vào **risk-management**?"* |
| Business requirement lacks a clear ROI/business case link | *"Chưa thấy liên kết business case — tham chiếu **governance-value-engine**?"* |

---

## General Rules

- **PM-level, not BA-specialist-level** — no formal BPMN 2.0, no relational
  data modeling. If the ask needs that depth, say so and suggest a BA/architect.
- **Never write a story without acceptance criteria** — a story without AC
  isn't ready, it's a placeholder.
- **Every requirement must trace to a story, every story to a requirement**
  — flag orphans in both directions (Workflow C).
- **Stated want ≠ business need** — always capture both during elicitation.
- **One context intake** — ask all missing questions at once in Step 0,
  never drip-feed.
- **Output language matches the user's** (Vietnamese in → Vietnamese out).
- **Default to lean formats** (lean BRD, Agile stories) unless the user
  signals a formal/contractual/Waterfall deliverable is needed.
- **Don't duplicate other skills' territory** — DoD belongs to
  quality-delivery-control, business case to governance-value-engine, risk
  logging to risk-management. Route to them instead of reproducing.

---

## Reference Files

| File | When to Read |
|---|---|
| `references/elicitation-techniques.md` | Before Workflow A when input is thin — deeper technique guidance (interview scripts, workshop facilitation) |
| `references/gherkin-patterns.md` | Before Workflow B when acceptance criteria involve complex states/permissions |
| `references/rtm-examples.md` | Before Workflow C for worked examples across Agile and Waterfall RTMs |

---

## Trigger Phrases

**English:**
- "Write a BRD for this project"
- "Help me gather requirements from this transcript"
- "Write user stories for this feature"
- "Check if this story is INVEST-compliant"
- "Write acceptance criteria for this story"
- "Build a requirements traceability matrix"
- "Prepare UAT test cases"
- "Split this story, it's too big"

**Vietnamese:**
- "Viết BRD cho dự án này"
- "Thu thập yêu cầu từ file ghi chú họp này"
- "Viết user story cho tính năng này"
- "Kiểm tra story này có đạt INVEST không"
- "Viết acceptance criteria cho story này"
- "Lập ma trận truy vết yêu cầu"
- "Chuẩn bị test case UAT"
- "Story này to quá, giúp tách nhỏ"
