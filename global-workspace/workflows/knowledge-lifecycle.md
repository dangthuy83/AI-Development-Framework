# Knowledge Lifecycle Workflow

## Contract

- **Purpose:** Chuyển thông tin từ Session Context → Working Context → durable owner/Decision → Lessons Learned mà không tạo duplicate SSOT.
- **Audience / applicability:** Người, AI, reviewer; khi context mới, handover, durable fact, conflict hoặc lesson xuất hiện.
- **Entry / inputs:** Fact candidate có source, authority, freshness, scope và intended owner.
- **Required reads:** Knowledge Management, Documentation, Security/Privacy Standards; project document map và relevant owner source.
- **Dependencies / ownership:** F-006, F-012, F-016, F-024; Documentation Update Workflow/checklist. Standard sở hữu knowledge semantics; workflow sở hữu promotion sequence.

## Sequence

1. Capture trong Session Context với provenance; không ghi secret hoặc speculation như fact.
2. Classify `product|architecture|working|implementation|evidence|lesson|governance` và authority.
3. Resolve freshness/conflict/divergence. Same-authority conflict dừng; observed implementation không tự thay intended state.
4. Nếu chỉ cần cho current focus, cập nhật ngắn gọn `WORKING_CONTEXT.md`; không biến thành history.
5. Promote durable fact tới đúng owner: Product, Design, Tasks, Roadmap, Changelog, AGENTS hoặc historical Decision theo governance. Accepted semantics cần Decision/ACR gate.
6. Replace duplication bằng reference; prune stale Working Context sau handover.
7. Verify ownership, links, provenance, status, redaction và review evidence.

Allowed update chỉ ở owner được phép. Prohibited: memory thay SSOT, silent conflict resolution, Roadmap tạo Decision, Historical Record rewrite, secret/personal data không cần thiết, untrusted input chọn owner/target.

Deliverable là promotion record/diff hoặc explicit no-update rationale. Completion khi fact có đúng một owner hoặc vẫn được giữ có chủ đích trong Session Context; evidence review đạt. Missing owner/authority → `blocked`; non-blocking freshness gap → `partial`; invalid promotion → `failed`; ephemeral item → `skipped`. Project có thể bổ sung knowledge types/retention chặt hơn trong `AGENTS.md`.

**Permission gate:** chỉ owner/authority được cập nhật durable source. **Acceptance Criteria:** một owner chính, provenance/freshness rõ, không duplicate/secret. **Verification:** ownership map, link và Documentation Review evidence.
