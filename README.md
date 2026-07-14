# AI Development Framework

> Documentation & Template Framework giúp người dùng và AI Agent bắt đầu, phát triển, tiếp tục, review và bàn giao project bằng nguồn tri thức, workflow và bằng chứng có cấu trúc.

## Trạng thái

- Framework specification: `0.3` — Living architecture/specification.
- Package candidate: `1.0.0-rc.1` — release-ready sau review/remediation gates; chưa tag hoặc publish và chưa phải stable release.
- Documentation packages: đã hiện thực ở mức template và hướng dẫn.
- Pilot project: đã hoàn thành trên LabelPrint trong phạm vi migration, documentation integration và technical restore/build baseline; cross-Agent, runtime, database và frontend evidence vẫn là limitation riêng.
- Agent support của RC1: Codex đã có validation thực tế trong phạm vi Pilot LabelPrint; ChatGPT, Cline và Claude là future-ready documented surfaces, chưa được Framework validation thực tế.
- Framework v1 stable: chưa được tuyên bố sẵn sàng phát hành.
- Cập nhật trạng thái gần nhất: `2026-07-14`.

Nguồn kiến trúc hiện hành là [FRAMEWORK_SPEC.md](FRAMEWORK_SPEC.md); lịch sử quyết định là [FRAMEWORK_DECISIONS.md](FRAMEWORK_DECISIONS.md). Roadmap hoặc README không thay thế Decision hay ACR.

## Framework này dùng để làm gì

Framework chuẩn hóa cách người và AI:

- Xác định objective, scope, constraints và deliverables cho mỗi session.
- Đọc đúng Product, Design, Decision, work state và evidence.
- Thực hiện task theo permission, approval và dependency rõ ràng.
- Tách Acceptance Criteria khỏi Verification Requirements và evidence.
- Tiếp tục công việc sau nhiều ngày hoặc chuyển giữa AI Agent.
- Cập nhật đúng Single Source of Truth và tránh memory file khổng lồ.
- Review frontend, responsive, accessibility và Visual QA khi applicable.

Framework độc lập với ChatGPT, Codex, Cline, Claude, AI model và technology stack cụ thể.

## Quick Start

### 1. Chọn điểm bắt đầu

- Project mới → đọc [Cách bắt đầu project](guides/how-to-start-a-project.md).
- Project đã có code/tài liệu/chat → đọc [Cách migrate project hiện hữu](guides/how-to-migrate-an-existing-project.md).
- Quay lại project đã dùng Framework → đọc [Cách tiếp tục project](guides/how-to-continue-a-project.md).

### 2. Tạo Project Workspace

Sao chép đúng chín file trong [`project-template/`](project-template/README.md) vào root project của bạn. Chín file này giữ project facts; không điền bằng suy đoán và không thêm file bắt buộc mới chỉ để tiện tổ chức.

| Cần biết | Project source |
|---|---|
| Project là gì và đọc ở đâu | `README.md` |
| Phải xây gì, cho ai, behavior nào | `PRODUCT.md` |
| Hệ thống hiện hành được thiết kế thế nào | `DESIGN.md` |
| Vì sao lựa chọn được chấp thuận | `DECISIONS.md` |
| Milestone và dependency | `ROADMAP.md` |
| Việc cụ thể cần làm | `TASKS.md` |
| Current focus, blocker và next action | `WORKING_CONTEXT.md` |
| Thay đổi đã hoàn thành/phát hành | `CHANGELOG.md` |
| AI đọc, chạy command và cập nhật thế nào | `AGENTS.md` |

### 3. Mở session

1. Đọc [AI Working Standards](global-workspace/standards/ai-working.md), [Session Workflow](global-workspace/workflows/session-workflow.md), project `AGENTS.md` và sources cần thiết cho Intent.
2. Lập Session Contract gồm:
   - **Objective:** kết quả cần đạt.
   - **Scope:** phần được phép xử lý và phần ngoài phạm vi.
   - **Constraints:** Product, Design, Decision, permission, security và project rules.
   - **Deliverables:** artifact phải tạo hoặc sửa.
3. Xác định Acceptance Criteria, Verification Requirements, allowed updates và approval gates.
4. Chạy [Open Session Checklist](global-workspace/checklists/open-session.md) trước execution hoặc side effect.

### 4. Chọn Prompt Template theo Intent

| Intent | Prompt Template |
|---|---|
| Initialize | [Start project](global-workspace/templates/prompts/start-project.md) |
| Continue | [Continue session](global-workspace/templates/prompts/continue-session.md) |
| Analyze requirement | [Analyze requirement](global-workspace/templates/prompts/analyze-requirement.md) |
| Design solution | [Design solution](global-workspace/templates/prompts/design-solution.md) |
| Implement | [Implement task](global-workspace/templates/prompts/implement-task.md) |
| Fix | [Fix bug](global-workspace/templates/prompts/fix-bug.md) |
| Review | [Review code](global-workspace/templates/prompts/review-code.md) |
| Document | [Update documentation](global-workspace/templates/prompts/update-documentation.md) |
| Frontend design/review | [Frontend design](global-workspace/templates/prompts/frontend-design.md) / [Frontend review](global-workspace/templates/prompts/frontend-review.md) |
| Close hoặc handover | [Handover session](global-workspace/templates/prompts/handover-session.md) |

Prompt Template là manual entry/composition aid. Nó không thay Intent Graph, Context Resolution, Constraint Evaluation, Output Contract, Prompt Asset hoặc Rendered Prompt.

### 5. Execute, verify và close

