# Frontend UI Review Checklist

**Applicability:** Conditional khi UI/presentation/interaction thay đổi. **Trigger:** Sau implementation, trước completion. **Owner:** Implementer/reviewer.

| Status | Item | Evidence | Blocking | Owner source |
|---|---|---|---|---|
| Pass / Fail / Not applicable | UI khớp Product behavior, Frontend Brief và Project Design; không đổi business logic ngoài scope. | Source refs + observation | Yes | Frontend Design |
| Pass / Fail / Not applicable | Hierarchy, typography, spacing, color và components nhất quán. | Screenshot/review note | Yes nếu criterion | Frontend Design |
| Pass / Fail / Not applicable | Loading, empty, error, success, disabled và validation states applicable được xử lý. | State evidence | Yes nếu required state | Frontend Design |
| Pass / Fail / Not applicable | Interaction feedback, affordance và recovery rõ. | Manual observation | Yes nếu critical flow | Frontend Design |
| Pass / Fail / Not applicable | Responsive, accessibility và Visual QA checklists được kích hoạt khi applicable. | Checklist refs | Yes | Frontend Design; Testing/Review |
| Pass / Fail / Not applicable | Impeccable policy/availability/fallback được tuân thủ, không hạ criteria. | Profile/result note | Yes nếu required by policy | Frontend Design |

**Completion rule:** Blocking item Pass; N/A có lý do. Không tuyên bố UI review nếu chưa quan sát. Workflow owner: [Frontend Design Workflow](../workflows/frontend-design.md); Standard owner: [Frontend Design Standards](../standards/frontend-design.md).
