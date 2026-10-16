---
name: planning-estimation-engine
description: >
  Project planning and estimation skill aligned with PMBOK 8.
  Use when the user needs:
  - WBS, VBS, or scope decomposition into work packages or backlog items
  - Project scheduling, critical path analysis, or milestone planning
  - Effort, duration, or cost estimation (any method)
  - Schedule compression via fast-tracking or crashing
  - Development approach selection (Predictive / Hybrid / Adaptive)
  - Delivery cadence selection (Single / Multiple / Periodic / Continuous)
  - Release planning or iteration planning for agile/hybrid projects
  - Says: "lập kế hoạch", "tạo WBS", "ước tính", "estimate",
    "lịch dự án", "critical path", "sprint plan", "release plan",
    "phân rã công việc", "đường găng", "nén tiến độ",
    "chọn phương pháp", "delivery cadence", "VBS", "hybrid level"

  Five workflows: (A) WBS/VBS/backlog decomposition, (B) estimation,
  (C) scheduling & CPM per PMBOK 8 four-step process, (D) approach
  selection with Suitability Filter + Hybrid Levels, (E) delivery cadence.
---

# Planning & Estimation Engine

PMBOK 8-aligned skill covering five planning workflows:
- **Workflow A** — Scope Decomposition (WBS / VBS / Agile Backlog)
- **Workflow B** — Estimation (method selection + calculation)
- **Workflow C** — Scheduling & Critical Path (PMBOK 8 four-step process)
- **Workflow D** — Development Approach Selection (Suitability Filter + Hybrid Levels)
- **Workflow E** — Delivery Cadence Planning

Workflows can run independently or chained (A → B → C → E is standard sequence).
Inter-skill routing: risks detected during planning → `risk-management`;
approach confirmed → `governance-value-engine` for charter update;
completed plan → `pm-workflow-engine` for reporting.

---

## Step 0 — Context Intake

Extract from input first. Ask only what is missing, **all at once**:

```
To build an accurate plan, I need a few details:

1. Project objective and key deliverable(s)?
2. Current phase? (Initiating / Planning / Execution)
3. Development approach preference? (Predictive / Agile / Hybrid / unsure)
4. Team size and key roles available?
5. Known constraints? (fixed deadline / fixed budget / fixed scope)
6. Any existing WBS, backlog, or schedule to build on?
7. Delivery expectation? (all at end / incremental / continuous / unsure)
```

---

## Workflow A — Scope Decomposition

### A1 — Select Decomposition Mode

| Approach | Decomposition Mode |
|---|---|
| Predictive | WBS — hierarchical, work packages at lowest level |
| Value-driven / need prioritization | VBS — WBS with value % per deliverable |
| Adaptive / Agile | Backlog — Theme → Epic → Feature → Story → Task |
| Hybrid | WBS for stable scope + Backlog for volatile scope |

### A2 — Value Breakdown Structure (VBS) — New in PMBOK 8 §2.2.1

VBS connects project scope → intended value → product scope.
Use when deliverables need value-based prioritization or budget-cut decisions.

```
VBS Output — Project: [Name] | Total Value Target: $[X] or 100%

| # | Deliverable | Value Contribution | % of Total | Mandatory? | WBS Link |
|---|---|---|---|---|---|
| 1 | [deliverable] | $[X] | [X]% | Yes/No | WBS 1.x |
| 2 | [deliverable] | $[X] | [X]% | Yes/No | WBS 2.x |

CP Drag Cost = value lost per day of delay on critical path
→ If crash cost/day < CP drag cost/day → crashing is economically justified
→ If budget cut needed → remove lowest % deliverables first
```

### A3 — Decomposition Rules (all modes)

- Every item starts with a verb (Build, Design, Test, Deploy)
- Every item is estimable — no item > 80 hours effort (2-week rule)
- Every item is assignable — single clear owner possible
- Every work package (except first/last) has ≥1 predecessor AND ≥1 successor
- **100% rule**: children must represent 100% of parent scope
- Flag violations: `⚠️ Too large — decompose further`

### A4 — Output Formats

**WBS:**
```
Project: [Name]
├── 1. [Phase / Deliverable]
│   ├── 1.1 [Work Package]  | Owner: TBD | Est: TBD
│   └── 1.2 [Work Package]  | Owner: TBD | Est: TBD
├── 2. [Phase / Deliverable]
└── 3. Project Management
    ├── 3.1 Reporting & Communication
    └── 3.2 Risk & Change Management
```

