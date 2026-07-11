# WORKING_CONTEXT.md

> RAM nhẹ của project: chỉ giữ current focus, blocker, handoff và next action cần cho lần tiếp tục kế tiếp.

## Session handoff metadata

- Cập nhật gần nhất: `[YYYY-MM-DD HH:mm và timezone]`
- Cập nhật bởi: `[Người hoặc AI Agent]`
- Current lifecycle hoặc milestone: `[ROADMAP M-ID hoặc trạng thái]`
- Active task refs: `[TASK ID]`

## Current objective

[Một mục tiêu hiện hành, bounded và liên kết Task hoặc Session Contract.]

## Active scope

### In scope

- `[Phạm vi đang thực hiện]`

### Out of scope

- `[Ranh giới cần giữ trong lần tiếp tục]`

## Current status

- Completion state: `[Not started | In progress | Partial | Blocked | Ready for review]`
- Kết quả gần nhất: `[Tóm tắt ngắn, có evidence ref nếu cần]`
- Verification state: `[Đã chạy gì, chưa chạy gì]`

## Confirmed continuation facts

> Chỉ giữ fact thực sự cần cho lần tiếp tục. Link source chuyên trách thay vì copy.

- `[Fact]` — Source: `[PRODUCT/DESIGN/DECISION/TASK/evidence ref]`

## Blockers, gaps and pending approvals

| ID | Type | Description | Impact | Owner hoặc approver | Next action |
|---|---|---|---|---|---|
| `WC-001` | `[Blocker \| Gap \| Conflict \| Divergence \| Approval]` | `[Nội dung]` | `[Impact]` | `[Tên hoặc vai trò]` | `[Action]` |

## Temporary hypotheses `[Conditional]`

> Hypothesis không phải Project Knowledge. Xóa hoặc promote về source đúng sau verification.

- `[Giả thuyết]` — Verification: `[Cách kiểm chứng]`

## Next actions

1. `[Action cụ thể tiếp theo]`
2. `[Verification hoặc handoff action]`

## Relevant source links

- Product: `[PRODUCT section]`
- Design: `[DESIGN section]`
- Decision: `[D-ID hoặc None]`
- Tasks: `[TASK ID]`
- Evidence: `[Link hoặc command result reference]`

## Handover note

[Điều người hoặc AI tiếp theo cần biết để tiếp tục mà không đọc session history.]

## Close Session maintenance

- [ ] Task status và evidence đã cập nhật tại `TASKS.md`.
- [ ] Durable Product, Design hoặc Decision knowledge đã promote về source đúng.
- [ ] Verified notable completion đã chuyển sang `CHANGELOG.md` khi cần.
- [ ] Context không còn cần đã bị prune.
- [ ] Next action và blocker còn hiệu lực.
- [ ] Không có secret, raw log hoặc chat transcript.

## Quy tắc bảo trì template

- AI phải đọc khi continue, handover hoặc resume blocked work.
- Người hoặc AI đóng phiên chịu trách nhiệm cập nhật; project owner giải quyết conflict về current state.
- Prefer replace và prune; không nối session history theo ngày.
- Nếu Working Context khác Tasks, code hoặc evidence, ghi divergence và xác minh.
- Working Context không có authority cho Product, Architecture hoặc Decision.
- Giữ file ở mức một màn hình đến vài trang ngắn khi có thể.

## Completion Checklist

- [ ] Người tiếp tục biết ngay objective, scope, status, blocker và next action.
- [ ] Active task và source links hợp lệ.
- [ ] Không chứa durable knowledge chưa promote.
- [ ] Không chứa completed chronology hoặc toàn bộ task inventory.
