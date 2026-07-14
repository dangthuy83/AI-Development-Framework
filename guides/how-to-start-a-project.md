# Cách bắt đầu một project

> Guide cho người dùng và AI Agent. Guide giải thích cách dùng package; Standards, Workflows và Project Workspace vẫn là nguồn sở hữu quy tắc và project facts.

## Khi nào dùng

Dùng cho project mới. Với project đã có code, tài liệu hoặc lịch sử, dùng [migration guide](how-to-migrate-an-existing-project.md) trước.

## Chuẩn bị

- Xác định thư mục project và người có quyền phê duyệt Product, Design, dependency và external side effect.
- Đọc [Start Project Checklist](../global-workspace/checklists/start-project.md), [Session Workflow](../global-workspace/workflows/session-workflow.md) và [AI Working Standards](../global-workspace/standards/ai-working.md).
- Chọn Agent theo capability thực tế, không theo tên model. Nếu Agent không sửa file được, dùng chế độ manual copy/review.
- Không đưa credential, token, personal data hoặc secret vào chat, prompt hay template.

## Standard Codex New Project Runbook

Runbook này dành cho người muốn Agent dẫn dắt việc khởi tạo mà không phải tự đọc hoặc tự ghép toàn bộ Standards, Workflow, Template và Checklist trước. Người dùng chỉ cung cấp facts tối thiểu và giữ authority đối với Product, Design, Decision, permission cùng các lựa chọn chưa xác định; Codex chịu trách nhiệm đọc Framework, lộ diện gaps và dừng tại approval gates.

Chuẩn bị input ngắn:

```text
Project path: [PROJECT_PATH]
Framework path: [FRAMEWORK_PATH]
Project name: [NAME]
Problem cần giải quyết: [PROBLEM hoặc chưa xác định]
Primary users: [USERS hoặc chưa xác định]
Có frontend: [có/không/chưa xác định]
Technology stack: [đã xác định/chưa xác định + details]
Project/Product/Design/Decision authority: [name/role]
Documentation write permission: [chưa cấp/có trong exact scope]
Technical command permission: [restore/build/run/test/database boundaries]
```

Copy prompt sau vào Codex đang mở tại root project:

```text
Khởi tạo project mới bằng AI Development Framework.

Project path: [PROJECT_PATH]
Framework path: [FRAMEWORK_PATH]

Thông tin ban đầu:

- Project name: [NAME]
- Problem cần giải quyết: [PROBLEM hoặc chưa xác định]
- Primary users: [USERS hoặc chưa xác định]
- Có frontend: [có/không/chưa xác định]
- Technology stack: [đã xác định/chưa xác định + details]
- Project/Product/Design/Decision authority: [name/role]
- Documentation write permission: [chưa cấp/có trong exact scope]
- Technical command permission: [restore/build/run/test/database boundaries]

Dùng Guided Start Mode. Không yêu cầu người dùng tự đọc hoặc tổng hợp toàn bộ
Framework trước.

PHASE 1 — Guided intake và initialization plan

1. Xác minh project path, Git/filesystem state và Framework dependency.
2. Đọc Start Project Guide, Start Project Prompt Template, AI Working,
   Documentation, Knowledge Management và Security Standards, Session Workflow
   cùng Start Project/Open Session Checklists.
3. Không sửa file hoặc chạy technical command.
4. Từ thông tin ban đầu, lập Session Contract, authority map, confirmed Product
   facts, explicit gaps, proposed nine-file initialization plan, frontend
   applicability và permission/approval gates.
5. Không chọn stack, Product behavior, milestone, Decision hoặc command thay
   owner.
6. Chỉ hỏi những câu blocking chưa thể xác định từ input; hỏi theo nhóm ngắn,
   không yêu cầu người dùng điền toàn bộ template.
7. Dừng để owner review và phê duyệt exact files/actions.

PHASE 2 — Project Workspace initialization

Chỉ chạy sau direct explicit approval.

1. Inventory lại target trước edit.
2. Tạo hoặc hợp nhất đúng chín Project Workspace files: README.md, PRODUCT.md,
   DESIGN.md, ROADMAP.md, DECISIONS.md, WORKING_CONTEXT.md, TASKS.md,
   CHANGELOG.md và AGENTS.md.
3. Chỉ điền confirmed facts có authority/provenance.
4. Fact chưa quyết định phải ghi explicit gap; không dùng code, AI suggestion
   hoặc preference để tự điền.
5. DECISIONS.md không có Accepted Decision nếu chưa có authority.
6. Commands phải là Verified, Unverified hoặc Not configured trung thực.
7. Nếu có frontend, giữ Frontend sections và tách Impeccable policy khỏi
   availability.
8. Không tạo source code, dependency, database, runtime hoặc extra
   documentation file nếu chưa có authorization riêng.
9. Không stage, commit hoặc push.

PHASE 3 — Initialization validation

1. Xác minh 9/9 files, required sections và ownership.
2. Kiểm tra links/anchors, tables/fences, empty files và conflict markers.
3. Kiểm tra Product–Design–Decision boundary.
4. Kiểm tra permission, secret và untrusted-input boundary.
5. Chạy Start Project và Open Session Checklists bằng evidence thật.
6. Báo completed, partial, blocked hoặc failed.
7. Dừng với exact changed files, gaps và recommended next action.

Technical baseline là session riêng. Không chạy restore/build/run/test/database
trong initialization nếu chưa có permission rõ.
```

