---
name: risk-management
description: >
  Advanced Project Risk Management skill aligned with PMBOK 8.
  Use this skill when the user needs:
  - Risk identification, analysis, or response planning
  - Risk Register, RAID Log, or risk review
  - Extraction of risks from documents, meeting notes, emails, or vague inputs
  - Decision support on risk prioritization and mitigation
  - Full risk management lifecycle including monitoring and control
  - Overall project risk assessment (separate from individual risks)
  - Risk resilience planning
  - Says things like "phân tích rủi ro", "risk review", "ROAM", "RAID",
    "risk register", "rủi ro dự án", "analyze risks", "build risk register",
    "overall risk", "resilience", "risk classification"

  This skill produces decision-ready outputs, not just risk lists.
  Always use this skill for any risk-related request — it contains PMBOK 8
  risk classification (4-quadrant Known/Unknown), overall project risk,
  Escalate strategy for opportunities, resilience planning, and
  PMP-standard frameworks for senior-quality output.
---

# Risk Management Skill (Senior PM — PMBOK 8)

## Purpose

Provide **decision-quality risk insights** by:
- Classifying uncertainty using PMBOK 8 four-quadrant model
- Identifying individual risks (threats AND opportunities) AND overall project risk
- Structuring risks using PMP standard (Cause → Event → Impact)
- Enabling prioritization & action with clear response strategies
- Building project resilience for unknown-unknowns
- Supporting ongoing monitoring and control

> PMBOK 8 Anchor: Risk management is **continuous, value-driven, and
> uncertainty-aware** — not a one-time listing activity. Risk and resilience
> are managed together: known risks get response plans; unknown risks get
> reserves and resilience mechanisms.

---

## Step 0 — Determine Context & Mode

### 0.1 Input Mode

| Situation | Action |
|---|---|
| User provides text / doc / meeting notes / email | Extract risks directly → Step 1 |
| User provides existing risk list | Validate, enrich & enhance → Step 1 |
| No input at all | Enter Interview Mode → Step 0.2 |

### 0.2 Project Context (ask all at once if missing)

```
To build a decision-quality risk register, I need a few details:

1. What is the project objective / outcome?
2. Current phase? (Initiating / Planning / Executing / M&C)
3. Timeline & critical milestones?
4. Key stakeholders?
5. What is NOT acceptable to fail? (scope / time / cost / reputation)
6. Development approach? (Predictive / Hybrid / Adaptive)
   [Adaptive projects → risk monitored per sprint, not per phase]
```

### 0.3 Risk Appetite & Threshold (PMBOK 8 §2.7.1)

```
Risk appetite = degree of uncertainty the org is willing to accept for a reward

Options:
  Low tolerance    — avoid uncertainty; prefer stability over speed
  Balanced         — moderate risk for moderate gain [default if unknown]
  High tolerance   — speed and innovation over certainty

Risk threshold = measurable boundary:
  Example: "Any risk with CPI impact > 10% or delay > 2 weeks
  must be escalated to sponsor"
```

→ If unknown: assume **Balanced** and flag as assumption in RAID log.
→ Document threshold in Risk Management Plan.

---

## Step 1 — Classify & Identify Uncertainty (PMBOK 8 §2.7.1)

### 1.1 — PMBOK 8 Risk Classification (Four-Quadrant Model)

**Apply this classification BEFORE building the risk register:**

```
┌─────────────────────────────────────────────────────┐
│              RISK CLASSIFICATION MATRIX             │
│                                                     │
│           KNOWN           │        UNKNOWN          │
│  ─────────────────────────────────────────────────  │
│  KNOWN  │ Known-Known     │ Known-Unknown           │
│         │ Facts/Requirements│ Classic risk          │
│         │ → Managed as    │ → Probability &        │
│         │   project scope │   impact assessable    │
│         │   NOT a risk    │   → Risk Register      │
│  ─────────────────────────────────────────────────  │
│  UNKNOWN│ Unknown-Known   │ Unknown-Unknown         │
│         │ Hidden fact     │ Emergent risk           │
│         │ Knowledge exists│ Cannot be foreseen     │
│         │ elsewhere but   │ → Management Reserve   │
│         │ not with team   │ → Resilience planning  │
│         │ → Research it   │                        │
└─────────────────────────────────────────────────────┘
```

**Classification rules:**
- **Known-Known** → scope or requirements — NOT a risk; handle in planning
- **Known-Unknown** → classic project risk → enter in Risk Register with P×I scoring
- **Unknown-Known** → team lacks knowledge that exists elsewhere → research action first
- **Unknown-Unknown** → cannot be identified upfront → address via Management Reserve +
  Resilience Plan (Step 5B)

### 1.2 — Extract RAID Items (4 types — NEVER mix)

