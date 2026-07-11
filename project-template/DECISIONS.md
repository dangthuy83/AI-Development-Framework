# DECISIONS.md

> Historical Record cho Project Decisions. Append hoặc supersede bằng record mới; không viết lại lịch sử như Living Document.

## Decision status

- `Proposed`: Đang chờ authority quyết định.
- `Accepted`: Đã được authority chấp thuận.
- `Rejected`: Đã xem xét và không chọn.
- `Superseded`: Được thay thế bởi Decision hoặc change record mới.

## Decision Index

| ID | Title | Status | Date | Superseded by |
|---|---|---|---|---|
| `D-001` | `[Tên Decision]` | `Proposed` | `[YYYY-MM-DD]` | `—` |

---

## D-001 — [Tên Decision]

**Status:** Proposed  
**Date:** `[YYYY-MM-DD]`  
**Decision authority:** `[Tên hoặc vai trò]`  
**Related:** `[PRODUCT/DESIGN/TASK/ROADMAP refs]`

### Context

[Bối cảnh, constraint, gap hoặc divergence dẫn đến nhu cầu quyết định.]

### Decision

[Lựa chọn cụ thể. Không ghi Accepted trước khi có authority.]

### Rationale

[Lý do lựa chọn dựa trên requirement, constraint và evidence.]

### Alternatives considered `[Conditional]`

| Alternative | Benefit | Cost hoặc risk | Reason not selected |
|---|---|---|---|
| `[Phương án]` | `[Lợi ích]` | `[Chi phí/risk]` | `[Lý do]` |

### Consequences

- Positive: `[Hệ quả]`
- Negative hoặc trade-off: `[Hệ quả]`
- Required follow-up: `[Task, migration hoặc document update]`

### Evidence `[Conditional]`

- `[Evidence ref]`

### Supersession `[Conditional]`

- Supersedes: `[D-ID hoặc None]`
- Superseded by: `[D-ID hoặc None]`
- Migration implication: `[Nếu có]`

---

## Cách thêm Decision mới

1. Copy toàn bộ mẫu `D-001` thành section mới với ID ổn định.
2. Thêm entry vào Decision Index.
3. Giữ nguyên record cũ.
4. Nếu thay Decision cũ, cập nhật liên kết supersession ở cả record cũ và mới mà không sửa nghĩa lịch sử.
5. Cập nhật current state tại `PRODUCT.md` hoặc `DESIGN.md` theo consequence đã Accepted.

## Quy tắc bảo trì template

- AI đọc khi cần biết lý do, thay đổi Product/Design quan trọng, refactor boundary, migration hoặc governance review.
- Decision authority chịu trách nhiệm Accepted/Rejected status; AI chỉ draft hoặc append sau authorization.
- Không rewrite context, decision hoặc rationale cũ để khớp current state.
- Same-authority Decision conflict phải tạo resolution hoặc superseding record; không silent override.
- Thiếu rationale hoặc provenance phải ghi gap, không được bịa.
- Không chứa backlog chung, session notes hoặc bản sao Product/Design.

## Completion Checklist cho mỗi Accepted Decision

- [ ] Có ID, date, authority và status.
- [ ] Context, Decision, Rationale và Consequences đầy đủ.
- [ ] Related sources có provenance.
- [ ] Supersession truy vết hai chiều khi áp dụng.
- [ ] Current Product hoặc Design được cập nhật riêng khi cần.

