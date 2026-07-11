# Testing and Review Standards

## Purpose, audience và applicability

Chuẩn `required` cho quality gate và evidence của implement, fix, refactor, review, test, document và release. Project bổ sung verification mapping/tool profile nhưng không làm yếu gate.

## Ba khái niệm

- **Acceptance Criterion**: điều kiện observable để deliverable được coi là đạt.
- **Verification Requirement**: phương thức và phạm vi kiểm tra criterion.
- **Evidence**: kết quả thực tế, thời điểm, environment/capability và artifact ref của lần kiểm.

## Verification modes

Automated test kiểm tra có thể lặp lại; manual review dùng judgment có checklist; Self Review là kiểm tra của tác giả; user confirmation xác nhận requirement/experience thuộc authority người dùng. Chúng không mặc nhiên thay thế nhau.

## Risk-based verification

Xét impact, likelihood, reversibility, security/privacy, data loss, compatibility, user reach và novelty. Rủi ro cao cần phạm vi test/reviewer/evidence mạnh hơn. Mọi code change phải cân nhắc regression ở behavior liên quan; document change phải review link, ownership và semantics; UI change cân nhắc responsive, accessibility và visual QA.

## Review conduct

Review theo requirement và applicable rule, không theo sở thích cá nhân. Findings nêu severity, evidence, impact và owner; phân biệt defect, risk, question và suggestion. Coding ownership ở Coding Standards; Product acceptance ở `PRODUCT.md`/task authority; AI Self Review ở AI Working Standards.

## Honest limitation reporting

Không tuyên bố test/build/runtime/visual/accessibility pass nếu chưa chạy hoặc không có evidence. Missing capability phải nêu checks skipped, impact và alternative/follow-up. `Not applicable` cần lý do, không dùng để né gate.

## Completion gate

`completed` chỉ khi required deliverables, criteria và verification đạt. Verification bắt buộc thiếu capability làm `partial` hoặc `blocked`, trừ alternative đã được authority chấp thuận. Giữ kết quả hợp lệ và báo failed/skipped IDs khi applicable.

## Evidence requirements

Evidence tối thiểu: criterion hoặc checklist item, method, scope, result, timestamp/run context và limitation. Không lưu secret hoặc raw sensitive payload. Manual evidence có thể là note, screenshot hoặc review record có provenance.

## Project extension, dependencies và prohibited content

Project định nghĩa commands, environments, test levels, reviewer requirement và release threshold. Chuẩn phụ thuộc AI Working, Coding, Documentation và Security/Privacy. Không thay Coding rules, Product Acceptance, architecture, stack; không yêu cầu test Runtime hoặc tool cụ thể.

## Blocking failures và completion

Blocking: criterion mơ hồ với deliverable bắt buộc, required verification chưa chạy, evidence không truy vết, critical regression/security finding, hoặc pass claim sai. Chuẩn đạt khi risk được đánh giá, methods đúng loại, evidence trung thực và completion status phản ánh kết quả.
