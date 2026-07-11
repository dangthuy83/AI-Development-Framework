# Release and Handover Checklist

**Applicability:** Required cho release, pilot handover hoặc ownership transfer. **Trigger:** Trước công bố/chuyển giao. **Owner:** Release/handover owner.

| Status | Item | Evidence | Blocking | Owner source |
|---|---|---|---|---|
| Pass / Fail / Not applicable | Scope/version/artifacts và recipient/owner rõ. | Manifest/handover note | Yes | AI Working; Documentation |
| Pass / Fail / Not applicable | Required criteria, verification và regression review đạt. | Evidence refs | Yes | Testing/Review |
| Pass / Fail / Not applicable | Changelog/docs phản ánh verified outcome, known limitations và migration impact. | Diff/link review | Yes | Documentation |
| Pass / Fail / Not applicable | Permission/approval cho publish, deploy hoặc transfer còn hiệu lực. | Approval ref | Yes | Security/Privacy |
| Pass / Fail / Not applicable | Secret, sensitive data, access và external dependency được xử lý an toàn. | Security review | Yes | Security/Privacy |
| Pass / Fail / Not applicable | Blockers, rollback/fallback, next owner và support path được ghi. | Handover record | Yes | AI Working |

**Completion rule:** Không release/handover với blocking Fail. Not applicable cần lý do; limitation non-blocking phải được recipient thấy. Workflow owner cho handover: [Session Workflow](../workflows/session-workflow.md); Standard owners: [AI Working](../standards/ai-working.md) và [Testing/Review](../standards/testing-and-review.md). Release-specific sequence vẫn được điều phối theo project rules và authorized release plan.
