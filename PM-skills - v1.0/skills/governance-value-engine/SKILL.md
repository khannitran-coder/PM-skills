---
name: governance-value-engine
description: >
  Project governance and value management skill aligned with PMBOK 7/8.
  Use when the user needs:
  - Business case creation or validation (ROI, NPV, cost-benefit analysis)
  - Project charter drafting or review
  - Benefits realization planning or tracking
  - Project authorization, sponsor alignment, or governance setup
  - Tailoring governance to project size and complexity
  - Says: "business case", "project charter", "charter", "ROI", "NPV",
    "lập business case", "viết charter", "hiến chương dự án",
    "benefits realization", "lợi ích dự án", "authorize project",
    "phê duyệt dự án", "governance", "project sponsor", "value"

  Three workflows: (A) business case development, (B) project charter
  drafting, (C) benefits realization planning. Always use this skill —
  contains PMBOK 7/8 value-focus principles, financial analysis formulas,
  governance tailoring rules, and routing to planning-estimation-engine.
---

# Governance & Value Engine

PMBOK 7/8-aligned skill for project initiation, governance, and value management.

> **Core principle (PMBOK 7):** Projects exist to deliver value — not just
> outputs. Every governance artifact must trace back to intended outcomes
> and benefits, not just deliverables.

Three workflows:
- **Workflow A** — Business Case Development & Validation
- **Workflow B** — Project Charter Drafting
- **Workflow C** — Benefits Realization Planning

Inter-skill routing: governance outputs feed `planning-estimation-engine`
for WBS and scheduling; risks surface to `risk-management`;
stakeholder sections route to `stakeholder-intelligence`.

---

## Step 0 — Context Intake

Extract from input first. Ask only for what is missing, **all at once**:

```
To build governance artifacts at the right level, I need:

1. Project objective — what outcome are we trying to achieve?
2. Trigger — why now? (strategic initiative / problem / opportunity / mandate)
3. Requesting organization — internal project or client-facing?
4. Project size estimate — budget range and duration?
5. Key stakeholders — sponsor, key decision makers?
6. Constraints — fixed deadline / fixed budget / regulatory requirements?
7. What already exists? (idea only / draft business case / approved charter)
```

If user pastes an existing document → extract context silently,
confirm key parameters once, then proceed.

---

## Workflow A — Business Case Development

**Read `references/business-case.md` before executing this workflow.**

### When to use
User needs to justify a project investment, validate whether a project
should proceed, or update an existing business case.

### A1 — Business Case Components (PMBOK 7 Aligned)

A complete business case must address all six components:

| Component | Question It Answers | Minimum Viable Content |
|---|---|---|
| Business Need | Why must we act? | Problem/opportunity statement, current state pain |
| Situation Assessment | What's the full picture? | Gap analysis, root cause, options considered |
| Recommended Option | What should we do? | Preferred solution with rationale |
| Financial Analysis | Is it worth it? | ROI, NPV, payback period, cost-benefit |
| Risk Summary | What could go wrong? | Top 3–5 risks, mitigation approach |
| Recommendation | What's the ask? | Decision needed, next steps, authorization request |

### A2 — Financial Analysis

**Read `references/business-case.md` → Financial Formulas section.**

Always compute at minimum:

```
ROI = (Net Benefit / Total Cost) × 100%
Net Benefit = Total Benefits - Total Costs

NPV = Σ [Cash Flow(t) / (1 + r)^t] - Initial Investment
      where r = discount rate, t = year

Payback Period = Initial Investment / Annual Net Benefit

Cost-Benefit Ratio = Total Benefits / Total Costs
(ratio > 1.0 = project generates more value than it costs)
```

Present financial analysis in a table — never as prose numbers:

```
Financial Summary

Assumptions: discount rate [r]%, analysis period [N] years

| Metric | Value | Interpretation |
|---|---|---|
| Total Investment | $[X] | One-time + recurring costs |
| Total Benefits (NPV) | $[X] | Over [N] years |
| Net NPV | $[X] | Positive = proceed / Negative = reconsider |
| ROI | [X]% | Industry benchmark: [Y]% |
| Payback Period | [X] months | Acceptable if < [threshold] |
| Cost-Benefit Ratio | [X]:1 | >1.0 = favorable |

Sensitivity: If benefits reduced by 20% → NPV = $[X] → [still viable / marginal / not viable]
```

### A3 — Options Analysis

For each alternative considered (minimum 3: do nothing, minimal, recommended):

```
| Option | Description | Cost | Benefit | Risk | Recommendation |
|---|---|---|---|---|---|
| 0. Do Nothing | Maintain status quo | $0 | $0 | Opportunity cost: $[X] | ❌ Not recommended |
| 1. Minimal | [description] | $[X] | $[X] | Low | ⚠️ Fallback |
| 2. Recommended | [description] | $[X] | $[X] | Medium | ✅ Recommended |
```