| Type | Definition | Handling |
|---|---|---|
| **Risk** | Uncertain future event (Known-Unknown) | → Risk Register |
| **Issue** | Already happening NOW | → Issue Log (immediate action) |
| **Assumption** | Unverified belief taken as true | → Assumption Log (validate ASAP) |
| **Dependency** | External reliance on team / system / vendor | → Dependency Tracking |

⚠️ **Critical rule:** Issues are NOT risks. An active issue requires immediate
response — do not put it in a risk register with probability scoring.

### 1.3 — Risk Statement Format (mandatory for every risk)

```
Due to [CAUSE], there is a risk that [EVENT], leading to [IMPACT].
```

Example:
> Due to dependency on vendor API delivery (no SLA signed), there is a risk
> that integration is delayed, leading to a 3-week timeline slippage and
> potential client penalty of $50K.

### 1.4 — Identify BOTH Threats AND Opportunities

- 🔴 **Threats** — negative risks to avoid or mitigate
- 🟢 **Opportunities** — positive risks to exploit or enhance

Proactively scan for upside: early delivery, cost savings, team capability
gains, technology advantage, market opportunity.

### 1.5 — Detect Implicit Risks

Scan input for hidden risk signals:
- Vague language: "we assume", "should be fine", "hopefully"
- Missing ownership on key tasks
- External dependencies with no SLA
- Over-optimistic timelines (planning fallacy)
- Decisions deferred without owner or date
- Sustainability risks: regulatory changes, ESG compliance gaps (PMBOK 8)

---

## Step 2 — Overall Project Risk (PMBOK 8 §2.7.1)

**New in PMBOK 8 — assess Overall Risk SEPARATELY from individual risks.**

> Overall Project Risk = the effect of ALL uncertainty on the project as a whole,
> arising from individual risks AND other sources of uncertainty combined.

### 2.1 — Overall Risk Assessment

```
Overall Risk Indicators — assess each:

| Dimension | Signal | Status |
|---|---|---|
| Schedule pressure | Critical path float < [X]% of duration | 🟢/🟡/🔴 |
| Cost confidence | Estimate accuracy > ±[X]% | 🟢/🟡/🔴 |
| Scope stability | Requirements change rate | 🟢/🟡/🔴 |
| Stakeholder alignment | Sponsor engagement level | 🟢/🟡/🔴 |
| External dependencies | # unconfirmed external dependencies | 🟢/🟡/🔴 |
| Team capacity | Resource availability confidence | 🟢/🟡/🔴 |
| Regulatory/compliance | Known compliance gaps | 🟢/🟡/🔴 |

Overall Project Risk Level: 🟢 Low / 🟡 Medium / 🔴 High / 🚨 Critical
```

### 2.2 — Overall Risk Response Strategies (PMBOK 8 §2.7.2)

Applied to the **whole project**, not individual risks:

| Strategy | When | Action |
|---|---|---|
| **Avoid** | Overall risk unacceptably high | Remove high-risk scope elements; if still unacceptable → consider project cancellation |
| **Exploit** | Overall risk significantly positive | Add scope to capture the upside |
| **Transfer/Share** | Org can't manage risk internally | Joint venture, risk-sharing contract, third-party |
| **Mitigate/Enhance** | Moderate overall risk | Replan, change scope boundaries, adjust resources |
| **Accept** | Within threshold | Continue as planned; establish overall contingency reserve |

---

## Step 3 — Qualitative Risk Analysis

### 3.1 — Scoring Model

| Score | Probability | Impact |
|---|---|---|
| 1 | Low (unlikely, <30%) | Minor disruption |
| 2 | Medium (possible, 30–70%) | Moderate delay / cost |
| 3 | High (likely, >70%) | Severe impact on scope / timeline / budget |

**Risk Score = Probability × Impact (1–9)**

| Score | Level |
|---|---|
| 7–9 | 🔴 High |
| 4–6 | 🟡 Medium |
| 1–3 | 🟢 Low |

### 3.2 — Senior Scoring Layers

Add to every risk entry:
- **Confidence Level:** Low / Medium / High
- **Estimation Flag:** Estimated (inferred) / Evidence-based (stated in input)

### 3.3 — Business Impact Tag

`Timeline` | `Cost` | `Scope` | `Quality` | `Stakeholder Trust` | `Business Outcome` | `Sustainability/ESG`

---

## Step 4 — Risk Response Planning (PMBOK 8 §2.7.2)

### 4.1 — Threat Response Strategies (🔴)

| Strategy | When to Use |
|---|---|
| **Avoid** | Eliminate the cause entirely; change plan to remove threat |
| **Mitigate** | Reduce probability or impact before risk occurs |
| **Transfer** | Shift responsibility to third party (insurance, contracts, warranties) |
| **Accept (Active)** | Absorb risk; establish contingency reserve |
| **Accept (Passive)** | No action; periodic review only |
| **Escalate** | Beyond PM authority → escalate to sponsor or portfolio level |