Runbook là entry guidance cho Codex, không thay [Start Project Prompt Template](../global-workspace/templates/prompts/start-project.md), Session Contract, upstream contracts hoặc owner authority. Project đơn giản vẫn có thể dùng các bước ngắn bên dưới mà không cần runbook đầy đủ.

## Các bước

1. Sao chép đúng chín file từ [`project-template/`](../project-template/README.md) vào root project. Không thêm file bắt buộc mới.
2. Điền `README.md` làm entry/document map; chưa rõ fact nào thì ghi gap, không đoán.
3. Xác nhận `PRODUCT.md`: problem, users, goals, scope, requirements và non-goals đã được owner chấp thuận.
4. Điền `DESIGN.md` từ thiết kế hiện hành hoặc đánh dấu chưa xác định. Không chọn stack thay người dùng.
5. Ghi milestone ở `ROADMAP.md`, actionable work ở `TASKS.md`, current focus ở `WORKING_CONTEXT.md`.
6. Chỉ append project Decision đã được chấp thuận vào `DECISIONS.md`; không dùng Roadmap thay Decision.
7. Cấu hình `AGENTS.md` bằng read order, verified commands, permissions và project rules có provenance.
8. Nếu có frontend, giữ các section conditional trong Product/Design/AGENTS, điền [Frontend Brief](../global-workspace/templates/frontend-brief.md) và xác định Impeccable policy tách biệt availability.
9. Mở session bằng [start-project prompt](../global-workspace/templates/prompts/start-project.md), lập Session Contract: Objective, Scope, Constraints, Deliverables.
10. Chạy Start Project và Open Session Checklists; ghi evidence và status trung thực.

## Ví dụ yêu cầu tối thiểu

> Khởi tạo project tại `[path]` bằng Project Workspace Template. Trước khi sửa, kiểm kê file hiện có. Đọc Start Project Prompt và các Standards/Workflow được tham chiếu. Không phát minh Product Requirement, Design, command hoặc Decision. Báo gap, permission cần thiết, file đã tạo và checklist evidence.

## Gate hoàn thành

`completed` khi đúng chín file tồn tại, ownership/read/update rules hợp lệ, required context có nguồn, permission rõ và checklist Pass. Thiếu Product/Design authority, required source hoặc quyền ghi làm `blocked`; thiếu supporting detail không chặn có thể `partial`. Không tuyên bố build/test pass nếu chưa chạy.

## Tiếp theo

Dùng [guide tiếp tục project](how-to-continue-a-project.md) cho session sau và guide riêng cho [ChatGPT](how-to-use-with-chatgpt.md), [Codex](how-to-use-with-codex.md), [Cline](how-to-use-with-cline.md) hoặc [Claude](how-to-use-with-claude.md).