### A4 — Business Case Output Structure

```
# Business Case — [Project Name]
Version: [X] | Date: [date] | Status: Draft / Under Review / Approved
Prepared by: [name/role] | Sponsor: [name]

## Executive Summary
[3–4 sentences: problem, recommended solution, key financial metric, ask]

## 1. Business Need
[Problem/opportunity statement — specific, quantified where possible]
Current state: [what is happening now and why it's a problem]
Desired state: [what success looks like]
Cost of inaction: [what happens if we don't act — quantified if possible]

## 2. Situation Assessment
[Root cause analysis, gap analysis, what has already been tried]

## 3. Options Considered
[Table from A3 above]

## 4. Recommended Option
[Description, rationale for selection over alternatives]

## 5. Financial Analysis
[Table from A2 above]
[Sensitivity analysis]

## 6. Risk Summary
[Top risks — route to risk-management skill for full register]
| Risk | Probability | Impact | Mitigation |
|---|---|---|---|

## 7. Recommendation & Authorization Request
Decision needed: [Approve / Reject / Defer / Request more information]
Requested by: [date]
Next step if approved: [Project charter → planning → execution]
```

### A5 — Decision Gate (mandatory, always run after A4)

After producing the business case, surface a structured decision prompt:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔲 DECISION GATE — Business Case Review
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Financial signal:   [🟢 Strong / 🟡 Marginal / 🔴 Weak]
  NPV:              $[X]  ([positive/negative])
  ROI:              [X]%  (benchmark: [Y]%)
  Payback:          [X] months
  Downside (–20%):  $[X]  → [still viable / breaks even / negative]

Risk signal:        [🟢 Low / 🟡 Medium / 🔴 High]
  Top risk:         [risk name] — [mitigation status]

Recommended decision:
  ✅ APPROVE   — NPV positive, risks manageable, proceed to charter
  ⚠️ DEFER     — [specific condition that must be resolved first]
  ❌ REJECT    — [specific reason: NPV negative / risk unacceptable / strategic misalign]
  🔍 MORE INFO — Missing: [what data would change the recommendation]

If approved → next step: **Workflow B (Project Charter)**
Decision needed by: [date or "sponsor to confirm"]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Rules for Decision Gate:
- Always show **all four options** — never pre-select for the sponsor
- If NPV < 0 but strategic value is high → show DEFER with condition
  *"Revisit if cost reduced by $[X] or benefits confirmed by [date]"*