### 4.2 — Opportunity Response Strategies (🟢) — PMBOK 8 Complete Set

| Strategy | When to Use |
|---|---|
| **Exploit** | Ensure opportunity is definitely realized (probability → 100%) |
| **Enhance** | Increase probability or impact of the upside |
| **Share** | Partner with others best able to capture the opportunity |
| **Accept** | Take advantage if it occurs naturally; no proactive action |
| **Escalate** ⭐ | **New in PMBOK 8** — opportunity is outside project scope or PM authority → escalate to portfolio/program level to capture at higher level |

> ⭐ Escalate for opportunities: when the upside is real but belongs to
> a different level of the organization — don't let it be lost, escalate it.

### 4.3 — Root Cause Thinking (mandatory)

Every mitigation must address the **root cause**, not just the symptom:

❌ BAD: "Follow up with vendor"
✅ GOOD: "Schedule SLA alignment meeting with vendor by [date] — root cause:
no formal SLA agreed at project kickoff"

### 4.4 — Action Writing Rules

Every action must:
- Start with a **verb** (Escalate / Schedule / Confirm / Draft / Hire / Review...)
- Be **specific** — who does what, with what output
- Be **time-bound** — by when
- Never invent owner names — use "TBD" or "PM to assign"

### 4.5 — Contingent Response Strategies (PMBOK 8 §5 Tools)

Some responses are triggered only when specific conditions occur:

```
Contingent response:
  Trigger condition: [specific event or threshold]
  Response action:   [what happens when trigger fires]
  Owner:             [who monitors trigger + executes response]

Example:
  Trigger: Vendor misses milestone A by >5 days
  Response: Activate backup supplier pre-qualified in sourcing plan
  Owner: PM monitors weekly; procurement activates backup
```

Use contingent strategies when: the response effort is significant and
only worth deploying if the trigger actually fires.

---

## Step 5 — Risk Register Output

Produce all four tables:

### Table 1 — RAID Log

| # | Type | Description | Owner | Status |
|---|---|---|---|---|
| 1 | Risk (Known-Unknown) | [future uncertain event] | TBD | Open |
| 2 | Issue | [happening now] | TBD | Active |
| 3 | Assumption | [unverified belief] | TBD | To Validate |
| 4 | Dependency | [external reliance] | TBD | Tracked |
| 5 | Risk (Unknown-Known) | [knowledge gap — research needed] | TBD | Research |

### Table 2 — Risk Register

| # | Risk Statement (Cause→Event→Impact) | Impact Tag | P | I | Score | Level | Type | Classification | Strategy | Contingent? | Confidence | Owner | Action |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Due to... risk that... leading to... | Timeline | 3 | 3 | 9 | 🔴 | Threat | Known-Unknown | Mitigate | No | Med/Est | TBD | Specific action by date |
| 2 | Due to... opportunity that... enabling... | Business Outcome | 2 | 3 | 6 | 🟡 | Opportunity | Known-Unknown | Escalate | No | Evidence | TBD | Escalate to [level] by [date] |

### Table 3 — Issue Log

| # | Issue Description | Impact Now | Owner | Action Required | Due |
|---|---|---|---|---|---|
| 1 | [Active problem] | [Immediate impact] | TBD | [Specific action] | ASAP |

### Table 4 — Assumption & Dependency Log

| # | Type | Description | Validated? | Owner | Action |
|---|---|---|---|---|---|
| 1 | Assumption | [belief] | No | TBD | Confirm by [date] |
| 2 | Dependency | [external reliance] | Tracked | TBD | Monitor weekly |

### Table 5 — Overall Risk Summary (PMBOK 8)

```
Overall Project Risk: 🟢 Low / 🟡 Medium / 🔴 High / 🚨 Critical

Key drivers of overall risk:
  1. [dimension] — [status] — [signal]
  2. [dimension] — [status] — [signal]

Overall risk response strategy: [Avoid / Exploit / Transfer / Mitigate / Accept]
Action: [specific response at project level]
Management reserve for unknown-unknowns: $[X] or [X]% of budget
```

---

## Step 5B — Resilience Planning (PMBOK 8 §2.7.1)

**For Unknown-Unknowns — risks that cannot be identified upfront.**

> Project Resilience = ability to absorb impacts and recover quickly from
> setbacks, failures, or emergent risks (black swan events).

```
Resilience Plan — [Project Name]

1. Management Reserve
   Amount: $[X] or [X]% of budget
   Authority: Sponsor-controlled (not PM-controlled)
   Release condition: [criteria for drawing on reserve]

2. Organizational Continuity Alignment
   Business continuity plan referenced: [yes/no / plan name]
   Emergency response triggers: [conditions]
   PM awareness: [confirmed / to be confirmed]

3. Adaptive Capacity Mechanisms
   Fast decision protocol: [how quickly can key decisions be made?]
   Team cross-training: [backup for critical roles]
   Vendor backup: [pre-qualified alternative suppliers identified?]
   Communication escalation: [24h/48h escalation path defined?]

4. Resilience Review Cadence
   Resilience assessed at: [each phase gate / monthly / per sprint]
   Trigger for resilience activation: [threshold]
```

