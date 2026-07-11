# Close Session Checklist

**Applicability:** Required khi kết thúc, pause hoặc handover session. **Trigger:** Trước final completion report. **Owner:** Người/AI thực hiện.

| Status | Item | Evidence | Blocking | Owner source |
|---|---|---|---|---|
| Pass / Fail / Not applicable | Deliverables được đối chiếu Acceptance Criteria. | Result matrix | Yes cho `completed` | Testing/Review |
| Pass / Fail / Not applicable | Verification thực tế và limitation/skipped checks được ghi trung thực. | Test/review output | Yes cho `completed` | Testing/Review |
| Pass / Fail / Not applicable | Tài liệu chỉ cập nhật đúng owner; durable facts promoted, Working Context pruned. | Diff/source refs | Yes nếu state thay đổi | Documentation; Knowledge Management |
| Pass / Fail / Not applicable | Blocker, partial result và next action rõ; valid outputs được giữ. | Handover note | Yes | AI Working; Knowledge Management |
| Pass / Fail / Not applicable | Không secret/sensitive data trong report/evidence. | Redaction review | Yes | Security/Privacy |
| Pass / Fail / Not applicable | Status là completed/partial/blocked/failed/skipped và phù hợp evidence. | Final report | Yes | AI Working; Testing/Review |

**Completion rule:** Close/handover hoàn tất khi mọi item applicable Pass; Fail bắt buộc làm status không được `completed`. Workflow owner: [Session Workflow](../workflows/session-workflow.md).
