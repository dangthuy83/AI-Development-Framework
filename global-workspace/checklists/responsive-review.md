# Responsive Review Checklist

**Applicability:** Conditional cho UI dùng nhiều viewport/device hoặc có responsive requirement. **Trigger:** Khi UI chạy được. **Owner:** Implementer/reviewer.

| Status | Item | Evidence | Blocking | Owner source |
|---|---|---|---|---|
| Pass / Fail / Not applicable | Viewports/containers đại diện được chọn từ Project Design/criteria. | Target list | Yes | Frontend Design |
| Pass / Fail / Not applicable | Không unintended overflow, clipping, overlap hoặc unreadable reflow. | Screenshot/observation | Yes | Frontend Design |
| Pass / Fail / Not applicable | Navigation, forms, dialogs và primary actions vẫn usable. | Interaction evidence | Yes | Frontend Design |
| Pass / Fail / Not applicable | Touch targets, content priority và orientation/zoom behavior phù hợp. | Manual review | Yes nếu applicable | Frontend Design |
| Pass / Fail / Not applicable | Deviations có source, impact và follow-up; không chỉ tối ưu một viewport. | Finding record | Yes nếu criterion violated | Frontend Design; Testing/Review |

**Completion rule:** Tất cả target applicable Pass hoặc deviation được authority chấp thuận. Thiếu browser/device capability phải báo limitation, không ghi Pass. Owners: [Frontend Design Standards](../standards/frontend-design.md) và [Frontend Design Workflow](../workflows/frontend-design.md).
