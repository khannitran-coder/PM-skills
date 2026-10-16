# Elicitation Techniques — Deeper Guidance

Read this when Workflow A's input is thin (a one-line ask, a vague email,
or "just figure out what they need").

## Interview Script Skeleton

Use when you have direct access to a stakeholder (or the user is relaying
answers from one).

1. **Context first** — "Trước khi đi vào chi tiết, mô tả giúp mình quy
   trình hiện tại đang diễn ra như thế nào?"
2. **Pain first, feature second** — "Điểm nào đang gây khó khăn/tốn thời
   gian nhất?" (never start with "bạn muốn tính năng gì")
3. **Quantify the pain** — "Việc này tốn bao nhiêu thời gian/người/lần?"
   (turns a vague ask into a measurable business requirement)
4. **Surface the workaround** — "Hiện tại mọi người đang xử lý việc này
   như thế nào để tạm ổn?" (reveals hidden requirements and hidden users)
5. **Close with prioritization** — "Nếu chỉ chọn được 3 điều quan trọng
   nhất trong danh sách này, đó là gì?"

## Workshop Facilitation Notes

- Capture agreement and disagreement separately — a workshop that "reached
  consensus" on paper but papered over real disagreement produces
  requirements that blow up later.
- Use a simple two-column capture live: "Agreed" / "Parking lot" (unresolved
  — assign an owner and a follow-up date, don't let it die silently).
- When two stakeholder groups want contradictory things, don't average
  them into a mushy compromise — document both asks and the conflict
  explicitly in the BRD's Open Questions section, and route to
  stakeholder-intelligence if it needs an engagement strategy to resolve.

## 5 Whys — Applied to Requirements

```
Ask: "Thêm nút xuất Excel"
Why? → Kế toán cần xem số liệu công nợ
Why? → Để đối soát với ngân hàng cuối tháng
Why? → Đối soát thủ công đang mất 2 ngày/tháng
Why? → Vì phải lọc dữ liệu tay từ nhiều màn hình
→ Real business requirement: "Giảm thời gian đối soát công nợ từ 2 ngày
  xuống còn vài giờ" — export Excel is ONE possible solution, not the
  requirement itself. Document the requirement, then let functional
  requirements (export, filter, auto-reconcile...) be candidate solutions.
```

Stop at 3–5 whys — further than that usually drifts into root-cause
territory that belongs in risk-management, not requirements gathering.

## Observation / Walkthrough Checklist

When asked to elicit requirements for an existing manual process:
- Ask to see it done, not described — "cho mình xem bạn làm việc này như
  thế nào" surfaces steps people forget to mention because they're
  automatic to them.
- Note every manual workaround, spreadsheet, or shadow system — these are
  unstated requirements the eventual solution needs to account for.
- Note who is NOT in the room but touches the process (upstream/downstream)
  — likely hidden stakeholders for stakeholder-intelligence.
