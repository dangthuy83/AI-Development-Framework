# Open Session Checklist

**Applicability:** Required cho mỗi session. **Trigger:** Trước execution hoặc side effect. **Owner:** Người/AI thực hiện.

| Status | Item | Evidence | Blocking | Owner source |
|---|---|---|---|---|
| Pass / Fail / Not applicable | Project và current state được xác định từ entry/current sources. | Source refs | Yes | Knowledge Management |
| Pass / Fail / Not applicable | Session Contract có Objective, Scope, Constraints, Deliverables. | Contract/note | Yes | AI Working, F-008 |
| Pass / Fail / Not applicable | Intent, dependency, Acceptance Criteria và required verification đủ rõ. | Plan/contract refs | Yes nếu ảnh hưởng execution | AI Working |
| Pass / Fail / Not applicable | Required reads đã nạp; conflict/gap/divergence được ghi. | Read set | Yes nếu required gap | Knowledge Management |
| Pass / Fail / Not applicable | Permission, approval, allowed targets và side effects đã xác định. | Approval/policy ref | Yes | Security/Privacy |
| Pass / Fail / Not applicable | Capability/fallback và evidence path được xác định. | Verification plan | Yes nếu verification bắt buộc | AI Working; Testing/Review |

**Completion rule:** Mọi blocking item Pass trước execution. Not applicable phải có lý do. Workflow owner: [Session Workflow](../workflows/session-workflow.md) và [AI Execution Workflow](../workflows/ai-execution-workflow.md).