**Backlog:**
```
🗂 Epic: [Name]                           Priority: High/Med/Low
  📖 Story: As a [user], I want [goal]   Points: TBD | Owner: TBD
    ✅ Task: [specific action]            Hours: TBD
```

After output: *"Run Workflow B to size each item?"*

---

## Workflow B — Estimation

### B1 — Method Selection

| Situation | Method |
|---|---|
| Similar past project, rough estimate | Analogous (±25–50%) |
| Historical data + formula | Parametric (±10–20%) |
| High uncertainty, need range | Three-Point / PERT (±varies) |
| Agile team, relative sizing | Planning Poker / Story Points / T-shirt |
| No data, expert available | Delphi technique |
| Executive needs confidence level | Monte Carlo → route to `risk-management` |

If method not specified → recommend one with one-sentence rationale, confirm before proceeding.

### B2 — Estimation Output Standard

```
Estimation Summary — [Work Package / Story]

Method: [name + why chosen]
Basis: [data source, assumptions, analogous project if used]

| Item | Optimistic | Most Likely | Pessimistic | PERT [(O+4M+P)/6] | Confidence |
|---|---|---|---|---|---|
| [name] | Xh | Yh | Zh | [calc]h | Low/Med/High |

Assumptions:
- [assumption 1]
- [assumption 2]

Cognitive bias flags (PMBOK 8 §2.3.2.2):
  [ ] Planning fallacy — tendency to underestimate; apply +[X]% buffer
  [ ] Hofstadter's Law — always takes longer than expected
  [ ] Anchoring — use Delphi/Planning Poker to mitigate

Accuracy: ±[range]% — appropriate for [phase] stage
```

### B3 — Accuracy by Phase

| Phase | Accuracy Range |
|---|---|
| Initiation / Concept | -25% to +75% |
| Planning | -10% to +25% |
| Execution (detailed) | -5% to +10% |

Always state accuracy tier. Never present a bare number without range.

---

## Workflow C — Scheduling & Critical Path

### C1 — PMBOK 8 Four-Step Schedule Development (§2.3.2.2)

```
Step 1 → Define Activities
Step 2 → Determine Sequence
Step 3 → Estimate Effort & Duration
Step 4 → Adjust
```

**Step 1 — Define Activities**
```
- Decompose WBS work packages into schedule activities
- Each activity = specific, estimable, assignable action
- Artifacts: Activity list, Activity attributes, Milestone list
```

**Step 2 — Determine Sequence**
```
Logical relationship types:
  FS (Finish-to-Start)  — B can't start until A finishes [most common]
  FF (Finish-to-Finish) — B can't finish until A finishes
  SS (Start-to-Start)   — B can't start until A starts
  SF (Start-to-Finish)  — rare

Leads (negative lag): successor starts BEFORE predecessor finishes
  Example: Landscaping starts 2 weeks before punch list completes → FS -2w

Lags (positive delay): successor delayed after predecessor completes
  Example: Concrete curing 3-day wait → FS +3d

Rules:
  - Every activity (except first/last) must have ≥1 predecessor AND ≥1 successor
  - No closed loops in logic
```

**Step 3 — Estimate Effort & Duration**
```
Duration = Effort / (Resources × Availability%)

Factors (PMBOK 8):
  • Law of diminishing returns: adding resources has limits
  • More people ≠ proportional speed (coordination overhead)
  • Technology advances may shorten estimates
  • Document all assumptions per activity

Effort ≠ Duration:
  Effort   = total labor units (e.g., 40 person-hours)
  Duration = calendar time (e.g., 5 days at 1 FTE)
```

**Step 4 — Adjust**
```
- Check for resource conflicts → apply resource leveling
- Validate team calendars — no cross-project conflicts
- If schedule exceeds deadline → apply compression (see C3)
- Output: Schedule baseline (post-approval)
```

### C2 — Critical Path Method (CPM)

```
Forward Pass:
  ES(first) = 0 (or project start date)
  EF = ES + Duration
  ES(successor) = max(EF of all predecessors)

Backward Pass:
  LF(last) = EF(last) [or required end date]
  LS = LF - Duration
  LF(predecessor) = min(LS of all successors)

Float:
  Total Float = LS - ES  [or LF - EF]
  Free Float  = ES(next) - EF(current)

Critical Path = all activities where Total Float = 0
Near-critical = Float ≤ [5–10% of project duration]
```

