# Knowledge Management Standards

## Purpose, audience và applicability

Chuẩn `required` này quản trị authority, Context Selection, promotion và lifecycle của tri thức. Đọc khi initialize, continue, analyze, document, migration hoặc khi có conflict/gap/staleness.

## Năm memory layers

1. Global Knowledge: chuẩn dùng chung.
2. Project Knowledge: Product, Design, Decisions và nguồn bền vững của project.
3. Working Context: RAM ngắn hạn cho focus, blocker và next action.
4. Session Context: dữ liệu tạm của execution hiện tại.
5. Lessons Learned: tri thức đã kiểm chứng, có owner và provenance; Framework v1 không bắt buộc file Lessons Learned mới.

## Taxonomy và authority

- `governance`: platform policy, Accepted Decision, Global Standard hoặc Project Rule phù hợp.
- `product`: `PRODUCT.md`.
- `architecture`: `DESIGN.md`; rationale tại `DECISIONS.md`.
- `working`: `WORKING_CONTEXT.md`, `TASKS.md`.
- `implementation`: source code và configuration.
- `evidence`: tests, logs, runtime/manual evidence.
- `lessons`: nguồn lesson có ownership và provenance.

Authority phụ thuộc câu hỏi. Code không tự thay Product; Roadmap không xác lập Decision; evidence không tự thay intended state.

## Context Selection theo Intent

Với từng Intent, xác định information requirement và chọn nguồn `required`, `supporting` hoặc `optional`. Load scope là `metadata_only`, `relevant_sections` hoặc `full_source`; mặc định dùng `relevant_sections`. Thiếu nguồn required làm context `blocked`; supporting gap chỉ cho phép `partial` khi không làm sai Intent.

Mỗi resolved fact quan trọng phải có source reference. Chỉ hỏi người dùng sau khi đã kiểm tra nguồn có thể truy cập trong phạm vi cho phép.

## Knowledge Lifecycle và promotion gate

`Session Context → Working Context → Project Knowledge hoặc Decision → Lessons Learned`.

Không phải mọi fact đều được promote. Trước promotion phải xác định type, authority, verification, provenance, destination owner, duplicate, conflict, approval và security. Fact chưa đạt gate giữ temporary và `unverified`, yêu cầu làm rõ hoặc loại bỏ khi hết giá trị.

## Provenance, quality và conflict handling

Ghi source, section/artifact, version hoặc timestamp khi relevant, transformation và verification. Conflict cùng authority không được tự resolve. Gap phải phân loại blocking. Divergence giữ riêng intended/implemented/observed. Staleness phải xác minh bằng nội dung và authority. Deduplication giữ full content ở owner và dùng reference ở nơi khác.

## AI memory và chat summary boundary

AI memory, conversation history và chat summary là supporting hoặc historical input, không phải authority. Phải kiểm chứng với SSOT trước khi dùng làm fact hoặc cập nhật project.

## Working Context boundary

`WORKING_CONTEXT.md` chỉ giữ current objective, active scope, confirmed continuation facts, blocker, next action và source links. Promote durable fact về owner, chuyển notable completed outcome sang Changelog và prune lịch sử không còn cần.

## Project extension và review gate

Project được khai báo source/type/owner/read rule riêng nhưng không silent override authority chuẩn. Review phải kiểm tra taxonomy, owner, provenance, promotion, duplicate, conflict, staleness, secret leakage và Working Context bloat. Extension ảnh hưởng Accepted ownership cần governance phù hợp.

## Evidence, completion và prohibited content

Evidence gồm source refs, verification result và promotion decision. Hoàn thành khi required context đủ, facts truy vết được, lifecycle đúng owner, conflicts/gaps không bị che giấu và security đạt. Không yêu cầu database, vector store, Runtime catalog, automatic promotion engine; không chứa Product/Design facts cụ thể hay workflow execution chi tiết.

## Dependencies

Phụ thuộc Documentation Standards, F-004 đến F-006, F-012, F-016 và F-024.
