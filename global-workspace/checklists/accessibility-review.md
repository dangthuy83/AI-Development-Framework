# Accessibility Review Checklist

**Applicability:** Conditional nhưng bắt buộc khi project có user-facing UI. **Trigger:** Sau UI implementation và trước release/completion tương ứng. **Owner:** Implementer/reviewer có capability phù hợp.

| Status | Item | Evidence | Blocking | Owner source |
|---|---|---|---|---|
| Pass / Fail / Not applicable | Semantic structure, labels, names/roles/values và alternatives phù hợp. | DOM/manual/tool evidence | Yes cho critical flow | Frontend Design |
| Pass / Fail / Not applicable | Keyboard path, focus order/visibility và focus management hoạt động. | Keyboard observation | Yes | Frontend Design |
| Pass / Fail / Not applicable | Contrast, non-color cues, zoom/reflow và readable states đạt project requirement. | Measurement/observation | Yes | Frontend Design; Testing/Review |
| Pass / Fail / Not applicable | Error, status và dynamic update được truyền đạt; motion preference được tôn trọng khi applicable. | State review | Yes nếu applicable | Frontend Design |
| Pass / Fail / Not applicable | Automated check không được dùng thay manual checks cần thiết; limitations được ghi. | Tool + manual refs | Yes cho required coverage | Testing/Review |

**Completion rule:** Critical/applicable items Pass; N/A có lý do. Không claim accessibility pass chỉ từ visual inspection hoặc tool chưa chạy. Owner: Frontend Design và Testing/Review Standards.
