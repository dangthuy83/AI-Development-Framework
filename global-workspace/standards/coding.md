# Coding Standards

## Purpose, audience và applicability

Chuẩn `required`, technology-stack neutral cho task tạo, sửa, refactor, review hoặc kiểm chứng code. Áp dụng cho người, AI Agent và reviewer; đọc cùng Project Rules trước thay đổi code.

## Global baseline và Project Rule

Global baseline yêu cầu: thay đổi bounded và traceable; giữ behavior ngoài scope; tuân current Product/Design/Decisions; xử lý input/error/resource rõ; không để secret; cập nhật documentation khi owner fact thay đổi; verification tương xứng rủi ro. Project `AGENTS.md`, `DESIGN.md` hoặc rule có provenance xác định language/framework, structure, naming, dependency boundary và commands.

Project Rule không chứa Product Requirement/business logic mới, không silent override Global rule và không thay Architecture/Decision. Khi rule conflict, ghi source, authority, scope và dừng theo governance.

## Applicability, enforcement và provenance

Mỗi rule được áp dụng phải nêu scope/condition, enforcement (`mandatory`, `approval_required`, `advisory`) và source. Chỉ dùng rule phù hợp artifact, Intent và project stack. Obligation không có provenance không được biến thành requirement.

## Implementation baseline

- Hiểu behavior và boundary trước edit; không mở rộng scope.
- Ưu tiên thay đổi nhỏ, cohesive, dễ review; tránh duplicate logic và dependency không cần thiết.
- Bảo toàn compatibility trừ khi breaking change được chấp thuận.
- Xử lý lỗi, validation, resource lifecycle và concurrency theo risk/project rule.
- Code và comment phản ánh intent; không ghi secret, personal data hoặc untrusted payload vào log.
- Không đổi architecture, data contract hay security boundary khi chưa có authority.

## Exception và override boundary

Exception phải có rule ref, scope, reason, approver/decision, thời hạn khi temporary, compensating control và verification. Locked safety/security/access baseline không được override. Thay Accepted semantics cần ACR; lựa chọn project architecture mới có thể cần Project Decision.

## Verification mapping

Map obligation sang phương thức trung lập: formatter, lint, compiler/build, static analysis, unit/integration test, security scan, runtime check hoặc manual review. Tool cụ thể thuộc Project/Environment profile. Không có capability thì ghi limitation và dùng alternative đã được chấp thuận; không tuyên bố pass khi chưa chạy.

## Review và evidence

Dùng `../checklists/code-review.md` khi applicable. Evidence gồm diff, rule/source refs, command và kết quả, test scope, manual observation hoặc limitation. Coding Standard không tự chạy verification hoặc tự tạo Acceptance Criteria.

## Completion và blocking failures

Đạt khi applicable rules xác định, conflicts resolved, change đúng scope, required verification có evidence, regression/doc/security impact được review. Blocking gồm mandatory conflict, missing required Product/Design context, unapproved exception, secret leakage, required verification không có alternative hoặc breaking change chưa được chấp thuận.

## Project extension và prohibited content

Project được bổ sung stack/version, source structure, naming, tool mapping và stricter rules có provenance. Chuẩn này không chứa Product Requirement, business logic, project architecture, schema rule contract bắt buộc, Constraint Engine, Runtime, CLI hay Web API. F-021 được hiện thực ở mức hướng dẫn và template; Coding Rule schema/executable engine không phải điều kiện Framework v1.

## Dependencies

Phụ thuộc F-017, F-021, F-024, Testing/Review và Security/Privacy Standards.
