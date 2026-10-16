---
name: quality-delivery-control
description: >
  Quality management and delivery control skill aligned with PMBOK 8.
  Use when the user needs:
  - Quality planning, assurance, or control (Manage Quality Assurance)
  - Definition of Done (DoD) creation or review
  - Scope & change control (Monitor & Control Scope / CCB process)
  - Cost of Quality (CoQ) analysis or trade-off decisions
  - Defect tracking, root cause analysis, or rework reduction
  - Acceptance criteria definition or sign-off planning (Validate Scope)
  - Phase gate review preparation
  - Says: "quality plan", "acceptance criteria", "definition of done",
    "scope creep", "change control", "defect", "rework", "QA", "QC",
    "kế hoạch chất lượng", "tiêu chí nghiệm thu", "kiểm soát phạm vi",
    "lỗi", "làm lại", "phase gate", "bàn giao", "nghiệm thu"

  Workflows: (A) quality planning, (B) scope & change control,
  (C) delivery readiness & acceptance, (D) defect & rework management.
---

# Quality & Delivery Control Skill (PMBOK 8)

## Purpose

Ensure that what gets delivered actually meets the standards it was built to —
by building quality **in** from the start, not inspecting it **in** at the end.

> **PMBOK 8 Anchor (§3.5 — Embed Quality Into Processes and Deliverables):**
> Quality is the degree to which inherent characteristics of a deliverable or
> process meet or exceed the project's target objectives. Quality covers BOTH
> the product (does it meet requirements?) AND the process (are we building
> it correctly?). Prevention always costs less than correction.
>
> **PMBOK 8 Integration Note:** Quality is integrated into the **Scope
> Performance Domain** (§2.2), not a standalone domain. Monitor & Control
> Scope includes quality measurement. Validate Scope combines process checking
> + formal acceptance.

Four workflows:
- **Workflow A** — Quality Planning (Manage Quality Assurance — process focus)
- **Workflow B** — Scope & Change Control (Monitor & Control Scope)
- **Workflow C** — Delivery Readiness & Acceptance (Validate Scope)
- **Workflow D** — Defect & Rework Management

---

## Step 0 — Context Intake

Extract from input first. Ask only for what is missing, **all at once**:

```
To build the right quality and delivery controls, I need:

1. Project type — software / construction / service / product / mixed?
2. Development approach — Predictive / Agile / Hybrid?
3. Phase — Planning / Execution / Closing?
4. Key deliverables — what are we building or delivering?
5. Who accepts the deliverables — internal sponsor / external client / regulatory body?
6. Known quality risks — any areas where defects or rework have occurred before?
7. Existing quality standards — ISO, industry-specific, organizational QMS?
8. Sustainability requirements — any ESG, environmental, or social impact targets?
```

---

## Workflow A — Quality Planning (Manage Quality Assurance)

### When to use
User is in planning phase and needs to establish how quality will be defined,
measured, assured, and controlled throughout the project.

### PMBOK 8 Distinction (§2.1.6.5)

> **Quality Assurance (QA)** = using project processes effectively.
> Process-focused. Assures stakeholders the project's final results will meet
> their needs. Related concepts: regulations, compliance, audits.
>
> **Quality Control (QC)** = creating deliverables that meet defined specs.
> Deliverable-focused. Ensures outputs achieve required attributes.
> Related concepts: product design, testing, defects.
>
> In predictive projects: QA is formal, systematic, documented.
> In adaptive/agile projects: QA can be performed formally or informally
> based on context — retrospectives, sprint reviews, and team agreements
> may serve as QA mechanisms.

### A1 — Quality Standards Identification

| Level | Examples |
|---|---|
| External / Regulatory | ISO 9001, ISO 27001, FDA 21 CFR, GDPR, building codes, safety standards |
| Industry / Client | Client QMS, SLAs, contractual acceptance criteria |
| Organizational | Internal coding standards, design guidelines, testing protocols |
| Sustainability (PMBOK 8 §3.7) | ESG KPIs, CO₂ emission limits, social impact standards |

For each standard: What does it require? Who verifies? What evidence is needed?

### A2 — Quality Metrics (PMBOK 8 §2.2.5)

