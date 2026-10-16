---
name: "stakeholder-intelligence"
description: >
  Stakeholder analysis and engagement skill aligned with PMBOK 8.
  Use when the user needs:
  - Stakeholder identification, mapping, or analysis
  - Power/Interest grid, Salience Model, or engagement assessment
  - Stakeholder engagement strategy or communication plan
  - Handling resistant, neutral, or unsupportive stakeholders
  - Stakeholder register creation or update
  - Says: "stakeholder analysis", "power interest grid", "engagement plan",
    "phân tích stakeholder", "bản đồ stakeholder", "xác định stakeholder",
    "communication plan", "kế hoạch truyền thông", "ai cần được thông báo",
    "how to handle difficult stakeholder", "cách xử lý stakeholder phản đối"

  Four workflows: (A) stakeholder identification & mapping, (B) engagement
  strategy, (C) communication plan, (D) difficult stakeholder handling.
  Always use this skill — contains PMBOK 8 engagement principles, salience
  scoring rules, communication channel guidance, and routing logic to
  pm-workflow-engine and governance-value-engine.
---

# Stakeholder Intelligence Skill (PMBOK 8)

## Purpose

Provide **decision-quality stakeholder insights** by:
- Identifying all relevant stakeholders — visible and hidden
- Assessing power, interest, influence, and attitude
- Building proactive engagement strategies (not just communication plans)
- Supporting the PM through the full stakeholder lifecycle

> **PMBOK 8 Anchor:** Stakeholders are not just recipients of communication —
> they actively shape outcomes, define value, and can enable or block success.
> Engagement is two-way and continuous, not one-directional broadcasting.
> In PMBOK 8, this idea lives inside the **"Focus on Value"** principle
> (Standard for Project Management §3.4) *and* is operationalized in full
> through the **Stakeholders Performance Domain** (PMBOK 8 Guide §2.5,
> ANSI/PMI 99-001-2025): value only exists once stakeholders are understood
> and guided through change — engagement is a value-delivery mechanic, not
> a communications checklist. This skill implements that domain (§2.5) directly.

Four workflows, mapped to the **7 official PMBOK 8 processes** in the
Stakeholders Performance Domain (§2.5.2):

| Workflow | PMBOK 8 Process(es) Covered |
|---|---|
| **A** — Stakeholder Identification & Mapping | Identify Stakeholders |
| **B** — Engagement Strategy | Plan Stakeholder Engagement |
| **C** — Communication Plan | Plan Communications Management |
| **D** — Difficult Stakeholder Handling | Manage Stakeholder Engagement (the execution/negotiation process — this is where PMBOK 8 places conflict handling) |
| *(embedded in C3 escalation path + Monitoring section)* | Manage Communications |
| *(embedded in "Stakeholder Monitoring — Review Cadence")* | Monitor Stakeholder Engagement · Monitor Communications |

> Note: PMBOK 8 does not have a standalone "Develop Communications" process —
> **Manage Communications** (executing the distribution of info) and
> **Manage Stakeholder Engagement** (working the relationship, handling
> resistance) are both Executing-Focus-Area processes. This skill's Workflow D
> and the escalation logic in C3 are where those two processes live in practice.

### AI Use in Stakeholder Engagement (PMBOK 8 §2.5.1 & §2.5.3)