- Never skip this gate — even for small projects (simplify, don't omit)

---

## Workflow B — Project Charter Drafting

**Read `references/charter.md` before executing this workflow.**

### When to use
User needs to formally authorize a project, define PM authority,
or establish the official project mandate.

### B1 — Charter vs Business Case

| Document | Purpose | Written By | Approved By |
|---|---|---|---|
| Business Case | Justify the investment | PM / BA / Sponsor | Executive / Portfolio |
| Project Charter | Authorize the project | PM (with sponsor) | Sponsor / Governance body |

Charter assumes business case is approved (or being approved simultaneously).
If no business case exists → ask: *"Should I draft a business case first,
or proceed with charter only?"*

### B2 — Charter Components

| # | Section | Content | Mandatory? |
|---|---|---|---|
| 1 | Project Purpose & Business Case | Problem/opportunity + expected value (TBD if unclear) + link to business need | ✅ |
| 2 | Objectives | SMART outcomes the project must achieve | ✅ |
| 3 | Success Criteria | Output success (deliverable accepted) + Outcome success (business KPI) | ✅ |
| 4 | High-level Scope | Included deliverables + Explicitly excluded items | ✅ |
| 5 | Key Deliverables | Tangible outputs the project will produce | ✅ |
| 6 | Milestones (High-level Timeline) | Key dates — not a detailed schedule | ✅ |
| 7 | Constraints | Fixed deadline, budget, resources, technology, regulatory | ✅ |
| 8 | Assumptions | What we believe to be true without proof + impact if false | ✅ |
| 9 | Key Stakeholders | Sponsor, PM, key influencers + engagement approach | ✅ |
| 10 | Project Governance | PM authority + escalation path + CCB setup | ✅ |
| 11 | High-level Budget | Order-of-magnitude estimate (±50% acceptable) + contingency | ✅ |
| 12 | Risk Summary | Top 3 known risks at initiation + initial response | ✅ |
| 13 | Project Approval Criteria | Conditions that must be met for sponsor to formally approve deliverables | ✅ |
| 14 | Termination Criteria | Conditions under which the project should be cancelled | ⚡ Recommended |
| 15 | Authorization | Sponsor signature + PM acknowledgment + date | ✅ |

> **Note — Section 3 vs Section 2:**
> Objectives = WHAT we achieve (outcome statement)
> Success Criteria = HOW we know we achieved it (measurement method)
> These are related but distinct — never collapse into one.

### B3 — SMART Objectives Writing Rule

Every objective must be:
- **S**pecific — names the exact outcome
- **M**easurable — includes a metric or KPI
- **A**chievable — realistic given constraints
- **R**elevant — links to business need
- **T**ime-bound — has a deadline

```
❌ Bad: "Improve customer satisfaction"
✅ Good: "Increase NPS score from 32 to 50 by Q3 2025,
          measured via quarterly customer survey"

❌ Bad: "Reduce costs"
✅ Good: "Reduce invoice processing cost by 30% (from $12 to $8.40/invoice)
          within 6 months of system go-live"
```

### B4 — PM Authority Matrix

Always include — ambiguous authority is the #1 cause of PM-sponsor conflict:

```
PM decides independently (no approval needed):
- Day-to-day work assignments within approved budget
- Minor schedule adjustments ≤ [X] days that don't affect milestones
- Vendor selection for purchases ≤ $[X]

PM requires sponsor approval:
- Scope changes (any addition or removal)
- Budget changes > [X]% or $[X]
- Schedule changes affecting key milestones
- Changes to project team composition (key roles)

Escalate to steering committee:
- Budget overrun > [X]%
- Strategic direction change
- Project cancellation recommendation
```

### B5 — Charter Output Structure

**Read `references/charter.md` → Charter Output Template section**
for the full 15-section charter template with all fields and writing guidance.

Key sections to always populate completely before delivering:
- Section 3 (Success Criteria): must include BOTH output and outcome rows
- Section 10 (Governance): PM authority must be explicit per decision type
- Section 13 (Approval Criteria): must be specific and verifiable — not subjective
- Section 14 (Termination Criteria): include even briefly — protects org from sunk cost

### B6 — Execution Hook

**Read `references/charter.md` → Execution Hook section** for the
post-charter action checklist and next-skill routing prompt.

---

## Workflow C — Benefits Realization Planning

**Read `references/benefits-realization.md` before executing this workflow.**

### When to use
User wants to track whether project benefits are actually being realized
after delivery — or needs to define how benefits will be measured.

### C1 — Why This Matters (PMBOK 7)

PMBOK 7 explicitly shifts focus from **outputs** (what we deliver) to
**outcomes** (what changes) and **benefits** (value gained).

```
Output → Outcome → Benefit → Strategic Value

Example:
Output:   New CRM system deployed
Outcome:  Sales team spends 40% less time on admin
Benefit:  $350K/year saved in labor costs
Value:    Company can scale sales without proportional headcount increase
```

### C2 — Benefits Register

For each benefit identified:

```
| # | Benefit | Type | Baseline | Target | Measurement | Timeline | Owner |
|---|---|---|---|---|---|---|---|
| 1 | [description] | Financial/Non-financial | [current state] | [goal] | [KPI/method] | [when realized] | [role] |
```

Benefit types:
- **Financial:** Cost reduction, revenue increase, efficiency gain (quantifiable $)
- **Operational:** Process improvement, quality increase, risk reduction
- **Strategic:** Market position, capability, compliance, customer satisfaction
- **Social/Environmental:** ESG-related outcomes

### C3 — Benefits Realization Timeline

```
Project Life Cycle          Benefits Realization Period
─────────────────────────────────────────────────────────
Initiation Planning Execution Closure │ Month 1-3 │ Month 4-12 │ Year 2+ │
                                      │ Early wins│ Core value │ Full ROI │
```

Map each benefit to when it will be measurable — many benefits appear
**after** project closure, not during.

### C4 — Benefits Realization Plan Output

```
# Benefits Realization Plan — [Project Name]
Linked to Business Case version: [X] | Charter version: [X]

## Benefits Summary
Total financial benefit (NPV): $[X] over [N] years
Primary non-financial benefit: [description]

## Benefits Register
[Table from C2]

## Measurement & Governance
| Benefit | Who Measures | When | Reporting Vehicle |
|---|---|---|---|
| [benefit] | [role] | [date/frequency] | [report name] |

## Benefits Realization Milestones
| Milestone | Expected Benefit | Measurement Date | Responsible |
|---|---|---|---|
| 3 months post go-live | [early indicator] | [date] | [owner] |
| 12 months post go-live | [core benefit] | [date] | [owner] |

## Transition to Operations
[What must happen for benefits to be realized — training, process change,
org change, etc. If significant → suggest stakeholder-intelligence skill]

## Review Cadence
Benefits reviewed: [monthly / quarterly] by [role/committee]
Escalation if benefits not tracking: [process]
```

### C5 — Benefits Control Loop (always run after C4)

This converts the benefits plan from a static document into an active
management loop. Apply at every scheduled review:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔄 BENEFITS CONTROL LOOP — Review Cycle
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Review date: [date] | Period: [reporting period]

Benefits Scorecard:
| # | Benefit | Target | Actual | Variance | Status | Trend |
|---|---|---|---|---|---|---|
| 1 | [name] | [value] | [value] | [+/-%] | 🟢/🟡/🔴 | ↑↓→ |

Diagnosis:
  🟢 On track  → [benefit name]: no action needed, document evidence
  🟡 At risk   → [benefit name]: root cause = [cause], intervention = [action]
  🔴 Off track → [benefit name]: escalate to [role] by [date]

Variance root causes detected:
  [ ] Adoption gap — staff not using new system/process as intended
  [ ] Baseline was wrong — re-measure and rebaseline
  [ ] External factor — market/org change outside project control
  [ ] Benefit realization delayed — timeline shift, not permanent loss
  [ ] Benefit was over-estimated — revise target with sponsor sign-off

Loop output — choose one:
  → No change needed: document review, set next review date
  → Rebaseline: update benefit target with sponsor approval + document reason
  → Intervention: [specific action + owner + deadline]
  → Escalate: [to whom + what decision is needed + by when]

Next review: [date] | Owner: [role]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Control loop rules:
- Run this loop at **every** scheduled review — not just when things go wrong
- 🟢 benefits still need to be documented — evidence for future business cases
- Never rebaseline silently — always require sponsor acknowledgment
- If 2+ consecutive reviews show 🔴 → trigger escalation automatically

---

## Governance Tailoring by Project Size

Apply before any workflow — adjust artifact depth accordingly:

| Project Size | Charter Depth | Business Case | Benefits Plan |
|---|---|---|---|
| **Small** (<3 months, <$50K, 1–3 people) | 1 page, key sections only | Lean canvas or email summary | Integrated into charter |
| **Medium** (3–12 months, $50K–$500K) | Full charter, all sections | Standard business case | Separate document, quarterly review |
| **Large** (>12 months, >$500K, multiple teams) | Full charter + governance framework | Full business case with sensitivity | Formal program, steering committee |
| **Regulatory / Compliance** | Full charter + audit trail | Mandatory, board-level | Formal, auditable evidence required |

---

## Inter-Skill Routing

Surface at end of workflow — never interrupt primary output:

| Condition | Routing Action |
|---|---|
| Charter approved, need detailed plan | *"Charter complete — run **planning-estimation-engine** for WBS, schedule, and estimates?"* |
| Stakeholder section needs depth | *"Stakeholder section drafted — run **stakeholder-intelligence** for power/interest mapping and engagement strategy?"* |
| Risk section needs expansion | *"Top risks identified — run **risk-management** for full RAID log and response planning?"* |
| Business case financial analysis needs simulation | *"For Monte Carlo sensitivity analysis on financial projections, route to **risk-management** skill?"* |
| Benefits realization involves org change | *"Significant change management needed — consider **team-performance-coach** skill for change adoption planning?"* |

---

## General Rules

- **Value first** — every artifact must trace deliverables → outcomes → benefits → strategic value
- **Never produce a charter without SMART objectives** — vague objectives create scope disputes later
- **Always include explicit exclusions** — what's OUT of scope is as important as what's in
- **PM Authority must be explicit** — never leave authority ambiguous
- **Size the artifact to the project** — a $20K project does not need a 40-page business case
- **Benefits are not deliverables** — distinguish clearly: system deployed ≠ benefit realized
- **Output language** — match user's language
- **One context intake** — all questions at once in Step 0, never drip-feed

---

## Reference Files

| File | When to Read |
|---|---|
| `references/business-case.md` | Before Workflow A — financial formulas, options analysis templates |
| `references/charter.md` | Before Workflow B — charter writing rules, authority matrix examples |
| `references/benefits-realization.md` | Before Workflow C — benefits types, measurement frameworks |

---

## Trigger Phrases

**English:** "write a business case", "draft a project charter", "create a charter",
"calculate ROI", "NPV analysis", "is this project worth doing",
"benefits realization plan", "authorize this project",
"what's the value of this project", "governance setup"

**Vietnamese:** "viết business case", "tạo hiến chương dự án", "draft charter",
"tính ROI", "phân tích NPV", "dự án này có đáng làm không",
"kế hoạch hiện thực hóa lợi ích", "phê duyệt dự án",
"giá trị dự án là gì", "thiết lập governance"
