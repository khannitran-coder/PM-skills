# RTM Worked Examples

Read this before Workflow C output when the user wants a concrete example
to model theirs on, or when choosing between Agile-style and formal
Waterfall-style RTM.

## Agile-Style RTM (lean, story-centric)

Most PM-owned projects should default to this — lighter to maintain, lives
alongside the backlog.

```
| Req ID | Business Requirement                  | Epic        | Story ID(s)   | Test Case ID(s) | UAT Status  |
|--------|----------------------------------------|-------------|---------------|-----------------|-------------|
| BR-01  | Giảm thời gian đối soát công nợ        | Reporting   | US-03, US-04  | TC-05, TC-06    | In Progress |
| BR-02  | Ngăn duyệt đơn vượt hạn mức tự động    | Approvals   | US-07         | TC-09           | Not Started |
| BR-03  | Migrate dữ liệu khách hàng trước go-live| Transition | US-12         | TC-15, TC-16    | Passed      |
```

Update this table live as stories move through the backlog — it should
never be a one-time artifact generated once and forgotten.

## Formal/Waterfall-Style RTM (contractual, sign-off heavy)

Use when the user explicitly needs a formal deliverable (client contract,
regulated environment, external audit).

```
| Req ID | Requirement Description | Requirement Type | Source (doc/section) | Design Ref | Test Case ID | Test Status | Approved By | Approval Date |
|--------|--------------------------|-------------------|-----------------------|------------|---------------|-------------|-------------|----------------|
| BR-01  | ...                       | Functional        | BRD §3.1              | FRD §2.4   | TC-05         | Passed      | [sponsor]   | [date]         |
```

The formal version adds two things the lean version doesn't need day to
day: an explicit **Source** column (proves the requirement came from an
approved document, not scope creep) and a **sign-off** column per row
(not just a summary sign-off block).

## Reading an RTM for Orphans (do this before calling it "done")

1. Scan every Req ID row — if Story ID(s) is empty, that's a requirement
   with no delivery plan. Surface it before it becomes a "we forgot this"
   conversation at go-live.
2. Cross-check against the backlog — any story with no Req ID reference
   is unapproved scope. Either backfill the traceability (it maps to a
   requirement that wasn't logged) or flag it as scope creep.
3. Any row stuck at "Not Started" while its epic is otherwise "Passed"
   is a common go-live risk — surface it explicitly, don't let it hide
   in an otherwise-green summary.