Define metrics for both **product** and **process**. PMBOK 8 Check Results
formulas to include:

**Scope & Quality metrics (PMBOK 8 Table 2-6):**
```
Scope Definition Accuracy (%) = (Planned Scope Items Correctly Delivered /
                                  Total Planned Scope Items) × 100

Scope Creep (%) = (Unplanned Deliverables / Total Deliverables) × 100

Requirements Stability (%) = (Unchanged Requirements /
                               Total Requirements) × 100
```

**Product Quality Metrics:**

| Metric | Definition | Measurement | Threshold |
|---|---|---|---|
| Defect density | Defects per unit of work | Defect log | < [X] per sprint |
| Defect escape rate | Defects found by client vs. found internally | Defect log | < [X]% |
| First-time pass rate | % deliverables accepted without rework on first submission | Review records | > [X]% |
| Test coverage | % of requirements covered by test cases | Test plan | > [X]% |
| Performance benchmark | Load time / throughput vs. specification | Testing tools | Meets spec ±[X]% |

**Process Quality Metrics:**

| Metric | Definition | Target |
|---|---|---|
| Review completion rate | % of planned QA reviews conducted | 100% |
| Rework ratio | Effort on rework vs. total effort | < [X]% |
| Defect resolution time | Avg time from logged to resolved | < [X] days |
| Audit findings | Non-conformances per audit | 0 critical / < [X] minor |

### A3 — Cost of Quality (CoQ) Framework (PMBOK 8 §5 Tools)

```
Total CoQ = Prevention Costs + Appraisal Costs + Failure Costs

Prevention Costs (invest here — cheapest):
  - Quality planning and standards development
  - Training and capability building
  - Process design and documentation
  - Supplier qualification

Appraisal Costs (necessary verification):
  - Testing and inspection
  - Peer reviews and walkthroughs
  - Quality audits
  - Acceptance testing

Internal Failure Costs (caught before delivery — bad but recoverable):
  - Rework and correction
  - Scrap and waste
  - Defect analysis time
  - Re-testing after fix

External Failure Costs (caught after delivery — most expensive):
  - Client complaints and remediation
  - Warranty / SLA penalties
  - Recalls or rollbacks
  - Reputation damage
  - Regulatory penalties
```

**Boehm's Curve — cost of fixing defects by phase:**
```
Requirements:  1×
Design:        5×
Build:         10×
Testing:       20×
Production:    100×+
```

→ Every hour in requirements review can save 100 hours of post-delivery remediation.
Always present this to justify quality investment.

**CoQ Analysis Output:**
```
Cost of Quality Analysis — [Project Name]

| Category | Activity | Estimated Cost | Notes |
|---|---|---|---|
| Prevention | Requirements review sessions | $[X] | [N] sessions × [N] people |
| Prevention | QA training | $[X] | |
| Appraisal | Test plan execution | $[X] | |
| Appraisal | UAT facilitation | $[X] | |
| Internal Failure | Estimated rework (at current defect rate) | $[X] | [X]% rework ratio |
| External Failure | Projected penalty if defects escape | $[X] | Per contract SLA |

Total CoQ: $[X]
Prevention + Appraisal: $[X] ([X]% of total)
Failure costs: $[X] ([X]% of total)

Recommendation: Shifting [X]% of failure cost budget to prevention is
expected to reduce total CoQ by [X]% over the project.
```

### A4 — Sustainability in Quality Plan (PMBOK 8 §3.7 + §2.2.5)

PMBOK 8 mandates sustainability be integrated into scope and quality.
**WBS or backlog must include sustainability activities:**

```
Sustainability Quality Checklist (add to Quality Management Plan):

Environmental:
  [ ] CO₂ / carbon footprint tracked per project phase
  [ ] Resource consumption (energy, water, materials) monitored
  [ ] Waste reduction targets defined and measured
  [ ] Green procurement criteria applied to vendor selection

Social:
  [ ] Community impact assessment completed (if applicable)
  [ ] Equity and inclusion standards applied to team practices
  [ ] Health and safety standards documented

Economic (long-term):
  [ ] Life-cycle cost considered, not just project cost
  [ ] Maintenance and support costs factored into acceptance criteria

ESG KPIs (if org has ESG policy):
  [ ] [Specific KPI 1] — target: [value] — measurement: [method]
  [ ] [Specific KPI 2] — target: [value] — measurement: [method]
```

