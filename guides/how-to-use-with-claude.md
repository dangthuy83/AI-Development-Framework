# Cách sử dụng Framework với Claude

## Chọn Claude Project hay Claude Code

- **Claude Projects:** phù hợp analysis, design, documentation và continuity qua project knowledge/instructions. Project knowledge và instructions có thể dùng xuyên chats; context không mặc nhiên chia sẻ giữa chats nếu chưa nằm trong project knowledge. Xem [What are projects?](https://support.anthropic.com/en/articles/9517075-what-are-projects) và [Create and manage projects](https://support.anthropic.com/en/articles/9519177-how-can-i-create-and-manage-projects).
- **Claude Code:** phù hợp local repository work, file edits, commands và verification. Continuation/permission options phụ thuộc CLI/environment; xem [Claude Code setup](https://docs.anthropic.com/en/docs/claude-code/getting-started) và [CLI reference](https://docs.anthropic.com/en/docs/claude-code/cli-usage).

## Capability profile

| Capability | Projects | Claude Code | Fallback |
|---|---|---|---|
| Project files | Upload/project knowledge | Local accessible workspace | Paste relevant sections hoặc manual patch |
| Durable guidance | Project instructions | Project rule/instruction files available to environment | Direct request + explicit read of `AGENTS.md` |
| Continuation | New chat reads project knowledge, not unsaved chat-only context | Resume/continue may be available | Working Context + Handover is authoritative |
| Verification | Document/manual review unless tools available | Commands/tools within permission | User-run command/static review; no false Pass |
| Mutation | Usually proposed content unless integrated tool | File edits when permitted | Human applies reviewed patch |

## Setup

1. Với Projects, upload chín project files và only relevant Global docs; dùng clear filenames, tránh duplicate version. Project instructions chỉ reference ownership/read rules.
2. Với Claude Code, mở đúng project root, xác nhận accessible directories, permission mode và `AGENTS.md`/project rules. Không dùng bypass-permission mode để né Framework approval boundary.
3. Không upload/prompt secret hoặc sensitive data không cần thiết; kiểm tra sharing/workspace policy.

## Thực hiện

- Dùng Start/Migration/Continue guide và Prompt Template phù hợp.
- Mỗi session xác nhận Objective, Scope, Constraints, Deliverables, source freshness, allowed targets và verification.
- Project knowledge, RAG/retrieval, terminal output và AI output đều là supporting/untrusted input qua trust boundary; source reference vẫn bắt buộc.
- Claude không được phát minh Product/Design/Decision, chọn stack khi chưa có authority hoặc coi chat continuity là SSOT.
- Kết thúc bằng owner updates, Close Session Checklist và Handover.

## Permission, limitation và fallback

External side effect, destructive command, extra directory, dependency hoặc publish/deploy cần explicit authority. Im lặng/timeout không phải approval. Nếu Claude Projects thiếu file mutation/test capability, output proposed diff và verification plan; nếu Claude Code thiếu permission/environment, dùng approved manual fallback. Acceptance Criteria không đổi; required missing verification làm `partial|blocked`.

## Completion

Report surface đã dùng, accessible sources, deliverables, actual checks/evidence, file updates hoặc proposed patch, limitations và status chuẩn. Khi chuyển giữa Projects và Claude Code, dùng Handover/Working Context và đối chiếu filesystem; không dựa vào memory giữa hai surface.
