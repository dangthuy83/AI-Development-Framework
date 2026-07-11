# Code Review Checklist

**Applicability:** Conditional cho task tạo, sửa, refactor hoặc review code. **Trigger:** Khi diff sẵn sàng. **Owner:** Reviewer/tác giả nếu Self Review được phép.

| Status | Item | Evidence | Blocking | Owner source |
|---|---|---|---|---|
| Pass / Fail / Not applicable | Diff đúng scope và truy vết Product/Design/Task/Decision. | Diff + refs | Yes | Coding Standards |
| Pass / Fail / Not applicable | Applicable Global/Project rules, enforcement và exception rõ; không silent override. | Rule refs | Yes | Coding Standards |
| Pass / Fail / Not applicable | Logic/error/resource/security/privacy boundary được review theo risk. | Findings note | Yes nếu critical | Coding; Security/Privacy |
| Pass / Fail / Not applicable | Compatibility, regression và documentation impact được xét. | Test/review refs | Yes khi required | Coding; Testing/Review; Documentation |
| Pass / Fail / Not applicable | Required formatter/lint/build/test/manual checks thực sự chạy hoặc limitation được báo. | Command output | Yes cho completed nếu required | Testing/Review |
| Pass / Fail / Not applicable | Findings có severity, evidence, impact và disposition. | Review record | Yes nếu unresolved blocking finding | Testing/Review |

**Completion rule:** Applicable blocking items Pass và blocking findings resolved/accepted bởi authority. Không ghi Pass cho tool chưa chạy. Workflow owner: [AI Execution Workflow](../workflows/ai-execution-workflow.md); Standard owner: [Coding](../standards/coding.md) và [Testing/Review](../standards/testing-and-review.md).
