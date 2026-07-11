# Documentation Review Checklist

**Applicability:** Required cho documentation update, pilot review hoặc release. **Trigger:** Sau edit, trước merge/handover/release. **Owner:** Tác giả hoặc reviewer độc lập khi required.

| Status | Item | Evidence | Blocking | Owner source |
|---|---|---|---|---|
| Pass / Fail / Not applicable | Fact nằm đúng owner; Living/Historical/Template/Evidence không bị trộn. | Diff + source map | Yes | Documentation Standards |
| Pass / Fail / Not applicable | Accepted semantics không bị silent-fix; Decision/ACR gate đúng. | Decision refs | Yes | Documentation Standards |
| Pass / Fail / Not applicable | Duplicate được loại bằng reference; migration/provenance được bảo toàn. | Search/mapping | Yes nếu duplicate SSOT | Documentation; Knowledge Management |
| Pass / Fail / Not applicable | Internal links/anchors, terminology, status và metadata hợp lệ. | Link/lint output | Yes nếu critical link | Documentation Standards |
| Pass / Fail / Not applicable | Conflict, gap, divergence và staleness không bị che giấu. | Review note | Yes nếu blocking gap | Documentation; Knowledge Management |
| Pass / Fail / Not applicable | Không secret/personal data không cần thiết; evidence đã redaction. | Security review | Yes | Security/Privacy |

**Completion rule:** Tất cả applicable item Pass; Not applicable có lý do; findings non-blocking có owner/follow-up. Workflow owner: [Documentation Update Workflow](../workflows/documentation-update.md); Standard owner: [Documentation Standards](../standards/documentation.md).
