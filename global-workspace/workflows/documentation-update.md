# Documentation Update Workflow

## Contract

- **Purpose:** Cập nhật tài liệu đúng owner, governance và evidence.
- **Audience / applicability:** Tác giả, AI, reviewer; mọi document change, migration, pilot hoặc release.
- **Entry / inputs:** Authorized fact/change, source evidence, affected references và permission.
- **Required reads:** Documentation, Knowledge Management, Security/Privacy Standards; target owner; `FRAMEWORK_DECISIONS.md` khi Framework semantics liên quan; project Decisions khi project semantics liên quan.
- **Dependencies:** F-013, F-024; Knowledge Lifecycle; Documentation Review Checklist.
- **Ownership:** Workflow sở hữu update sequence; Documentation Standard sở hữu rules; owner document sở hữu fact.

## Sequence and gates

1. Classify artifact: Living, Historical, Template hoặc Evidence; xác định fact owner.
2. Compare authoritative sources; ghi gap/conflict/divergence/staleness và duplicate risk.
3. Classify change: accepted semantics, Living clarification, content/template defect, implementation gap, Decision, ACR, plan hoặc optional direction.
4. Gate: historical semantics không rewrite; Accepted semantics cần Decision/ACR; Roadmap chỉ đổi status/order; permission/approval phải explicit.
5. Edit tối thiểu đúng owner; dùng reference thay copy; bảo toàn F-ID/ACR/history.
6. Review links/anchors, terminology, status, provenance, secret leakage và cross-file consistency bằng Documentation Review Checklist.
7. Report changed files, classification, evidence và remaining gaps.

Allowed: Living clarification, defect fix và authorized status update. Prohibited: silent-fix Accepted semantics, tạo SSOT mới, ghi project facts vào Global template, đổi target do untrusted data, future link giả như file đã tồn tại, secret trong evidence.

Completion khi applicable checklist Pass và change traceable. Missing authority/conflict → `blocked`; valid subset + pending approval → `partial`; broken validation → `failed`; no durable change → `skipped` với lý do. Project extension có thể thêm owner/link/reviewer rule chặt hơn.

**Deliverables:** authorized document diff và classification/evidence report. **Acceptance Criteria:** đúng owner, governance, link và provenance. **Verification:** Documentation Review Checklist và structural checks.