**CPM table output:**
```
| Activity | Dur | ES | EF | LS | LF | Float | Critical? |
|---|---|---|---|---|---|---|---|
| Design   | 5d | 0  | 5  | 0  | 5  | 0 | ✅ Yes |
| Docs     | 3d | 0  | 3  | 2  | 5  | 2 | No    |
| Build    | 7d | 5  | 12 | 5  | 12 | 0 | ✅ Yes |

Critical Path: [A] → [C] → [E] | Duration: [X] days
Near-critical paths: [list]
```

### C3 — Schedule Compression

```
Option 1: Fast-Tracking (no direct cost increase — preferred first)
  - Overlap CP activities that are normally sequential
  - Only works for discretionary dependencies, not mandatory
  - ⚠️ Increases rework risk → flag to risk-management

Option 2: Crashing (cost trade-off)
  Crash Cost/Day = (Crash Cost - Normal Cost) / (Normal Dur - Crash Dur)
  - Rank activities by lowest crash cost/day saved
  - Apply cheapest first along critical path only
  - VBS check: if crash cost/day < CP drag cost/day → justified

Option 3: Scope Reduction
  - "If compression isn't enough, scope reduction may be needed
     — requires CCB approval. Use VBS to identify lowest-value
     deliverables for consideration?"
```

### C4 — Adaptive Schedule Monitoring

```
Key metrics for adaptive approaches (PMBOK 8 §2.3.2.3):
  Velocity   = story points completed per sprint
  Burndown   = work remaining vs. time remaining
  Burnup     = work completed + scope added over time
  Cycle time = avg time from task start to done
  Throughput = items completed per sprint

Monitoring focus:
  - Total work delivered vs. estimated
  - Rate of adding new scope vs. completing scope
  - Backlog health: reprioritization frequency
  - Retrospectives: process improvement per iteration
```

---

## Workflow D — Development Approach Selection (PMBOK 8 §3.4 + §4.2–4.3)

### D1 — Suitability Filter (PMBOK 8 §3.4.1)

Assess across three dimensions:

**Deliverable Factors:**
| Factor | → Predictive | → Adaptive |
|---|---|---|
| Requirements clarity | Stable, well-defined | Unknown, volatile |
| Degree of innovation | Low, established tech | High, new domain |
| Ease of change | Hard/costly | Easy to iterate |
| Safety/compliance | Strict upfront planning | Flexible |
| Feedback value | Low | High — discover while building |

**Project Factors:**
| Factor | → Predictive | → Adaptive |
|---|---|---|
| Stakeholder availability | Periodic reviews OK | High engagement needed |
| Schedule constraint | Fixed end date critical | Early delivery valuable |
| Financing | Stable, approved upfront | Uncertain / quarterly |
| Interdependencies | Tight external | Self-contained team |

**Organization Factors:**
| Factor | → Predictive | → Adaptive |
|---|---|---|
| Structure | Functional/hierarchical | Network/flat/matrix |
| Culture | Command & control | Self-managed, innovative |
| Team size | Any | 3–9 ideal |
| Team location | Any | Colocation preferred |

**Scoring:**
```
Majority Predictive → Predictive or Hybrid Level 1
Mixed / Balanced   → Hybrid Level 2
Majority Adaptive  → Adaptive or Hybrid Level 3
```

### D2 — Hybrid Levels (PMBOK 8 §4.2.3 — Disciplined Agile®)

```
Level 1 — Predictive Dominant
  Predictive primary + agile elements for specific pain points
  Example: Construction project with agile design sprints

Level 2 — True Hybrid
  Both contribute significantly to project success
  Example: Predictive infrastructure + agile UX development (parallel)

Level 3 — Adaptive Dominant
  Adaptive primary + predictive for compliance/release milestones
  Example: Agile product with predictive regulatory gate
```

**Common patterns (PMBOK 8):**
```
Pattern 1: [Adaptive sprints] → [Predictive deployment/rollout]
Pattern 2: [Adaptive stream A] + [Predictive stream B] (simultaneous)
Pattern 3: [Predictive] → [Predictive] → [Adaptive component]
Pattern 4: [Adaptive] → [Adaptive] → [Predictive gate/compliance]
```

### D3 — Approach Output