### A5 — Quality Management Plan Output (PMBOK 8 aligned)

```
# Quality Management Plan — [Project Name]
Version: [X] | Date: [date]

## 1. Quality Objectives
- Deliverable quality: [metric + target]
- Process quality: [metric + target]
- Client satisfaction: [measurement + target]

## 2. Applicable Standards
| Standard | Requirement | Verification Method | Owner |
|---|---|---|---|
| [standard] | [requirement] | [how verified] | [role] |

## 3. QA vs QC Responsibilities (PMBOK 8 §2.1.6.5)
| Role | QA Responsibility (process) | QC Responsibility (deliverable) |
|---|---|---|
| PM | Ensure processes followed | Review deliverable status |
| QA Lead | Conduct audits, process checks | [if separate role] |
| Team Members | Follow defined processes | Self-review before submission |
| Client/Sponsor | Governance oversight | Final acceptance sign-off |

## 4. Quality Metrics
[Tables from A2 — product + process metrics]

## 5. Cost of Quality Summary
[Table from A3]

## 6. QA Activities Schedule (Manage Quality Assurance)
| Activity | Type | Frequency | Owner | Output |
|---|---|---|---|---|
| Process audit | QA | Monthly | QA Lead | Audit report |
| Sprint retrospective | QA (adaptive) | Per sprint | PM/SM | Improvement actions |
| Requirements review | Prevention | Before design | PM + team | Sign-off record |
| Peer code/design review | Prevention | Per feature | Team | Review checklist |
| Defect trend review | QC | Weekly | PM | Defect trend report |

## 7. Sustainability Integration
[Checklist from A4]

## 8. Adaptive Approach Tailoring
[If Agile/Hybrid: describe how QA is embedded in sprints — informal QA
through retrospectives, sprint reviews, Definition of Done]
```

---

## Workflow B — Scope & Change Control (Monitor & Control Scope)

### When to use
User needs to control scope baseline, manage change requests, prevent
scope creep, or process a change through the CCB.

### PMBOK 8 Process: Monitor & Control Scope (§2.2.2.5)

> Primary objective: ensure the product/service/result is **relevant and
> delivering value** to stakeholders, while fulfilling requirements.
> Scope and quality are monitored together in this process.

### B1 — Scope Baseline Protection

A scope baseline must exist before scope can be controlled:

```
Scope Baseline = Project Scope Statement + WBS + WBS Dictionary
  (Predictive: formal approval required)
  (Adaptive: scope baseline = prioritized backlog + iteration commitment)

Cannot control what has no baseline.
If baseline is missing → stop and establish it first.
```

### B2 — Scope Health Metrics (PMBOK 8 Table 2-6)

```
Scope Definition Accuracy (%) =
  (Planned Scope Items Correctly Delivered / Total Planned Scope Items) × 100
  Target: > [X]%

Scope Creep (%) =
  (Unplanned Deliverables / Total Deliverables) × 100
  Threshold: > [X]% triggers CCB review

Requirements Stability (%) =
  (Unchanged Requirements / Total Requirements) × 100
  Target: > [X]% (lower in adaptive — expected; monitor trend)

Rate of new scope added (adaptive):
  New backlog items added per sprint vs. completed
  Alert if additions > completions for 2+ consecutive sprints
```

### B3 — Change Control Process (CCB)

```
CHANGE REQUEST FLOW

Any stakeholder → submits Change Request (CR)
                          ↓
              PM records in Change Log
                          ↓
              Impact Analysis (PM + team):
                - Scope impact
                - Schedule impact (→ planning-estimation-engine)
                - Cost/Finance impact (→ governance-value-engine)
                - Risk impact (→ risk-management)
                - Quality impact
                          ↓
              ┌─────────────────────────┐
              │ Within PM authority?    │
              │ (per charter matrix)    │
              └─────────────────────────┘
                  Yes ↓        No ↓
              PM decides   Submit to CCB
                          ↓
              CCB Decision:
                ✅ Approved → update baseline + schedule + budget
                ⏸ Deferred → log reason + revisit date
                ❌ Rejected → notify requester + log reason
                🔍 More Info → request additional analysis
```

