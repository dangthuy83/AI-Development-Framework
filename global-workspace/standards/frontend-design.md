# Frontend Design Standards

## Purpose, audience và applicability

Chuẩn có nội dung đầy đủ nhưng `conditional`: áp dụng khi project/task có user-facing UI, design system, presentation hoặc interaction change. Không áp dụng cho backend-only, data-only hoặc document task không có UI. Technology-stack neutral.

## Required reads và ownership

Đọc `PRODUCT.md`, relevant `DESIGN.md`, `DECISIONS.md`, `AGENTS.md`, task/acceptance và design references. Product sở hữu requirement/business logic; Project `DESIGN.md` sở hữu stack, visual direction và project design; Standard này sở hữu baseline dùng chung. Frontend Brief là execution artifact, không thay Project sources.

## Design baseline

- Visual hierarchy thể hiện priority, grouping và primary action rõ.
- Component, typography, color, spacing và interaction nhất quán với project system/reference.
- Responsive behavior xác định content reflow, overflow, touch target và interaction qua viewport applicable.
- Accessibility gồm semantic structure, keyboard, focus, contrast, alternatives và motion preference khi applicable.
- Có loading, empty, error, success, disabled và validation states phù hợp.
- Interaction có affordance, feedback, state transition và error recovery rõ.

## Reference và provenance

Ghi nguồn của requirement, design system, mockup, screenshot hoặc inspiration; phân biệt authoritative reference với inspiration. Không copy asset/style không rõ license hoặc biến inspiration thành Product Requirement.

## Visual QA và evidence

Dùng frontend UI, responsive, accessibility và visual QA checklists tương ứng. Evidence có thể là browser observation, screenshot, viewport/device, keyboard path, automated result hoặc limitation. Không tuyên bố visual/accessibility pass nếu chưa quan sát/kiểm tra.

## Impeccable boundary

Project `DESIGN.md` khai usage policy; `AGENTS.md` khai availability profile và fallback. Dùng Impeccable khi user hoặc policy yêu cầu và capability khả dụng. Impeccable/AI không được thay Product Requirement, business logic, architecture, technology stack hoặc Project Decision. Khi unavailable, dùng cùng brief/standards/checklists; không hạ Acceptance Criteria. Chỉ blocked nếu authority quy định tool là bắt buộc.

## Project extension

Project bổ sung frontend stack, design system, token, browser/device targets, accessibility level, Impeccable profile và stricter QA. Extension không silent override global accessibility/security baseline.

## Completion và blocking failures

Đạt khi applicable requirements có source, core states có thiết kế, responsive/accessibility/visual QA có evidence hoặc limitation đúng status, và không đổi Product/Architecture ngoài scope. Blocking: missing Product behavior, unapproved design/architecture change, critical accessibility failure, required viewport/state chưa kiểm, hoặc required Impeccable unavailable không có policy fallback.

## Dependencies và prohibited content

Phụ thuộc phần 13A, F-018, F-021, AI Working, Testing/Review và Security/Privacy. Không chọn React/Vue/.NET hay stack chung; không chứa project visual direction, business logic, workflow implementation hoặc Runtime.
