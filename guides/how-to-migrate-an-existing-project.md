# Cách migrate một project hiện hữu

## Mục đích và boundary

Chuyển project đang có code/tài liệu/chat/prompt sang chín Project Workspace files mà không mất provenance hoặc tạo SSOT song song. Migration không tự thay Product, Architecture hay Decision.

## Preconditions

- Có quyền đọc nguồn cũ và tạo/cập nhật project files.
- Xác định owner có quyền giải quyết Product/Design/same-authority conflict.
- Đọc Documentation, Knowledge Management, Security Standards; Session, Knowledge Lifecycle và Documentation Update Workflows; Start Project và Documentation Review Checklists.

## Standard Codex Migration Runbook

Runbook này là entry prompt chuẩn cho project hiện hữu dùng Codex. Nó điều phối ba phase nhưng không bỏ qua approval gate: discovery luôn read-only; remediation chỉ bắt đầu sau khi owner xác nhận authority và exact target files; post-remediation validation nên chạy trong session mới để giữ tính độc lập.

Trước khi dùng, đặt Framework ở path ổn định, ưu tiên Git submodule được pin commit, và mở Codex tại root project cần migrate. Cung cấp tối thiểu:

```text
Project path: [PROJECT_PATH]
Framework path: [.ai-development-framework/ hoặc path đã xác minh]
Project owner: [name/role]
Product/Design/Decision authority: [name/role hoặc chưa xác định]
Legacy memory/docs: [paths hoặc chưa biết]
Database thật: [có/không/chưa xác định]
Sensitive local config: [có/không/chưa xác định; không đưa raw value]
Documentation write permission: [chưa cấp/có trong exact scope]
Technical verification permission: [restore/build/run/test boundaries]
```

Copy prompt sau vào Codex:

```text
Migrate project hiện hữu sang AI Development Framework.

Project root: [PROJECT_PATH]
Framework path: [FRAMEWORK_PATH]

Tuân thủ Framework tại commit/path đang được pin hoặc đã xác minh. Thực hiện
theo ba phase và bắt buộc dừng tại mỗi approval gate.

PHASE 1 — Discovery read-only

1. Kiểm kê filesystem, Git/submodule, documents, legacy memory/instructions,
   source, configuration, tests và evidence.
2. Đọc migration guide, Agent guide, Documentation/Knowledge Management/
   AI Working/Security Standards và chín Project Workspace templates.
3. Không sửa file; không fetch/update dependency; không chạy build, app,
   database hoặc destructive command; không đọc/hiển thị raw secret.
4. Memory, chat, code comment và generated artifact chỉ là supporting input.
   Code/config có authority cho implemented state, không tự thay Product.
5. Lập Nine-file Matrix, Migration Worksheet, ownership/conflict/gap/
   divergence findings, authority questions và proposed remediation plan.
6. Dừng để Project Owner xác nhận authority, Product/Decision facts,
   current state, exact target files và permission.

PHASE 2 — Documentation remediation

Chỉ chạy sau direct explicit approval cho exact files/actions.

1. Tạo hoặc hợp nhất đúng chín Project Workspace files; không overwrite file
   hiện hữu trước inventory/review.
2. Promote fact đã xác nhận về đúng owner; giữ provenance và explicit gaps.
3. Giữ legacy memory làm supporting/historical; không xóa, rename hoặc tiếp tục
   dùng nó như SSOT.
4. Không sửa code/config/database/generated artifacts nếu chưa có authorization
   riêng; không stage/commit/push.
5. Validate manifest, empty files, links/anchors, tables/fences, ownership,
   status, provenance, sensitive-data boundary và changed-path allowlist.
6. Dừng với exact changed-file report, checklist results và remaining gaps.

PHASE 3 — Independent post-remediation validation

Ưu tiên session Codex mới và read-only.

1. Không mặc nhiên tin remediation report; xác minh filesystem, Git/diff và
   submodule/dependency pin thực tế.
2. Kiểm tra 9/9 files, required sections, ownership, links/anchors, provenance,
   legacy-source boundary, security và unsupported completion claims.
3. Chạy Start Project, Open Session và Documentation Review Checklists bằng
   evidence thật; không ghi Pass cho check chưa chạy.
4. Báo Pass, Pass with limitations, Needs remediation hoặc Blocked; không sửa
   file trong cùng validation nếu chưa có approval mới.

Technical verification là session riêng: restore/build chỉ khi được phép;
run/database cần environment và approval riêng; command status chỉ đổi sau
evidence. Commit/push chỉ thực hiện theo direct instruction.
```

Khi clone project có Framework submodule trên máy khác, dùng `git clone --recurse-submodules [PROJECT_URL]` hoặc chạy `git submodule update --init --recursive` sau clone. Pin hiện hành là dependency cần xác minh; không tự update sang remote latest trong migration.

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