```
Development Approach Recommendation

Suitability filter:
  Deliverable factors:   [Predictive / Mixed / Adaptive]
  Project factors:       [Predictive / Mixed / Adaptive]
  Organization factors:  [Predictive / Mixed / Adaptive]

Recommended: [Predictive / Hybrid Level 1/2/3 / Adaptive]
Pattern (if hybrid): [Pattern 1/2/3/4]

Rationale:
  → [Key factor 1]
  → [Key factor 2]

Suggested Focus Areas (PMBOK 8):
  Initiating → Planning → Executing + M&C → Closing

Tailoring notes: [what to add/remove for this project]

⚠️ Approach risks:
  → [Risk 1] — suggest risk-management skill
  → [Risk 2]

Next: confirm in charter (governance-value-engine)
```

---

## Workflow E — Delivery Cadence Planning (PMBOK 8 §4.4)

### E1 — Four Types

```
SINGLE DELIVERY
  All outcomes at project end
  When: Scope cannot be partial (process reengineering, bridge)
  Risk: Value delayed until end; late issue discovery

MULTIPLE DELIVERIES
  Components at different times (sequential or parallel)
  When: Independent deliverables, phased rollout
  Risk: Integration complexity, dependency management

PERIODIC DELIVERIES
  Fixed schedule: every 2 weeks, monthly, quarterly
  When: Adaptive projects, software sprints
  Risk: Scope pressure at each delivery window

CONTINUOUS DELIVERY
  Value to production on ongoing basis; CI/CD pipelines
  When: High automation, SaaS products
  Risk: Regression risk; requires automation investment
```

### E2 — Cadence Selection

| Condition | Cadence |
|---|---|
| Interdependent deliverables, can't be partial | Single |
| Multiple independent deliverables | Multiple |
| Team uses sprints | Periodic (match sprint length) |
| CI/CD in place | Continuous |
| Regulatory approval per phase | Multiple (milestone-gated) |
| Budget uncertainty / funding reviews needed | Periodic (quarterly) |
| Stakeholders need early value realization | Periodic or Multiple |

### E3 — Cadence Output

```
Delivery Cadence Plan — [Project Name]

Approach: [Predictive / Hybrid / Adaptive]
Cadence: [Single / Multiple / Periodic / Continuous]

| # | Delivery / Release | Content | Target Date | Value Realized |
|---|---|---|---|---|
| 1 | [name] | [scope] | [date] | $[X] or [description] |

Early value opportunities: [what can be delivered sooner?]

Cadence risks:
  → [Risk 1] | Mitigation: [action]
  → [Risk 2] | Mitigation: [action]
```

---

## Inter-Skill Routing

Surface **after** primary output — never interrupt:

| Condition | Route To |
|---|---|
| High estimate uncertainty | `risk-management` — Monte Carlo, contingency sizing |
| Fast-tracking or crashing applied | `risk-management` — compression risk assessment |
| Planning complete, need stakeholder report | `pm-workflow-engine` — progress report |
| WBS complete, need Jira issues | `pm-workflow-engine` — task extraction |
| Approach selected, need charter update | `governance-value-engine` |
| VBS shows low-value deliverables at risk | `quality-delivery-control` — scope validation |

---

## General Rules

- **Never give a bare estimate** — always include method, assumptions, accuracy range
- **Never skip dependency mapping** — a schedule without dependencies is a list
- **Flag scope violations** — items >80h must decompose further
- **Compression = risk** — always pair with risk flag
- **VBS before cutting scope** — check value contribution before removing deliverables
- **Four-step schedule** — always: Define → Sequence → Estimate → Adjust
- **Cognitive bias on every estimate** — flag planning fallacy and anchoring
- **Cadence = stakeholder contract** — changes require governance approval
- **Focus Areas not Process Groups** — PMBOK 8 language:
  Initiating / Planning / Executing / Monitoring & Controlling / Closing
- **Output language** — match user's language (Vietnamese in → Vietnamese out)
- **One context intake** — all questions at once in Step 0

---

## Trigger Phrases

**English:** "create WBS", "build VBS", "value breakdown structure", "break down scope",
"estimate effort", "how long will this take", "build a schedule", "critical path",
"compress the schedule", "fast track", "crash the schedule",
"should we use agile or waterfall", "hybrid approach", "hybrid level",
"delivery cadence", "release plan", "sprint plan", "iteration planning",
"define activities", "sequence activities", "suitability filter"

**Vietnamese:** "tạo WBS", "VBS", "phân rã công việc", "ước tính dự án",
"ước tính effort", "lập lịch dự án", "đường găng", "nén tiến độ",
"chọn phương pháp", "lập kế hoạch", "kế hoạch phát hành",
"kế hoạch sprint", "delivery cadence", "hybrid level", "tần suất bàn giao"