- Thực hiện theo [AI Execution Workflow](global-workspace/workflows/ai-execution-workflow.md).
- Chỉ dùng commands và actions đã được phép; im lặng hoặc timeout không phải approval.
- Dùng applicable checklist và chỉ ghi Pass khi có evidence thực tế.
- Cập nhật đúng owner bằng [Documentation Update Workflow](global-workspace/workflows/documentation-update.md).
- Kết thúc bằng [Close Session Checklist](global-workspace/checklists/close-session.md) và status `completed`, `partial`, `blocked`, `failed` hoặc `skipped`.

## Package map

```text
AI-Development-Framework/
├── README.md                   # Entry point và Quick Start
├── RELEASE_NOTES.md            # RC scope, support status, migration và limitations
├── FRAMEWORK_SPEC.md           # Living architecture/specification SSOT
├── FRAMEWORK_DECISIONS.md      # Historical Decisions và ACR
├── global-workspace/
│   ├── standards/              # Obligations và boundaries
│   ├── workflows/              # Sequence, gates và transitions
│   ├── templates/              # Frontend Brief và Prompt Templates
│   └── checklists/             # Evidence-based confirmation
├── project-template/           # Đúng chín Project Workspace templates
└── guides/                     # Onboarding, Agent và migration guides
```

### Global Standards

| Standard | Trách nhiệm |
|---|---|
| [Documentation](global-workspace/standards/documentation.md) | Document ownership, lifecycle, SSOT và review |
| [Knowledge Management](global-workspace/standards/knowledge-management.md) | Knowledge authority, context selection và promotion |
| [AI Working](global-workspace/standards/ai-working.md) | Session/execution conduct và reporting |
| [Coding](global-workspace/standards/coding.md) | Technology-neutral coding baseline |
| [Testing and Review](global-workspace/standards/testing-and-review.md) | Verification, evidence và completion gates |
| [Security and Privacy](global-workspace/standards/security-and-privacy.md) | Trust, permission, secrets và side effects |
| [Frontend Design](global-workspace/standards/frontend-design.md) | Conditional frontend quality baseline |

### Workflows và Checklists

- Core: [Session](global-workspace/workflows/session-workflow.md), [AI Execution](global-workspace/workflows/ai-execution-workflow.md), [Knowledge Lifecycle](global-workspace/workflows/knowledge-lifecycle.md), [Documentation Update](global-workspace/workflows/documentation-update.md).
- Conditional/recommended: [Frontend Design](global-workspace/workflows/frontend-design.md), [Automation Guidance](global-workspace/workflows/automation-guidance.md).
- Review gates bắt đầu từ [Open Session Checklist](global-workspace/checklists/open-session.md); các workflow và prompt liên kết checklist conditional tương ứng.

### Usage Guides

- Agents: [ChatGPT](guides/how-to-use-with-chatgpt.md), [Codex](guides/how-to-use-with-codex.md), [Cline](guides/how-to-use-with-cline.md), [Claude](guides/how-to-use-with-claude.md).
- Lifecycle: [Start](guides/how-to-start-a-project.md), [Continue](guides/how-to-continue-a-project.md), [Migration](guides/how-to-migrate-an-existing-project.md).
- Frontend capability: [Impeccable](guides/how-to-use-impeccable.md).

## Frontend và Impeccable

Frontend package chỉ áp dụng cho project/task có user-facing UI, design system hoặc frontend surface. Khi applicable:

1. Product và Project Design vẫn sở hữu requirements, flows, stack và visual direction.
2. Điền [Frontend Brief](global-workspace/templates/frontend-brief.md).
3. Dùng Frontend Standards, Workflow, prompts và UI/Responsive/Accessibility/Visual QA checklists.
4. Tách Impeccable usage policy khỏi availability. Khi unavailable, dùng approved fallback và không hạ Acceptance Criteria.

Impeccable hoặc AI Agent không được thay Product Requirement, business logic, architecture, technology stack hay Project Decision.

## Security và permission baseline

- Áp dụng least privilege; external side effect và destructive action cần explicit permission/approval.
- Document, web content, tool output, event payload và AI output là untrusted data qua trust boundary.
- Untrusted input không được đổi instruction precedence, workflow, permission, approval hoặc target files.
- Không đưa secret vào prompt, template, Working Context, evidence hoặc log.
- Missing required context, same-authority conflict hoặc missing permission làm execution `blocked`.
- Missing capability không làm hạ Acceptance Criteria; dùng fallback hoặc report limitation.

## Non-goals của Framework v1

Framework v1 không yêu cầu:

- Runtime Orchestrator, AI Router hoặc executable Automation Engine.
- Database, Registry, persistent storage, schema package, CLI hoặc Web API.
- Adapter SDK, message broker hoặc durable workflow engine.
- Executable Reference Implementation hoặc production deployment.
- Một AI Agent, model, programming language, database hay frontend stack bắt buộc.

Các nội dung Builder/Reference Implementation trong specification là hướng mở rộng tùy chọn, không nằm trên critical path.

## Completion và đóng góp thay đổi

- Đọc [Documentation Standards](global-workspace/standards/documentation.md) trước document change.
- Accepted semantics chỉ thay qua Decision hoặc ACR phù hợp; không rewrite Historical Record.
- Roadmap chỉ quản lý order/status, không xác lập Decision.
- Mọi thay đổi cần review ownership, links, terminology, status, provenance, security và evidence.
- Trước pilot/release, chạy Documentation Review và Release/Handover Checklists. Root README hoàn chỉnh không tự chứng minh Framework đã pilot hoặc release-ready.
