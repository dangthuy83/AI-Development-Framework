# TASKS.md

> Single Source of Truth cho actionable work items và trạng thái task.

## Metadata

- Task owner hoặc planner: `[Tên hoặc vai trò]`
- Current milestone: `[ROADMAP M-ID]`
- Review gần nhất: `[YYYY-MM-DD]`

## Status vocabulary

- `Proposed`: Chưa được đưa vào active work.
- `Ready`: Scope, dependency và acceptance đủ để bắt đầu.
- `In Progress`: Đang được thực hiện.
- `Blocked`: Có blocker explicit.
- `Review`: Đang chờ review hoặc verification.
- `Completed`: Acceptance và required verification đã đạt.
- `Partial`: Một phần deliverable đạt, phần còn lại được ghi rõ.
- `Failed`: Execution không đạt và có failure evidence.
- `Skipped`: Được authority cho phép bỏ qua với lý do.
- `Deferred`: Hoãn sang thời điểm khác.

## Active Tasks

### T-001 — [Tên task]

- Status: `Proposed`
- Owner hoặc assignee: `[Tên, vai trò hoặc Unassigned]`
- Objective: `[Kết quả bounded, không phải Product Requirement mới]`
- Source refs: `[PRODUCT PR/BR, DESIGN section, DECISION D-ID, ROADMAP M-ID hoặc defect evidence]`
- Dependencies: `[T-ID, approval, source hoặc None]`
- Scope:
  - In: `[Phạm vi]`
  - Out: `[Ranh giới]`
- Constraints: `[Source-linked constraints]`

#### Deliverables

- `[Artifact hoặc outcome]`

#### Acceptance Criteria

- [ ] `AC-001` — `[Điều kiện pass/fail rõ]`

#### Verification

| ID | Method | Required evidence | Status |
|---|---|---|---|
| `VR-001` | `[Test \| Review \| Inspection \| Manual check]` | `[Evidence]` | `[Pending \| Passed \| Failed \| Limited]` |

#### Blockers or gaps `[Conditional]`

- `[Nội dung, owner và next action]`

#### Completion result

- Result: `[Completed | Partial | Blocked | Failed | Skipped | Not completed]`
- Evidence: `[Link hoặc summary]`
- Limitations: `[None hoặc mô tả trung thực]`
- Completed at: `[YYYY-MM-DD hoặc blank]`

## Backlog `[Conditional]`

| ID | Candidate outcome | Source | Priority | Readiness gap |
|---|---|---|---|---|
| `T-002` | `[Outcome]` | `[Source ref]` | `[Nếu project dùng]` | `[Gap hoặc None]` |

## Blocked Tasks `[Conditional]`

| ID | Blocker | Required resolver | Next review |
|---|---|---|---|
| `[T-ID]` | `[Blocker]` | `[Người, approval hoặc source]` | `[Date hoặc condition]` |

## Deferred Tasks `[Conditional]`

| ID | Reason | Revisit condition | Authority |
|---|---|---|---|
| `[T-ID]` | `[Lý do]` | `[Điều kiện]` | `[Nguồn]` |

## Quy tắc bảo trì template

- AI đọc khi implement, fix, refactor, test, review, continue hoặc actionable planning.
- Project owner hoặc planner xác lập task scope; assignee hoặc AI cập nhật progress và evidence trong quyền được giao.
- Task phải xuất phát từ source có provenance và không được override Product, Design hoặc Decision.
- Thiếu required Acceptance Criteria hoặc Verification là gap và có thể làm task chưa Ready.
- `Completed` yêu cầu evidence; limitation phải được báo cáo trung thực.
- Completed notable outcome chuyển sang `CHANGELOG.md`; Working Context chỉ giữ active subset.

## Completion Checklist cho task

- [ ] Objective, source, scope và dependency rõ.
- [ ] Deliverable và Acceptance Criteria có thể kiểm chứng.
- [ ] Verification status và evidence đầy đủ.
- [ ] Completion result chính xác.
- [ ] Upstream documents hoặc Changelog được xem xét cập nhật đúng ownership.