**Change Request Form:**
```
# Change Request — CR-[###]
Date: [date] | Requested by: [name/role] | Priority: High/Med/Low

## Description of Change
[What is being requested?]

## Justification / Business Need
[Why is this change needed?]

## Impact Analysis
| Domain | Impact | Detail |
|---|---|---|
| Scope | [increase/decrease/neutral] | [description] |
| Schedule | [+/- X days/weeks] | [activities affected] |
| Cost | [+/- $X] | [budget line affected] |
| Quality | [risk increase/neutral] | [quality risk] |
| Risk | [new risk created?] | [risk description] |

## Recommended Decision
[ ] Approve  [ ] Defer  [ ] Reject  [ ] Needs more information

## CCB Decision
Decision: [        ]  | Date: [        ]  | Authorized by: [        ]
Reason (if rejected/deferred): [        ]
```

### B4 — Adaptive Scope Control (Backlog-Based)

In adaptive projects, scope is controlled via backlog management, not CCB:

```
Adaptive Scope Control:
  - New feature/story requests → added to product backlog (not a "change request")
  - Priority assigned by Product Owner
  - Lower-priority items effectively "deferred"
  - Removing an item from backlog = "rejected" (no formal CCB needed)
  - Sprint scope locked at sprint planning — no changes mid-sprint

Alert signals:
  🟡 New items added > items completed (2+ sprints) → backlog health review
  🔴 Scope added without deprioritizing something else → capacity risk
  🔴 Mid-sprint scope changes occurring → team agreement violated
```

---

## Workflow C — Delivery Readiness & Acceptance (Validate Scope)

### When to use
User needs to verify a deliverable is ready for acceptance, run a phase gate
review, or obtain formal sign-off from sponsor/client.

### PMBOK 8 Process: Validate Scope (§2.2.2.6)

> Two objectives:
> 1. Check processes used to achieve quality standards (QA check)
> 2. Formalize acceptance of completed deliverables (stakeholder sign-off)
>
> Key benefit: scope is validated through an **objective process** to assure
> value and quality in what is delivered.

### C1 — Definition of Done (DoD) Templates

**DoD must be agreed before work starts — not defined at delivery.**

**Software feature DoD:**
```
Definition of Done — Software Feature

Code & Development:
  [ ] Code written and self-reviewed by developer
  [ ] Code reviewed by peer (at least 1 reviewer)
  [ ] All automated unit tests written and passing
  [ ] No new critical or major linting errors introduced
  [ ] Feature branch merged to main/develop

Testing:
  [ ] Functional testing completed — all acceptance criteria tested
  [ ] Integration testing passed — no regression in existing features
  [ ] Performance within spec (load time / throughput targets met)
  [ ] Security scan completed — no high-severity findings

Documentation:
  [ ] User-facing documentation updated (if applicable)
  [ ] API documentation updated (if applicable)
  [ ] Release notes entry written

Acceptance:
  [ ] Product Owner / client reviewed and accepted the feature
  [ ] All acceptance criteria explicitly marked as PASSED
  [ ] No open Critical or Major defects

Sustainability (PMBOK 8):
  [ ] Feature complies with data privacy/security requirements (GDPR etc.)
  [ ] No unnecessary resource consumption introduced (energy, storage)
```

**Construction milestone DoD:**
```
Definition of Done — Construction Milestone

Physical completion:
  [ ] All scope items in milestone completed per drawings
  [ ] Quality inspection completed by [internal QC / third-party inspector]
  [ ] Inspection report with zero Critical non-conformances
  [ ] Photographic evidence collected

Documentation:
  [ ] As-built drawings updated
  [ ] Material test certificates filed
  [ ] Compliance certificates obtained (if required)

Acceptance:
  [ ] Client representative walked the site and signed inspection form
  [ ] Snag list issued (if applicable) with resolution timeline agreed
  [ ] Payment milestone authorized by client (per contract)

Sustainability (PMBOK 8):
  [ ] Waste disposal records completed
  [ ] Environmental impact compliance confirmed
  [ ] CO₂ / material consumption logged for project ESG reporting
```