---

## Step 6 — Risk Monitoring & Control

### 6.1 — Monitoring Plan

| Element | Definition |
|---|---|
| **Review frequency** | 🔴 High → weekly; 🟡 Medium → per sprint/biweekly; 🟢 Low → per milestone |
| **Trigger conditions** | Early signals that a risk is materializing |
| **Re-score rules** | When to reassess P or I |
| **Escalation path** | Who to notify if risk crosses threshold |
| **Overall risk review** | Assess overall risk level at each phase gate |

### 6.2 — Monitoring Logic

- Re-evaluate top risks at every review cycle
- Convert Risk → Issue when it materializes (remove from Risk Register, add to Issue Log)
- Check: are any Unknown-Known risks now researchable and classifiable?
- Identify new risks continuously as project evolves
- Close resolved risks with documented outcome
- **Adaptive approach:** re-prioritize risk backlog at start of each sprint

---

## Step 7 — Decision Insights (Senior PM Layer)

Always include — a risk list without insights is junior-level output.

### 7.1 — Critical Risks

Top 1–3 risks that may derail the project — explain **why they matter**
beyond the score.

### 7.2 — Recommended Decisions NOW

What the PM should decide or act on **this week**, not next sprint.

### 7.3 — Trade-off Analysis

Surface the key tension explicitly:
> "Mitigating Risk #1 requires a 2-week buffer — which means either pushing
> the deadline or reducing scope. Recommend: [option] because [reason]."

### 7.4 — Risk Cascade (Systems Thinking)

Identify how individual risks + overall risk interact:
> "If Risk #1 materializes (vendor delay), it triggers Risk #3 (integration
> delay), which pushes overall project risk from 🟡 to 🔴 and activates
> Issue #2. These three are linked — mitigating Risk #1 breaks the cascade
> and keeps overall risk at 🟡."

---

## Step 8 — Prioritized Action Plan

Produce for all 🔴 High and 🟡 Medium risks:

| Priority | Risk | Root Cause | Action | Strategy | Owner | When |
|---|---|---|---|---|---|---|
| 1 | [risk name] | [root cause] | [specific action] | Mitigate | TBD | By [date] |

Rules:
- 🔴 High → action within **1 week**
- 🟡 Medium → action within **2 weeks**
- 🟢 Low → Accept or Monitor at next milestone
- Overall 🔴 → immediate escalation to sponsor

---

## Step 9 — Quick Wins (Do This Week)

Identify 1–3 low-effort, high-impact actions:

```
Quick Wins:
- ✅ [action] — reduces Risk #X from 🔴 to 🟡 (root cause: [cause])
- ✅ [action] — validates Assumption #Y (unblocks planning decision)
- ✅ [action] — confirms Dependency #Z SLA (prevents cascade to Risk #3)
- ✅ [action] — escalates Opportunity #W to portfolio for capture
```

---

## General Rules

- **Never invent data** — use "TBD" when owner or date is unknown
- **Never convert Issues to Risks** — keep them in separate logs
- **Always identify both Threats AND Opportunities**
- **Always classify risk type** — Known-Unknown / Unknown-Known per PMBOK 8
- **Always assess Overall Project Risk** — separate from individual risks
- **Escalate applies to BOTH threats and opportunities** — do not omit
- **Resilience plan for Unknown-Unknowns** — management reserve is not optional
- **Minimum 3 risks** — if input is thin, use Interview Mode (Step 0.2)
- **Always include Decision Insights** — mandatory for senior-quality output
- **Sustainability/ESG risks** — always scan; tag with Sustainability/ESG impact
- **Output language** — match user's language (Vietnamese in → Vietnamese out)
- After completing register: *"Would you like me to log any of these as Jira issues?"*
  (chains with pm-workflow-engine skill)

---

## Trigger Phrases

**English:** "analyze risks", "build risk register", "RAID analysis", "ROAM",
"extract risks from notes", "risk review", "what risks do you see",
"overall project risk", "project resilience", "unknown unknowns",
"risk classification", "opportunity response", "escalate opportunity",
"contingent response", "management reserve"

**Vietnamese:** "phân tích rủi ro", "tạo risk register", "RAID log",
"rủi ro dự án", "xác định rủi ro", "kế hoạch ứng phó rủi ro",
"rủi ro tổng thể dự án", "khả năng phục hồi", "dự phòng quản lý",
"phân loại rủi ro", "cơ hội dự án", "leo thang cơ hội"
