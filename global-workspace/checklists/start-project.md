# Start Project Checklist

**Applicability:** Required khi initialize project mới hoặc hoàn tất migration. **Trigger:** Trước khi bắt đầu delivery. **Owner:** Project owner/người hoặc AI được ủy quyền.

| Status | Item | Evidence | Blocking | Owner source |
|---|---|---|---|---|
| Pass / Fail / Not applicable | Có đúng chín Project Workspace files; N/A không hợp lệ cho file bắt buộc. | File inventory | Yes | F-003, F-024 |
| Pass / Fail / Not applicable | `README.md` link đủ document map và có review metadata. | Link check/review field | Yes | Documentation Standards |
| Pass / Fail / Not applicable | Product scope, current Design và governance source được xác định; gap được đánh dấu. | Source refs | Yes nếu thiếu nguồn chính | Knowledge Management Standards |
| Pass / Fail / Not applicable | `AGENTS.md` có read guidance, permission, verified command/fallback và untrusted-data boundary. | Review note | Yes | AI Working; Security/Privacy |
| Pass / Fail / Not applicable | Frontend applicability được xác định; nếu có, Frontend sections/anchors và Impeccable policy/profile nhất quán. | Anchor/policy check | Yes khi frontend | Frontend Design |
| Pass / Fail / Not applicable | Initial Roadmap/Tasks/Working Context không phát minh Decision hoặc trộn history. | Cross-file review | Yes | Documentation Standards |

**Completion rule:** Tất cả item applicable là Pass; mọi Not applicable có lý do. Không tuyên bố initialized nếu blocking item Fail. Workflow owner: [Session Workflow](../workflows/session-workflow.md); thực hiện cùng [AI Working Standards](../standards/ai-working.md).
