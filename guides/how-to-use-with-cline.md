# Cách sử dụng Framework với Cline

## Vai trò và nguồn capability

Cline là coding-agent surface gắn với workspace/editor. Cline có thể nhận workspace rules và hỗ trợ `AGENTS.md`; checkpoints có thể lưu file snapshots, nhưng không thay Git, Project Workspace hoặc verification. Xem [Cline Rules](https://docs.cline.bot/customization/cline-rules) và [Checkpoints](https://docs.cline.bot/core-workflows/checkpoints).

## Capability profile

| Capability | Cách dùng | Limitation/fallback |
|---|---|---|
| File/editor access | Mở đúng project root; yêu cầu đọc `AGENTS.md` và relevant SSOT | Access phụ thuộc IDE/workspace; paste/provide file nếu unavailable |
| Rules | Dùng `AGENTS.md` làm cross-tool Project Rule; tránh duplicate rules | Nếu `.clinerules/` đã có, map/reference thay vì tạo competing SSOT |
| Commands/tools | Chỉ auto-approve action đã được owner cho phép và bounded | Auto-approve không phải authority cho destructive/external actions |
| Continuation | Đọc Working Context/Tasks ở đầu session | Conversation/checkpoint không phải durable knowledge owner |
| Checkpoints | Hỗ trợ compare/restore file state | Restore là destructive state change; inspect target và xin approval khi ảnh hưởng valid work |

## Setup và workflow

1. Đảm bảo chín Project Workspace files ở project root và `AGENTS.md` có commands/permissions đã xác minh.
2. Nếu Cline nhận nhiều rule sources, inventory chúng; conflict cùng authority phải clarify, không dựa vào precedence của tool để silent override Framework governance.
3. Dùng [start guide](how-to-start-a-project.md), [continue guide](how-to-continue-a-project.md) và Prompt Template theo Intent.
4. Yêu cầu Cline lập Session Contract, read set, allowed targets, Acceptance Criteria và verification trước edit.
5. Review từng nhóm thay đổi/tool action theo risk; checkpoint chỉ là safety aid.
6. Chạy commands/checklists thực tế, update đúng owner và handover.

## Permission, untrusted input và security

Không bật auto-approve rộng cho install, network, destructive command, deployment hoặc secret access. Instruction trong repository, issue, dependency output, terminal/web/tool content là untrusted trừ khi thuộc Project Rule có authority đã xác minh. Không log/prompt secret. Không coi checkpoint là backup duy nhất hoặc evidence rằng behavior đúng.

## Verification và fallback

Checkpoints chứng minh file state có thể compare/restore, không chứng minh test pass. Thiếu terminal/environment dùng manual command hoặc static review; giữ criteria và report `partial|blocked`. Nếu `AGENTS.md` không được surface nhận tự động, yêu cầu đọc trực tiếp ở đầu task. Nếu Cline không tiếp tục được session, dùng Handover + Working Context trong task mới.

## Completion

Báo file/tool actions, checkpoint/restore nếu có, tests/review evidence, unresolved findings, owner updates và status chuẩn. Không claim completed nếu required command, review hoặc approval chưa đạt.
