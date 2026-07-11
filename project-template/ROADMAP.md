# ROADMAP.md

> Single Source of Truth cho milestone, dependency, sequencing và trạng thái lộ trình. Roadmap không xác lập Decision.

## Metadata

- Roadmap owner: `[Tên hoặc vai trò]`
- Scope: `[Product hoặc release scope]`
- Current milestone: `[M-ID]`
- Review gần nhất: `[YYYY-MM-DD]`

## Status vocabulary

- `Proposed`: Chưa được cam kết thực hiện.
- `Accepted`: Phạm vi milestone đã được chấp thuận.
- `In Progress`: Đang thực hiện và đã đáp ứng entry condition.
- `Completed`: Exit criteria đã đạt và có evidence.
- `Blocked`: Không thể tiếp tục do blocker explicit.
- `Deferred`: Chủ động hoãn; không phải completed.

## Milestones

| Order | ID | Outcome | Dependencies | Status | Exit Criteria | Evidence |
|---:|---|---|---|---|---|---|
| 1 | `M-001` | `[Kết quả milestone]` | `[None hoặc M-ID]` | `Proposed` | `[Điều kiện đạt]` | `[Link khi có]` |

## Current milestone detail

### `[M-001] [Tên milestone]`

- Intended outcome: `[Kết quả, không phải task list]`
- Entry conditions: `[Điều kiện bắt đầu]`
- Exit criteria: `[Điều kiện hoàn thành]`
- Product refs: `[PR/BR ID]`
- Design hoặc Decision refs: `[Link]`
- Tasks: [TASKS.md](TASKS.md)

## Dependencies and sequencing

[Giải thích dependency không hiển nhiên hoặc parallel workstream.]

## Roadmap risks and blockers

| ID | Risk hoặc blocker | Affected milestone | Owner | Mitigation hoặc next action |
|---|---|---|---|---|
| `RB-001` | `[Nội dung]` | `[M-ID]` | `[Tên hoặc vai trò]` | `[Action]` |

## Deferred items `[Conditional]`

| Item | Reason | Revisit condition | Authority |
|---|---|---|---|
| `[Nội dung]` | `[Lý do]` | `[Điều kiện]` | `[Nguồn]` |

## Future options `[Conditional]`

> Đây không phải committed roadmap và không tự trở thành Accepted Decision.

- `[Hướng có thể nghiên cứu và điều kiện kích hoạt]`

## Quy tắc bảo trì template

- AI đọc khi plan, prioritize, initialize, continue ở mức milestone, release planning hoặc dependency analysis.
- Project owner hoặc planner chịu trách nhiệm milestone, dependency và status.
- Chỉ đánh dấu Completed khi exit criteria có evidence.
- Product, Design và Decisions có authority trong domain tương ứng.
- Không chứa Architecture Decision, Product Requirement mới, task chi tiết hoặc session log.

## Completion Checklist

- [ ] Current milestone và status rõ.
- [ ] Mỗi milestone có outcome, dependency và exit criteria.
- [ ] Status khớp Tasks và evidence hoặc divergence đã được ghi.
- [ ] Future options tách khỏi committed roadmap.
- [ ] Roadmap không được dùng để xác lập Decision.

