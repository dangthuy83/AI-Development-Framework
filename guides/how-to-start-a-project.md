# Cách bắt đầu một project

> Guide cho người dùng và AI Agent. Guide giải thích cách dùng package; Standards, Workflows và Project Workspace vẫn là nguồn sở hữu quy tắc và project facts.

## Khi nào dùng

Dùng cho project mới. Với project đã có code, tài liệu hoặc lịch sử, dùng [migration guide](how-to-migrate-an-existing-project.md) trước.

## Chuẩn bị

- Xác định thư mục project và người có quyền phê duyệt Product, Design, dependency và external side effect.
- Đọc [Start Project Checklist](../global-workspace/checklists/start-project.md), [Session Workflow](../global-workspace/workflows/session-workflow.md) và [AI Working Standards](../global-workspace/standards/ai-working.md).
- Chọn Agent theo capability thực tế, không theo tên model. Nếu Agent không sửa file được, dùng chế độ manual copy/review.
- Không đưa credential, token, personal data hoặc secret vào chat, prompt hay template.

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
