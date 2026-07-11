# Visual QA Checklist

**Applicability:** Conditional khi có design reference, new UI, redesign/restyle hoặc UI polish. **Trigger:** UI render được ở target state. **Owner:** Implementer/reviewer.

| Status | Item | Evidence | Blocking | Owner source |
|---|---|---|---|---|
| Pass / Fail / Not applicable | Reference authoritative/inspiration và provenance được xác định. | Reference links | Yes | Frontend Design |
| Pass / Fail / Not applicable | So sánh layout, hierarchy, spacing, typography, color và assets ở states/viewport applicable. | Screenshots/comparison | Yes nếu acceptance criterion | Frontend Design |
| Pass / Fail / Not applicable | Loading/empty/error/success và interaction states không có visual regression. | State captures | Yes nếu applicable | Frontend Design |
| Pass / Fail / Not applicable | Deviation được ghi với impact và disposition; không đổi Product/Architecture để khớp hình. | Finding record | Yes nếu unauthorized | Frontend Design |
| Pass / Fail / Not applicable | Capability, environment và timestamp của observation rõ; không giả lập evidence. | QA note | Yes | Testing/Review |

**Completion rule:** Mọi blocking deviation resolved hoặc approved; missing visual capability làm partial/blocked theo contract, không Pass. Owners: [Frontend Design Standards](../standards/frontend-design.md) và [Frontend Design Workflow](../workflows/frontend-design.md).
