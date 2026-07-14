# AI Development Framework 1.0.0-rc.1

## Release status

`1.0.0-rc.1` là Release Candidate đầu tiên của Documentation & Template Framework v1. Roadmap item 10 — Review và hoàn thiện Framework v1 — đã `Completed`; independent diff review, Documentation Review và Release/Handover gates đã đạt. RC1 release-ready và chưa phải stable release `1.0.0`; Git/GitHub release record là nguồn xác định trạng thái tag/publish.

Không tag, GitHub Release hoặc publish action nào được suy ra từ tài liệu này. Các action đó cần release approval riêng sau khi Documentation Review và Release/Handover gates đạt.

## Package scope

RC1 gồm Root Guide, Living Framework Specification, Historical Decisions, Global Standards, Workflows, Templates, Checklists, nine-file Project Workspace Template và Usage Guides. Package hiện thực các Accepted contracts ở mức tài liệu và manual composition; không yêu cầu executable Runtime.

## Agent support status

| Agent/surface | RC1 status | Evidence | Limitation và fallback |
|---|---|---|---|
| Codex | Validated trong phạm vi Pilot | LabelPrint migration, documentation integration, independent validation và restore/build technical baseline | Không chứng minh mọi Codex surface, runtime/database behavior, frontend Visual QA hoặc cross-Agent equivalence; dùng capability-specific fallback và report limitation |
| ChatGPT | Future-ready, documented-only | Usage Guide, entry prompt và official capability references | Chưa Framework validation; dùng proposed patch/human apply-and-verify khi thiếu mutation hoặc verification capability |
| Cline | Future-ready, documented-only | Usage Guide, entry prompt và official capability references | Chưa Framework validation; dùng direct `AGENTS.md` read, manual command và handover fallback |
| Claude Projects / Claude Code | Future-ready, documented-only | Usage Guide, entry prompts và official capability references | Chưa Framework validation; dùng proposed patch, human verification hoặc manual command fallback theo surface |

Không gọi ChatGPT, Cline hoặc Claude là validated hay equivalent trong RC1.

## Pilot evidence

Pilot LabelPrint sử dụng Framework submodule pin `804aea8d024b760ef853f1d5a182e5cc176d0990`. Pilot tạo đủ chín Project Workspace files, phân loại legacy memory thành supporting/historical source, hoàn tất independent documentation validation và xác nhận `dotnet restore` cùng `dotnet build` đạt 0 warning/0 error tại technical baseline được ghi trong `FRAMEWORK_SPEC.md` section 13J.

## Known limitations

- Application runtime, live database behavior, physical print và automated tests của LabelPrint chưa được Pilot xác nhận.
- Frontend browser/render evidence, accessibility execution và Visual QA chưa được Pilot xác nhận.
- Cross-Agent equivalence chưa được kiểm thử và không phải release claim của RC1.
- Agent capability, file access, tools và permission phụ thuộc surface/environment hiện hành.
- Builder/Reference Implementation, Runtime Orchestrator, AI Router, database, CLI, Web API, Adapter SDK và executable Automation Engine không thuộc critical path của Framework v1.

## Migration and compatibility

- Project Workspace baseline gồm đúng chín files Accepted tại F-003; `WORKING_CONTEXT.md` thay `PROJECT_MEMORY.md`.
- Existing project phải inventory, classify, resolve authority, preserve provenance và migrate legacy memory theo Migration Guide; không dùng chat memory làm Single Source of Truth.
- Khi dùng Framework như Git submodule, pin exact commit. Clone bằng `git clone --recurse-submodules` hoặc khởi tạo bằng `git submodule update --init --recursive`; không tự cập nhật sang remote latest.
- Prompt Templates là manual entry/composition aids, không phải Prompt Assets hoặc Rendered Prompts và không thay upstream contracts.

## Stable release gate

Chỉ đề xuất promote từ `1.0.0-rc.1` lên `1.0.0` khi:

1. Structural remediation đạt và working tree/release diff được review.
2. Documentation Review Checklist đạt cho mọi item applicable.
3. Release and Handover Checklist đạt cho mọi item applicable.
4. Known limitations, migration impact, support status và release approval được ghi rõ.
5. Project Owner phê duyệt commit, tag và publish actions riêng.