**Service / process delivery DoD:**
```
Definition of Done — Service Deliverable

Service readiness:
  [ ] Process documented and reviewed
  [ ] Team trained and sign-off obtained
  [ ] System / tools configured and tested
  [ ] SLA parameters tested and confirmed

Acceptance:
  [ ] Business owner reviewed and accepted
  [ ] Go-live checklist completed
  [ ] Rollback plan documented and tested

Sustainability (PMBOK 8):
  [ ] Service design considers long-term operational sustainability
  [ ] Environmental and social impact assessed
```

### C2 — Acceptance Criteria Framework

Acceptance criteria must be:
- **Specific** — no ambiguity ("fast" is not acceptable; ">95% requests <2s" is)
- **Measurable** — can be objectively verified Pass/Fail
- **Agreed** — signed off by both team and client before work starts
- **Value-linked** — tied to the outcome the deliverable enables

**Acceptance Criteria Format (Gherkin for software / plain for others):**
```
Software:
  Given [precondition/context]
  When  [user action / system event]
  Then  [expected outcome — specific and measurable]

Example:
  Given a registered user on the login page
  When they submit valid credentials
  Then they are redirected to dashboard within 2 seconds

Non-software:
  [Deliverable] is accepted when:
    - [Criterion 1 — measurable]
    - [Criterion 2 — measurable]
    - [Sustainability criterion — if applicable]
```

### C3 — Phase Gate Review Checklist

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔲 PHASE GATE — [Phase Name] → [Next Phase]
Date: [date] | Reviewer: [role] | Decision Authority: [role]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SCOPE & QUALITY (Monitor & Control Scope + Validate Scope)
  [ ] All planned deliverables for this phase completed
  [ ] Acceptance criteria met for each deliverable (evidence attached)
  [ ] DoD satisfied — no open waivers
  [ ] Change log reviewed — all CRs resolved or deferred with reason
  [ ] Scope Definition Accuracy ≥ [X]%
  [ ] Scope Creep ≤ [X]% of total deliverables

QUALITY ASSURANCE (Manage Quality Assurance)
  [ ] Planned QA activities completed (audits, reviews, inspections)
  [ ] No open Critical audit findings
  [ ] Quality metrics within threshold
  [ ] Lessons learned captured

RISK (route to risk-management)
  [ ] Risk register reviewed and updated
  [ ] No unmitigated High risks proceeding to next phase
  [ ] Overall project risk assessed

SCHEDULE & FINANCE
  [ ] Schedule variance within threshold (SV: [value])
  [ ] Cost variance within threshold (CV: [value])
  [ ] Budget for next phase confirmed and available

STAKEHOLDERS
  [ ] Key stakeholders informed of gate outcome
  [ ] Sponsor/client sign-off obtained (or scheduled)

SUSTAINABILITY (PMBOK 8)
  [ ] Sustainability KPIs tracked and documented for this phase
  [ ] Environmental/social commitments met for phase activities

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Gate Decision:
  ✅ PROCEED   — all criteria met; next phase authorized
  ⚠️ CONDITIONAL — proceed with exceptions: [list exceptions + owners + dates]
  ⏸ HOLD      — [specific blocker must be resolved first]
  ❌ STOP      — [critical issue; re-plan required]

