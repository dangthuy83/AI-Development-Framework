# Cách migrate một project hiện hữu

## Mục đích và boundary

Chuyển project đang có code/tài liệu/chat/prompt sang chín Project Workspace files mà không mất provenance hoặc tạo SSOT song song. Migration không tự thay Product, Architecture hay Decision.

## Preconditions

- Có quyền đọc nguồn cũ và tạo/cập nhật project files.
- Xác định owner có quyền giải quyết Product/Design/same-authority conflict.
- Đọc Documentation, Knowledge Management, Security Standards; Session, Knowledge Lifecycle và Documentation Update Workflows; Start Project và Documentation Review Checklists.

## Migration worksheet

| Source item | Type | Authority | Freshness | Target owner | Conflict/gap | Action/evidence |
|---|---|---|---|---|---|---|
| `[path/chat/issue]` | `[Product\|Design\|Decision\|Roadmap\|Task\|Working\|Changelog\|Agent Rule\|evidence\|discard candidate]` | `[primary\|supporting\|observational\|historical]` | `[date/status]` | `[one of nine files]` | `[details]` | `[promote\|reference\|retain\|discard]` |

## Mười bước bắt buộc

1. Inventory memory, tài liệu cũ, chat summary, prompt, code, configuration, issues, tests/logs và evidence.
2. Phân loại từng item theo worksheet; không đưa mọi thứ vào Working Context.
3. Xác định authority và provenance. AI memory/chat chỉ supporting hoặc historical đến khi đối chiếu.
4. Ghi conflict/gap/divergence/staleness; không tự chọn giữa nguồn cùng authority.
5. Deduplicate: mỗi fact có đúng một owner; nguồn cũ chỉ reference/historical/supporting.
6. Promote chỉ fact đã kiểm chứng. Intended behavior thuộc Product; current design thuộc Design; observed behavior thuộc implementation/evidence.
7. Tạo `WORKING_CONTEXT.md` từ current goal/state/blocker/next action, không sao chép lịch sử.
8. Cấu hình `AGENTS.md` chỉ bằng command/rule/permission đã xác minh; unknown command ghi Unverified.
9. Chạy Documentation Review và thử một Open Session bằng [continue-session prompt](../global-workspace/templates/prompts/continue-session.md).
10. Giữ nguồn cũ khi cần audit, nhưng đánh dấu không còn là SSOT; không xóa/destructive cleanup thiếu approval.

## Frontend và data nhạy cảm

Nếu có UI, map Product journeys, Design direction, states, responsive/accessibility criteria và Impeccable policy. Không để tool/design reference đổi business logic/stack. Redact credentials, personal records và raw sensitive payload khỏi project docs/evidence.

## Completion và rollback

`completed` khi đúng chín file có ownership rõ, links hợp lệ, conflict blocking đã resolve, legacy sources không còn cạnh tranh SSOT, Start Project/Open Session/Documentation Review đạt. `partial` khi valid subset đã migrate nhưng còn non-blocking gap; `blocked` khi thiếu authority/context/permission; `failed` khi validation hỏng. Giữ backup/history và valid outputs; cleanup legacy là action riêng cần approval.