PMBOK 8 explicitly names AI as a **Key Concept** ("Data-driven decision-making")
and a **Tailoring Consideration** ("Large language models (LLMs) and artificial
intelligence (AI)") for this domain. Apply both when this skill uses AI to
produce stakeholder artifacts:

- **Data-driven decision-making (§2.5.1):** AI/predictive analytics may be
  used to help interpret stakeholder patterns (e.g., attitude trend across
  the register, engagement-level drift) — but the PM makes the call, not the
  model. Present AI-derived insight as input to the PM's judgment, never as
  a final verdict on a named person.
- **AI as a tailoring decision (§2.5.3):** Before using AI to draft
  communications, register entries, or engagement scripts involving specific
  named stakeholders, this is a **project-level tailoring decision**, not a
  default. If the project has a cybersecurity/data-governance function,
  PMBOK 8 instructs the PM to check with them on acceptable AI use before
  processing stakeholder data through it — because a stakeholder register
  routinely contains sensitive personal and political information (see
  **Data Handling & Confidentiality** rule in General Rules below).

---

## Step 0 — Context Intake

Extract from input first. Ask only for what is missing, **all at once**:

```
To build a stakeholder intelligence profile, I need:

1. Project objective — what outcome are we delivering?
2. Phase — Initiation / Planning / Execution / Closing?
3. Organization type — internal project, client-facing, multi-org, or regulatory?
4. Known stakeholders — who have you identified so far?
5. Any known concerns — resistance, political sensitivities, conflicts?
6. Urgency — is this for an upcoming meeting, presentation, or ongoing planning?
```

If user provides a document, charter, or notes → extract context silently,
confirm key parameters once, then proceed.

---

## Workflow A — Stakeholder Identification & Mapping

### When to use
User wants to identify who the stakeholders are, map them visually, and
understand who matters most and why.

### A1 — Stakeholder Identification (8 Categories)

Systematically scan for stakeholders across all eight categories:

| Category | Examples |
|---|---|
| **Internal — Delivery** | Project team, PM, technical leads, developers, QA |
| **Internal — Business** | Sponsor, product owner, department heads, executives |
| **Internal — Support** | PMO, finance, legal, IT, procurement, HR |
| **Internal — Governance** | Steering committee, change control board, audit |
| **External — Customer/User** | End users, customers, client organization, user groups |
| **External — Vendor/Partner** | Suppliers, contractors, subcontractors, technology vendors |
| **External — Regulatory** | Government agencies, standards bodies, regulators, auditors |
| **External — Broader** | Community, media, industry associations, competitors (monitoring) |

**Hidden stakeholder detection** — always scan for:
- People impacted by the change who are NOT explicitly on the list
- People who can veto or block without being formally involved
- Predecessors whose work feeds this project
- Successors who will operate/maintain the deliverable post-project
- "Shadow" influencers — people whose opinion shapes key decision-makers

For each stakeholder identified, populate the Stakeholder Register (A3).

### A2 — Power / Interest Grid Analysis

Classify each stakeholder on two dimensions:

```
        HIGH INTEREST
             │
  Manage     │     Engage
  Closely    │     Actively
  (keep      │     (key
  satisfied) │     players)
─────────────┼─────────────
  Monitor    │     Keep
  (low       │     Informed
  effort)    │     (show
             │     value)
        LOW INTEREST
  LOW POWER         HIGH POWER
```

| Quadrant | Label | Strategy |
|---|---|---|
| High Power, High Interest | 🔴 **Key Players** | Manage closely — co-create, involve in decisions |
| High Power, Low Interest | 🟡 **Keep Satisfied** | Manage carefully — don't bore, but don't surprise |
| Low Power, High Interest | 🟡 **Keep Informed** | Show value — they amplify your message |
| Low Power, Low Interest | 🟢 **Monitor** | Minimal effort — just ensure no nasty surprises |

### A3 — Salience Model (Advanced Layer)

For high-stakes projects, add Salience scoring on three dimensions:

| Dimension | Definition | Score (1–3) |
|---|---|---|
| **Power** | Ability to enforce their will on the project | 1=Low / 2=Med / 3=High |
| **Legitimacy** | Right to be involved (contractual, role-based, regulatory) | 1=Low / 2=Med / 3=High |
| **Urgency** | Degree to which their claim demands immediate attention | 1=Low / 2=Med / 3=High |

**Salience Score = Power + Legitimacy + Urgency (3–9)**

| Score | Label | Priority |
|---|---|---|
| 7–9 | 🔴 **Definitive** — must engage actively | Immediate priority |
| 5–6 | 🟡 **Expectant** — waiting and watching | High priority |
| 3–4 | 🟢 **Latent** — low salience now but may escalate | Monitor |

### A4 — Stakeholder Register Output

```
# Stakeholder Register — [Project Name]
Last Updated: [date] | Version: [X]

| # | Name / Group | Role | Category | Power | Interest | Salience | Current Attitude | Desired Attitude | Key Concern | Engagement Level Needed |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | [Name] | [Role] | Internal/External | H/M/L | H/M/L | [score] | 😀 Supportive / 😐 Neutral / 😠 Resistant | [target] | [what they care about most] | Key Player / Keep Informed / etc. |
```

**Current Attitude Icons:**
- 😀 Supportive — actively backing the project
- 😐 Neutral — aware but uncommitted
- 🤔 Unaware — not yet engaged
- 😟 Resistant — has concerns or opposes
- 😠 Blocking — actively working against

After output: *"Register complete — run Workflow B to build engagement strategy per stakeholder?"*

---

## Workflow B — Engagement Strategy

### When to use
User has identified stakeholders (or uses Workflow A output) and needs to
define HOW to engage each one — not just what to communicate.

> **PMBOK 8 distinction (Guide §2.5.1, Key Concept: Stakeholder engagement):**
> Communication tells people things. Engagement involves them — it means
> "identifying and analyzing stakeholder needs and managing expectations and
> communications to foster stakeholder support." High-stakes stakeholders
> need engagement, not newsletters.

### B1 — Engagement Level Scale (PMBOK Standard)

Assess current vs. desired engagement level for each key stakeholder:

| Level | Definition | Signal |
|---|---|---|
| **Unaware** | Doesn't know about the project | Never been contacted |
| **Resistant** | Knows about it, actively opposes | Raises objections, blocks decisions |
| **Neutral** | Aware but non-committal | Shows up, gives nothing |
| **Supportive** | Favorable, willing to help | Agrees to actions, advocates informally |
| **Leading** | Actively driving project success | Champions internally, removes barriers |

→ Goal is to move each key stakeholder from current to desired level.

### B2 — Engagement Gap Analysis

For each stakeholder in the 🔴 Key Player quadrant:

```
| Stakeholder | Current Level | Desired Level | Gap | Root Cause of Gap | Engagement Action |
|---|---|---|---|---|---|
| [Name] | Resistant | Supportive | Large | Concern about job impact | 1:1 meeting + impact assessment |
| [Name] | Neutral | Leading | Medium | Not yet seen the value | Include in steering committee |
```

### B3 — Engagement Strategy Toolkit

Select tactics based on gap size and root cause:

| Root Cause | Recommended Tactics |
|---|---|
| Lack of awareness | Briefing session, executive summary, roadshow |
| Concern about impact | 1:1 conversation, impact assessment, involvement in design |
| Political / territorial | Sponsor intervention, win-win framing, early involvement |
| Loss of control | Co-design approach, advisory role, regular check-ins |
| Competing priorities | Executive alignment, resource negotiation via sponsor |
| Missing information | Direct answer to their specific question, not general comms |
| Distrust (past failure) | Transparent reporting, early wins, frequent low-stakes touchpoints |

### B4 — Engagement Plan Output

```
# Stakeholder Engagement Plan — [Project Name]
Version: [X] | Date: [date]

## Stakeholder Engagement Summary

| # | Stakeholder | Current Level | Desired Level | Primary Tactic | Owner | Frequency | Next Action | Due |
|---|---|---|---|---|---|---|---|---|
| 1 | [Name] | Resistant | Supportive | 1:1 meeting — address job impact concern | PM | Weekly | Schedule meeting | [date] |
| 2 | [Name] | Neutral | Leading | Include in steering committee | Sponsor | Monthly | Send invitation | [date] |

## Key Engagement Rules for This Project
- [Rule 1: e.g., "All executive stakeholders briefed before public announcements"]
- [Rule 2: e.g., "Sponsor informed within 24h of any 🔴 High risk materializing"]
- [Rule 3: e.g., "User group consulted before any scope change affecting UX"]

## Engagement Monitoring
Review stakeholder attitudes: [weekly / fortnightly / per milestone]
Red flag trigger: Any 🔴 Key Player moves from Supportive → Neutral
Escalation: PM informs Sponsor within 48h of attitude regression
```

---

## Workflow C — Communication Plan

### When to use
User needs to define what information goes to whom, how often, through what
channel, and with what level of detail.

### C1 — Communication Needs Analysis

For each stakeholder group, answer:

| Question | Guidance |
|---|---|
| What do they need to know? | Role-specific: executives want outcomes, teams want tasks |
| Why do they need it? | To make decisions / take action / stay informed / provide approval |
| When do they need it? | Cadence: real-time / daily / weekly / milestone-based / on-demand |
| How should it be delivered? | See channel richness matrix below |
| Who sends it? | PM / sponsor / team lead — match sender authority to audience |
| How detailed? | Executives: 1 page. Teams: full detail. Clients: polished summary |

### C2 — Communication Channel Selection

Match channel richness to message complexity:

| Message Type | Recommended Channel | Why |
|---|---|---|
| Crisis / major issue | Face-to-face / video call | Maximum richness — needed for nuance and reaction |
| Complex decision | Meeting + written follow-up | Allows real-time Q&A, creates record |
| Regular status update | Email + dashboard | Efficient, scannable, asynchronous |
| Quick coordination | Instant message / Slack | Speed over formality |
| Broad announcement | Email + intranet post | Reach + searchable record |
| Sensitive news | 1:1 conversation first | Relationship preservation before formal communication |
| Project documentation | Project portal / wiki | Single source of truth |

**Anti-patterns to avoid:**
- Sending complex decisions via email only (no dialogue possible)
- Using meetings for information that could be an email (wastes time)
- Informal channels for formal decisions (creates accountability gaps)
- One-size-fits-all newsletters to both executives and front-line staff

### C3 — Communication Plan Output

```
# Communication Plan — [Project Name]
Version: [X] | Date: [date]

| # | Audience | Information | Purpose | Format | Channel | Frequency | Sender | Owner |
|---|---|---|---|---|---|---|---|---|
| 1 | Executive Sponsor | Project health, key decisions | Maintain alignment & get decisions | 1-page dashboard | Email + meeting | Monthly | PM | PM |
| 2 | Steering Committee | Progress, risks, budget | Governance oversight | Status report | Meeting + slides | Bi-weekly | PM | PM |
| 3 | Project Team | Tasks, priorities, blockers | Coordination | Task board + standup | Jira + standup | Daily | Team Leads | PM |
| 4 | End Users | Upcoming changes, training dates | Change readiness | Newsletter + FAQ | Email + intranet | Monthly | Change lead | PM |
| 5 | External Vendor | Requirements, approvals | Delivery coordination | Formal document | Email + meeting | Weekly | PM | PM |

## Communication Escalation Path
| Situation | Action | Timeline |
|---|---|---|
| Risk escalates to 🔴 High | PM → Sponsor notification | Within 24 hours |
| Milestone missed | PM → Steering Committee | Before next meeting; email within 48h |
| Scope change request | PM → CCB formal submission | Before any work begins |
| Stakeholder complaint received | PM acknowledges → investigates → responds | 48h acknowledgment / 1 week resolution |

## Review & Update
Communication plan reviewed: [monthly / per phase]
Owner of updates: [PM role]
```

---

## Workflow D — Difficult Stakeholder Handling

### When to use
User is facing a specific resistant, blocking, or politically complex stakeholder
and needs a tailored handling strategy.

### D1 — Resistance Classification

First, identify the TYPE of resistance — each requires a different response:

| Type | Description | Signal | Wrong Response | Right Response |
|---|---|---|---|---|
| **Information gap** | Missing facts → wrong conclusions | Asks many clarifying questions | Push more documentation | 1:1 briefing, answer specific questions |
| **Legitimate concern** | Valid worry about real impact | Raises specific, substantive objection | Dismiss or override | Acknowledge, investigate, adjust if valid |
| **Political / territorial** | Protecting turf, budget, or authority | Blocks decisions, slows approvals | Go around them | Involve early, give visible role, link to their win |
| **Personal / trust deficit** | Past bad experience with PM or project type | Skeptical regardless of evidence | Prove yourself with data | Build relationship first, then data |
| **Organizational misalignment** | Their priorities conflict with project | Consistently deprioritizes the project | Escalate immediately | Sponsor alignment, executive re-prioritization |
| **Change fatigue** | Too much change happening at once | Disengaged, going through motions | Add more urgency | Reduce cognitive load, sequence changes |

### D2 — Difficult Stakeholder Response Framework

```
Step 1: Listen first — understand before responding
  → What is their REAL concern? (stated concern ≠ real concern often)
  → What do they stand to lose?
  → What would "winning" look like for them?

Step 2: Validate — even if you disagree
  → "I understand your concern about X..."
  → Never dismiss, minimize, or argue in the moment
  → Validation ≠ agreement

Step 3: Reframe toward shared interest
  → Find the overlap between their goal and project goal
  → Lead with "we both want..." not "but the project needs..."

Step 4: Involve — give them a role
  → Resistant stakeholders often become champions when given ownership
  → Advisory role, named contributor, review gate owner

Step 5: Escalate appropriately (if steps 1–4 fail)
  → Route through sponsor — not around the stakeholder
  → Frame as "need your help aligning [name]" not "I have a problem with [name]"
  → Document all engagement attempts before escalating
```

### D3 — Specific Scenario Playbooks

#### Scenario 1: The Blocker (High Power, actively working against)
```
Situation: Key stakeholder with authority is actively blocking approvals or resources.

Diagnosis: Usually political (turf), fear of change, or a legitimate concern being ignored.

Response:
1. Request a private 1:1 with the stakeholder — not in a group setting
2. Ask open questions: "What would need to be true for you to feel comfortable moving forward?"
3. If legitimate concern → address it concretely and visibly
4. If political → escalate to sponsor with evidence of blocking behavior
5. Involve sponsor in next interaction — changes the power dynamic

Never: Go around a high-power blocker without sponsor cover.
Always: Document every engagement attempt.
```

#### Scenario 2: The Ghost (High Power, Low Engagement — never responds)
```
Situation: Critical decision-maker who ignores emails, skips meetings, delegates everything.

Diagnosis: Too busy / doesn't see urgency / disengaged / has a different priority.

Response:
1. Move from email to live channel — request 15 min via phone or in person
2. Simplify the ask — never send a 10-page document for a yes/no decision
3. Use their assistant or EA to get on the calendar
4. Route through someone they respect (their peer, their boss)
5. If decision is blocking project: escalate to your sponsor to engage their sponsor

Message template:
"[Name], I need one decision from you by [date] to keep the project on track.
I can explain in 10 minutes — can we find time this week?"
```

#### Scenario 3: The Skeptic (Neutral, high visibility — publicly questions the project)
```
Situation: Influential stakeholder who publicly questions value or approach,
but hasn't formally opposed.

Diagnosis: Often information gap + credibility test.

Response:
1. Give them data — but only the data they asked for, not everything
2. Invite them to challenge the plan formally — turns skepticism into constructive input
3. Acknowledge previous project failures that may be driving skepticism
4. Give them a small win they can see early (pilot, proof of concept)
5. Credit them publicly when their input improved the project

Never: Get defensive or flood with justification — confirms their skepticism.
```

### D4 — Difficult Stakeholder Action Plan Output

```
# Stakeholder Action Plan — [Stakeholder Name]
Date: [date] | Prepared by: [PM]

Stakeholder profile:
- Role: [role]
- Power level: High / Medium / Low
- Current attitude: [attitude]
- Resistance type: [type from D1]

Root cause of resistance:
[Specific, honest assessment — not "they're difficult"]

What they stand to lose / are protecting:
[Specific concern]

What would "winning" look like for them:
[Their definition of success]

Engagement strategy:
| Action | Who | When | Expected Outcome |
|---|---|---|---|
| [Specific action — see D2] | [role] | [date] | [what we're trying to achieve] |

Escalation trigger:
If [specific condition], escalate to [sponsor] by [date].

Success criteria for this action plan:
[How will we know the stakeholder has moved to the desired engagement level?]
```

---

## Stakeholder Engagement Assessment Matrix

Use this to visualize and track movement over time:

```
Stakeholder Engagement Assessment Matrix

| Stakeholder | Unaware | Resistant | Neutral | Supportive | Leading |
|---|---|---|---|---|---|
| [Name 1] | | | C→ | →D | |
| [Name 2] | | C | →D | | |
| [Name 3] | | | | C=D | |

Legend:
C = Current engagement level
D = Desired engagement level
→ = Direction of movement needed
= = Already at desired level (maintain)
```

---

## Stakeholder Monitoring — Review Cadence

After the engagement plan is established, define a review rhythm:

| Review Type | Frequency | Trigger |
|---|---|---|
| Attitude check — all key stakeholders | Weekly (quick — 15 min) | Routine |
| Full register update | Per milestone or phase gate | Scheduled |
| Urgent reassessment | Within 48h | Any 🔴 Key Player regresses |
| Communication effectiveness review | Monthly | Scheduled |

**Monitoring signals to watch:**
- Stakeholder stops responding → attitude regression, investigate
- New stakeholder appears mid-project → update register immediately
- A Neutral becomes vocal in opposition → escalate to Resistant
- A Resistant provides constructive input → opportunity to convert

---

## Check Results — Outcome Verification (PMBOK 8 Table 2-9)

PMBOK 8 requires every performance domain to close the loop with a **Check
Results** step: outcomes are only valuable if verified, not just produced.
Run this check after Workflow B/C/D output, or when the user asks "is our
stakeholder engagement actually working?":

| Target Outcome (PMBOK 8) | How to Check |
|---|---|
| Stakeholder engagement is maintained | Pulse-check via short interviews/survey; track a simple sentiment indicator (e.g., a lightweight Net Promoter Score–style question: *"How likely are you to recommend continuing this project as-is?"*) across key stakeholders over time |
| Risk responses tied to stakeholders are implemented | Cross-check the stakeholder register against the issue log / risk register — every 🔴 Key Player or 🔴 Definitive-salience stakeholder marked Resistant should have a corresponding risk entry (route via **risk-management**) |
| Stakeholder agreement with project objectives achieved | Count of change requests originating from stakeholder pushback — falling trend = agreement improving; review feedback captured on increments/milestones |
| Communications management is performed | Periodically re-review the Communication Plan (Workflow C) against actual channel usage — is the plan still matching stakeholder needs, or has it gone stale? |
| Project plans integrated with vendor/supplier perspective | If **External — Vendor/Partner** stakeholders exist in the register, confirm their delivery commitments are reflected in the project plan, not just their communication preferences |

If a check fails, do not just re-run the workflow — diagnose *why* (wrong
channel? wrong cadence? real resistance vs. perceived?) before proposing a fix.

---

## Inter-Skill Routing

Surface at end of workflow — never interrupt primary output:

| Condition | Routing Action |
|---|---|
| Stakeholder register complete, need engagement plan | Proceed to Workflow B automatically |
| Communication plan defined, need to log comms tasks to Jira | *"Communication actions identified — run **pm-workflow-engine** to log as Jira tasks?"* |
| Difficult stakeholder linked to a project risk | *"Stakeholder resistance is a project risk — run **risk-management** skill to log and analyze?"* |
| Engagement plan requires sponsor activation | *"Sponsor engagement needed — reference **governance-value-engine** for sponsor role guidance?"* |
| Stakeholder is involved in budget/funding decisions or financial controls | *"This stakeholder has a Finance role (PMBOK 8 §2.5.4 — Stakeholders domain interacts directly with Finance) — route to **governance-value-engine** or **planning-estimation-engine** for budget alignment?"* |
| Change management is significant component | *"Stakeholder change volume is high — consider linking to organizational change management planning"* |

---

## General Rules

- **Never label stakeholders as "difficult"** — identify the root cause of their behavior
- **Engagement ≠ Communication** — communication is one-way; engagement is two-way
- **Always identify hidden stakeholders** — the ones missed at the start cause the most trouble at the end
- **Salience changes over time** — a Latent stakeholder can become Definitive overnight
- **Never go around a high-power stakeholder** — route through sponsor
- **Attitude is data** — track it systematically, not anecdotally
- **Output language** — match user's language (Vietnamese in → Vietnamese out)
- **One context intake** — ask all missing questions at once in Step 0, never drip-feed
- **Never produce a stakeholder register without engagement guidance** — a list without strategy is incomplete
- **Data Handling & Confidentiality** — the Stakeholder Register and Action
  Plan (A4, D4) routinely contain sensitive personal and political data:
  named individuals, resistance profiles, "who is blocking," private
  attitudes. Before the user exports, shares, or pastes this output outside
  the current conversation (e.g., into a shared doc, email, or a wider
  audience), remind them once: *"Register này chứa đánh giá cá nhân nhạy
  cảm (thái độ, mức độ phản đối) — cân nhắc ẩn danh hóa tên/vai trò hoặc
  giới hạn quyền truy cập trước khi chia sẻ ra ngoài nhóm dự án."* Do not
  repeat this reminder on every turn — once per output is enough.

---

## Reference Files

| File | When to Read |
|---|---|
| `references/power-interest-grid.md` | Before Workflow A — grid construction, examples by industry |
| `references/engagement-tactics.md` | Before Workflow B — full tactic library by stakeholder type |
| `references/communication-channels.md` | Before Workflow C — channel richness framework and templates |
| `references/difficult-stakeholder-playbooks.md` | Before Workflow D — detailed scenario scripts |

---

## Trigger Phrases

**English:**
- "Who are my stakeholders?"
- "Build a stakeholder register"
- "Create a power interest grid"
- "How do I handle this resistant stakeholder?"
- "Write a communication plan"
- "Stakeholder engagement strategy"
- "How do I get buy-in from [person/group]?"
- "Who needs to be kept informed?"
- "This stakeholder is blocking us — what do I do?"

**Vietnamese:**
- "Xác định stakeholder cho dự án"
- "Phân tích stakeholder"
- "Vẽ bản đồ quyền lực và lợi ích"
- "Lập kế hoạch truyền thông"
- "Cách xử lý stakeholder phản đối"
- "Làm sao để có được sự ủng hộ từ [tên]?"
- "Ai cần được thông báo về dự án?"
- "Stakeholder này đang cản trở dự án — phải làm gì?"
- "Chiến lược giao tiếp với stakeholder"