Authorized by: [role + name] | Date: [date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### C4 — Formal Acceptance Record

```
# Delivery Acceptance Record
Project: [name] | Deliverable: [name] | Version: [X]
Date: [date]

Acceptance criteria verification:
| # | Criterion | Test Method | Result | Pass/Fail |
|---|---|---|---|---|
| 1 | [criterion] | [how tested] | [actual result] | ✅ Pass / ❌ Fail |

Sustainability criteria:
| # | Criterion | Evidence | Pass/Fail |
|---|---|---|---|
| 1 | [ESG/sustainability criterion] | [document reference] | ✅ / ❌ |

Open items (conditional acceptance only):
| # | Item | Owner | Resolution Date |
|---|---|---|---|

Decision:
  [ ] Accepted unconditionally
  [ ] Accepted conditionally — open items must be resolved by [date]
  [ ] Rejected — [reason; next steps]

Signed:
  Client/Sponsor: [name] _________________ Date: _______
  PM:             [name] _________________ Date: _______
```

---

## Workflow D — Defect & Rework Management

### When to use
User is dealing with defects found in testing or production, high rework
volume, recurring defect patterns, or needs a root cause analysis.

### D1 — Defect Classification

**Severity** (impact on functionality):

| Level | Definition | Response Time |
|---|---|---|
| 🔴 Critical | System crash, data loss, security breach, core function unusable | Fix within [24h / current sprint] |
| 🟠 Major | Core function degraded, significant workaround required | Fix within [48h / next sprint] |
| 🟡 Minor | Non-core function affected, minor workaround available | Fix within [current release / next release] |
| 🟢 Trivial | Cosmetic, spelling, UI misalignment | Backlog — fix when convenient |

**Priority** (urgency — separate from severity):

| Priority | Meaning |
|---|---|
| P1 | Fix now — stops delivery or customer activity |
| P2 | Fix this sprint / week |
| P3 | Fix next sprint / release |
| P4 | Fix when capacity allows |

⚠️ Severity ≠ Priority. A Critical defect in a rarely-used feature may be P2.
A Minor defect on the main login page may be P1. Always assess both independently.

### D2 — Root Cause Analysis (5 Whys)

For every Critical and recurring defect — address root cause, not symptom:

```
Defect: [description]

Why did this defect occur?
→ [Answer 1]

Why did [Answer 1] happen?
→ [Answer 2]

Why did [Answer 2] happen?
→ [Answer 3]

Why did [Answer 3] happen?
→ [Answer 4]

Why did [Answer 4] happen?
→ Root cause: [Answer 5]

Corrective action (addresses root cause):
[Specific action — not "be more careful"]

Preventive action (prevents recurrence):
[Process change / checklist addition / training / tooling]
```

**Fishbone categories for systemic defects:**
```
         ├── People: skill gaps, unclear ownership, fatigue
         ├── Process: missing step, unclear requirement, no review gate
         ├── Technology: tool limitation, environment issue
         ├── Requirements: ambiguous, incomplete, conflicting
         ├── Communication: missed handoff, assumption not stated
         └── Environment: test env ≠ prod, data mismatch
```

### D3 — Rework Reduction Strategy

High rework = systemic problem, not a team problem. Diagnose pattern first:

| Rework Pattern | Root Cause | Corrective Action |
|---|---|---|
| Defects found late in testing | Requirements not validated early | Add requirements review gate before build |
| Same defect type recurring | No lessons learned applied | Add defect pattern to DoD checklist |
| Rework after client review | Acceptance criteria not agreed upfront | Define and sign off AC before sprint starts |
| Rework after integration | Components tested in isolation only | Add integration test gate |
| Rework due to changed requirements | Scope creep entering without control | Enforce Workflow B change control |
| Developer rework loops | Code review too late | Shift code review earlier — after design |

### D4 — Defect Trend Analysis

```
Defect Trend Report — [Project Name] | Period: [date range]

| Week | New | Resolved | Escaped | Open (EOW) | Rework % |
|---|---|---|---|---|---|
| W1 | [N] | [N] | [N] | [N] | [X]% |
| W2 | [N] | [N] | [N] | [N] | [X]% |

Trends:
  New defects:  ↑ Increasing / → Stable / ↓ Decreasing
  Escape rate:  ↑ Increasing / → Stable / ↓ Decreasing  [TARGET: <[X]%]
  Open defects: ↑ Increasing / → Stable / ↓ Decreasing  [TARGET: <[X] Critical]

Alert thresholds:
  🔴 Critical open > [N] → immediate escalation to PM + Sponsor
  🟡 Escape rate > [X]% → QA process review required
  🟡 Rework > [X]% of sprint capacity → sprint health check

Actions this period:
  [ ] [Action 1] — addresses [pattern]
  [ ] [Action 2] — addresses [pattern]
```

### D5 — Defect Log

```
# Defect Log — [Project Name] | Updated: [date]

| ID | Date | Found By | Description | Component | Severity | Priority |
Status | Assigned | Root Cause | Fixed | Verified? |
|---|---|---|---|---|---|---|---|---|---|---|---|
| DEF-001 | [date] | [QA/Client] | [desc] | [feature] | 🔴 Crit | P1 |
Open | TBD | TBD | — | No |
```

---

## Quality Control Gates — Summary Reference

| Gate | When | What to Check | Decision |
|---|---|---|---|
| Requirements Gate | Before design starts | Requirements complete, unambiguous, agreed, sustainability criteria included | Proceed / Rework |
| Design Gate | Before build starts | Design meets requirements, reviewed, risks addressed | Proceed / Rework |
| Build Gate | Before integration | Unit tests pass, code review done, DoD met | Integrate / Fix first |
| Integration Gate | Before system test | Integration tests pass | Proceed / Fix |
| System Test Gate | Before UAT | No open Critical/Major defects | Proceed / Fix first |
| UAT Gate | Before go-live | Business scenarios pass, sustainability verified, client sign-off | Go-live / Conditional / Hold |
| Phase Gate | Between phases | Phase DoD complete, risks cleared, sponsor approved | Next phase / Hold |
| Closure Gate | Before project close | All deliverables accepted, lessons learned captured, sustainability KPIs documented | Close / Outstanding items |

---

## Inter-Skill Routing

Surface **after** primary output — never interrupt:

| Condition | Route To |
|---|---|
| Defects linked to requirements ambiguity | `risk-management` — log as risk, analyze impact |
| Change requests accumulating beyond threshold | `pm-workflow-engine` — change impact report for steering committee |
| Quality metrics 🔴 — project health at risk | `pm-workflow-engine` for status report + `risk-management` for escalation |
| Phase gate approaching — need stakeholder sign-off plan | `stakeholder-intelligence` — confirm sign-off owners |
| Approved CRs require plan rebaseline | `planning-estimation-engine` — rebaseline schedule and budget |
| Sustainability KPIs off track | `risk-management` — log as ESG risk + escalate |

---

## General Rules

- **Prevention > Inspection** — always present CoQ to justify upfront quality investment
- **PMBOK 8 language** — use "Manage Quality Assurance" (not just QA plan),
  "Monitor & Control Scope", "Validate Scope" — align with process names
- **Quality is in Scope domain** — per PMBOK 8, quality integrated into Scope
  Performance Domain; Monitor & Control Scope includes quality measurement
- **Never waive a DoD criterion** — if a criterion changes, update DoD formally
- **Severity ≠ Priority** — always assess both independently
- **Root cause, not symptom** — every Critical/Major defect gets 5 Whys
- **Scope change = CCB** (predictive) or backlog management (adaptive) — no exceptions
- **Baseline before control** — scope cannot be controlled without an approved baseline
- **Sustainability is not optional** — PMBOK 8 §3.7 + §2.2.5: WBS/backlog must
  include sustainability activities; phase gates must verify ESG commitments
- **Adaptive tailoring** — QA in agile can be informal (retrospectives, sprint reviews,
  DoD) but must still exist; document how QA is performed per approach
- **Output language** — match user's language (Vietnamese in → Vietnamese out)
- **One context intake** — all questions at once in Step 0

---

## Trigger Phrases

**English:** "create quality management plan", "define acceptance criteria",
"write definition of done", "too much rework", "prevent scope creep",
"process change request", "CCB", "are we ready to deliver",
"phase gate review", "defect root cause analysis", "cost of quality",
"UAT planning", "validate scope", "quality assurance audit",
"sustainability in scope", "ESG quality criteria"

**Vietnamese:** "lập kế hoạch chất lượng", "định nghĩa tiêu chí nghiệm thu",
"viết definition of done", "rework quá nhiều", "ngăn scope creep",
"xử lý change request", "CCB", "chuẩn bị bàn giao deliverable",
"checklist phase gate review", "phân tích nguyên nhân lỗi",
"chi phí chất lượng", "lên kế hoạch UAT", "kiểm soát phạm vi",
"nghiệm thu bàn giao", "chất lượng bền vững", "tiêu chí ESG"
