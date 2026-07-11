# FRAMEWORK_DECISIONS.md

# Nhật ký quyết định kiến trúc của AI Development Framework

Tài liệu này ghi lại các quyết định kiến trúc đã được thống nhất trong quá trình thiết kế Framework.

---
# Architecture Change Requests

| ACR | Trạng thái | Decision  |
|------|-----------|-----------|
| ACR-001 | Accepted | F-010 |
| ACR-002 | Accepted | F-014 |
| ACR-003 | Accepted | F-023 |

---

## ACR-001 — Mở rộng Prompt Strategy thành AI Execution Strategy

**Trạng thái:** Accepted

**Decision:** F-010

**Provenance của bản ghi phục hồi**

Nội dung ACR-001 nguyên bản không còn trong Historical Record. Bản ghi này được tái dựng ngày `2026-07-11` từ:

- Chat snapshot còn lại `Tóm tắt Framework AI.html`, SHA-256 `07E5512092096391500EC996A26F9E0BA9B5A03CAB81637D0E506B4DB18E7007`.
- Bản `FRAMEWORK_DECISIONS.md` trước remediation từ local recovery source, SHA-256 `48B117A615D5132B43CDFDBF8C2412D04D4E3283300B910DE726C7EE5F0C89C9`; đây là provenance evidence, không phải package dependency.
- F-009 và F-010 được bảo toàn nhất quán trong các snapshot tài liệu.
- Xác nhận của Project Owner rằng chat snapshot trên là nguồn lịch sử duy nhất còn chứa nội dung thay đổi liên quan ACR-001.

Đây không phải nguyên văn ACR ban đầu. Phần tái dựng chỉ bảo toàn semantics đã được thể hiện tại F-009 và F-010; không bổ sung hoặc thay đổi Accepted semantics.

**Bối cảnh được phục hồi**

F-009 xác định phải thiết kế Prompt Strategy trước Prompt Library. Trong quá trình làm rõ phạm vi, cách tiếp cận tập trung vào Prompt được đánh giá là quá hẹp vì Framework cần chuẩn hóa toàn bộ quá trình AI thực hiện yêu cầu, không chỉ artifact Prompt cuối cùng.

**Thay đổi được chấp thuận**

1. Giữ F-009 như Historical Record; F-009 được mở rộng bởi F-010, không bị rewrite hoặc silent supersede.
2. Mở rộng Prompt Strategy thành AI Execution Strategy.
3. Framework quản lý toàn bộ quá trình AI thực hiện yêu cầu thay vì quản lý Prompt trước.
4. Xác lập pipeline ở mức kiến trúc:

```text
User Request
      ↓
Intent Detection
      ↓
Intent Graph
      ↓
Context Resolver
      ↓
Constraint Engine
      ↓
Output Contract
      ↓
Prompt Renderer
      ↓
AI Agent
```

5. Prompt chỉ là lớp chuyển đổi hoặc thích ứng cuối cùng trước khi yêu cầu được gửi tới AI Agent; Prompt không phải trung tâm của Framework.
6. Ghi nhận thay đổi bằng F-010 — AI Execution Strategy.

**Lý do được phục hồi**

Điều cần chuẩn hóa là:

- AI cần làm gì.
- AI cần đọc Knowledge Sources nào.
- AI phải tuân theo những ràng buộc nào.
- AI phải tạo ra kết quả gì.

AI Execution Strategy giúp Framework độc lập với từng AI cụ thể và có khả năng mở rộng mà không đặt Prompt ở vị trí trung tâm.

**Ranh giới phục hồi**

- Chi tiết Intent Graph Linear/DAG thuộc F-011, không được gán ngược vào ACR-001.
- Knowledge-first Reasoning thuộc F-012, không được gán ngược vào ACR-001.
- Governance của Framework Documents thuộc F-013, không được gán ngược vào ACR-001.
- Thay đổi kiến trúc cấp cao sau đó thuộc ACR-002/F-014, không thuộc ACR-001.
- Ngày chấp thuận nguyên bản, tác giả, approver và wording xác nhận nguyên văn không còn evidence; không được suy đoán.

---

## ACR-002 — Cập nhật kiến trúc tổng thể của Framework

**Trạng thái:** Accepted

**Bối cảnh**

F-001 xác định kiến trúc tổng thể ban đầu gồm:

1. Global Workspace
2. Project Workspace
3. AI Agent Layer
4. Workflow & Automation

Trong quá trình thiết kế AI Execution Strategy, kiến trúc hiện hành trong FRAMEWORK_SPEC.md v0.2 đã phát triển thành:

1. Global Workspace
2. Project Workspace
3. AI Workflow
4. AI Execution Strategy

F-001 chưa được cập nhật để phản ánh thay đổi này.

**Thay đổi được chấp thuận**

- Dùng sơ đồ kiến trúc trong FRAMEWORK_SPEC.md v0.2 làm kiến trúc hiện hành.
- Không coi AI Agent Layer là một lớp kiến trúc cấp cao độc lập.
- AI Agent là đích thực thi nhận Prompt từ Prompt Renderer.
- AI Workflow trở thành một khối kiến trúc cấp cao.
- Automation là thành phần mở rộng, không còn đại diện cho một lớp kiến trúc cấp cao.
- Thêm F-014 để thay thế F-001 về kiến trúc tổng thể hiện hành.

**Nguyên tắc cập nhật**

Theo F-013, không viết lại nội dung lịch sử của F-001.

F-001 được giữ nguyên và bổ sung ghi chú truy vết đến F-014.

---

## ACR-003 — Điều chỉnh phạm vi F-023 và xác lập Documentation & Template Framework là sản phẩm chính

**Trạng thái:** Accepted

**Liên quan:** F-023

**Bối cảnh**

F-023 đã xác lập Technology-neutral Builder Specification, Modular Package Architecture và Reference Implementation Strategy nhằm chuẩn bị xây dựng một executable Framework.

Qua đánh giá lại mục tiêu sử dụng, Framework chủ yếu phục vụ các dự án cá nhân và cần chuẩn hóa tài liệu, ngữ cảnh, workflow, standards, checklists và prompt khi làm việc với nhiều AI Agent.

Việc yêu cầu Runtime, Storage, Adapter SDK, CLI, database, Conformance Test Suite và Reference Implementation làm điều kiện hoàn thành đã mở rộng phạm vi vượt quá nhu cầu của sản phẩm chính.

**Thay đổi được chấp thuận**

1. Giữ nguyên nội dung lịch sử của F-023 trong `FRAMEWORK_DECISIONS.md`.
2. Xác lập Documentation & Template Framework là sản phẩm chính và bắt buộc của AI Development Framework.
3. Sản phẩm chính gồm:
   - Global Workspace.
   - Project Workspace Template.
   - Bộ tài liệu Markdown chuẩn.
   - Standards.
   - Checklists.
   - AI Workflows.
   - Prompt Templates.
   - Hướng dẫn sử dụng với ChatGPT, Codex, Cline và Claude.
   - Frontend Design Workflow.
   - Hướng dẫn tích hợp Impeccable.
4. F-015 đến F-022 tiếp tục giữ nguyên giá trị kiến trúc và ngữ nghĩa.
5. Các contract của F-015 đến F-022 có thể được hiện thực bằng hướng dẫn, template, checklist, prompt, metadata hoặc quy trình thủ công hay bán tự động.
6. Không mặc nhiên yêu cầu mỗi contract phải có module phần mềm, Runtime hoặc persistent storage tương ứng.
7. Executable Reference Implementation trở thành hướng mở rộng tùy chọn trong tương lai.
8. Runtime, AI Router chạy thật, Storage, Adapter SDK, CLI, database, Web API, message broker, durable workflow engine, NuGet package, Mock Agent bằng code và production deployment không phải điều kiện hoàn thành Framework v1.
9. Reference Implementation Technology Profile không còn nằm trong roadmap sản phẩm chính.
10. Bước tiếp theo của roadmap chính được thay bằng `Framework Deliverable Profile và Template Package Specification`.
11. Builder Specification trong `FRAMEWORK_SPEC.md` được giữ lại như hướng mở rộng tùy chọn có nguồn gốc từ F-023, không phải critical path của Framework v1.
12. Không implementation nào được mặc nhiên bắt đầu chỉ vì nội dung đó xuất hiện trong Builder Specification hoặc roadmap tùy chọn.

**Nguyên tắc quản trị sau ACR-003**

- Dùng Decision mới khi bổ sung một lựa chọn kiến trúc hoặc quy tắc mới không thay đổi Decision đã Accepted.
- Dùng ACR khi thay thế, giới hạn, mở rộng hiệu lực, làm suy yếu hoặc thay đổi nghĩa của Decision, Contract hoặc locked policy đã Accepted.
- Dùng cập nhật Living Document khi chỉ làm rõ nội dung hiện hành mà không thay đổi semantics.
- Dùng Roadmap hoặc implementation plan cho thứ tự công việc, thử nghiệm, pilot và công việc triển khai.
- Việc đưa Executable Reference Implementation trở lại critical path phải có Decision hoặc ACR phù hợp, không được thực hiện chỉ bằng sửa Roadmap.

**Hệ quả**

- Framework v1 có thể hoàn thành và sử dụng mà không cần build một phần mềm Framework riêng.
- F-023 được bảo toàn đầy đủ để truy vết lịch sử.
- Giá trị kiến trúc của F-015 đến F-022 không thay đổi.
- Builder Specification trở thành hướng mở rộng tùy chọn.
- Roadmap chính chuyển sang xây dựng và kiểm chứng bộ tài liệu, template, standards, checklists, prompt và workflow.

---

## F-001 — Kiến trúc tổng thể 4 lớp

**Trạng thái:** Accepted

**Quyết định**

Framework sử dụng kiến trúc 4 lớp:

1. Global Workspace
2. Project Workspace
3. AI Agent Layer
4. Workflow & Automation

**Lý do**

Mô hình này giúp tách rõ:

- Chuẩn dùng chung
- Ngữ cảnh riêng của từng dự án
- Quy tắc cho từng AI agent
- Quy trình vận hành

> **Ghi chú lịch sử:**  
> Kiến trúc tổng thể trong quyết định này đã được thay thế bởi F-014 thông qua ACR-002.  
> Nội dung F-001 được giữ nguyên để đảm bảo khả năng truy vết theo F-013.

---

## F-002 — Global Workspace là nơi chứa chuẩn dùng chung

**Trạng thái:** Accepted

**Quyết định**

Global Workspace chỉ chứa các thành phần dùng chung cho mọi dự án.

Không đưa vào Global Workspace:

- Nghiệp vụ riêng của dự án
- Lỗi riêng của dự án
- Database schema riêng
- Roadmap riêng
- Quyết định kỹ thuật riêng

---

## F-003 — Project Workspace dùng cấu trúc tài liệu chuẩn

**Trạng thái:** Accepted

**Quyết định**

Mỗi dự án có bộ tài liệu chuẩn:

- README.md
- PRODUCT.md
- DESIGN.md
- ROADMAP.md
- DECISIONS.md
- WORKING_CONTEXT.md
- TASKS.md
- CHANGELOG.md
- AGENTS.md

---

## F-004 — Dùng WORKING_CONTEXT.md thay cho PROJECT_MEMORY.md

**Trạng thái:** Accepted

**Quyết định**

Không dùng PROJECT_MEMORY.md làm tài liệu chính.  
Thay vào đó dùng WORKING_CONTEXT.md.

**Lý do**

PROJECT_MEMORY dễ trở thành nơi chứa mọi thứ.  
WORKING_CONTEXT đóng vai trò là bộ nhớ làm việc hiện tại của dự án.

---

## F-005 — Memory phân tầng

**Trạng thái:** Accepted

**Quyết định**

Memory được chia thành 5 tầng:

1. Global Knowledge
2. Project Knowledge
3. Working Context
4. Session Context
5. Lessons Learned

---

## F-006 — Knowledge Lifecycle

**Trạng thái:** Accepted

**Quyết định**

Thông tin đi theo vòng đời:

Session Context  
→ Working Context  
→ Decisions  
→ Lessons Learned

**Mục đích**

Tránh trùng lặp thông tin và giữ Single Source of Truth.

---

## F-007 — AI-Native Workflow

**Trạng thái:** Accepted

**Quyết định**

Mọi phiên làm việc tuân theo workflow 8 bước:

1. Open Session
2. Load Context
3. Define Goal
4. Execute
5. Self Review
6. Update Documents
7. Summarize
8. Close Session

---

## F-008 — Session Contract

**Trạng thái:** Accepted

**Quyết định**

Mỗi phiên làm việc bắt đầu bằng Session Contract gồm:

- Objective
- Scope
- Constraints
- Deliverables

---

## F-009 — Prompt Strategy trước Prompt Library

**Trạng thái:** Accepted

**Quyết định**

Không xây Prompt Library ngay.  
Trước tiên cần thiết kế Prompt Strategy.

Prompt Management gồm:

1. Prompt Strategy
2. Prompt Decision Tree
3. Prompt Metadata
4. Prompt Library

> Ghi chú:
>
> Quyết định này được mở rộng bởi F-010 thông qua ACR-001.
---

## F-010 — AI Execution Strategy

**Trạng thái:** Accepted

**Nguồn gốc**

Được chấp thuận thông qua ACR-001.

**Quyết định**

Prompt Strategy được mở rộng thành AI Execution Strategy.

Framework không quản lý Prompt trước.

Framework quản lý toàn bộ quá trình AI thực hiện yêu cầu.

AI Execution Strategy gồm:

```text
User Request
      ↓
Intent Detection
      ↓
Intent Graph
      ↓
Context Resolver
      ↓
Constraint Engine
      ↓
Output Contract
      ↓
Prompt Renderer
      ↓
AI Agent
```

Prompt chỉ là lớp chuyển đổi cuối cùng trước khi gửi yêu cầu đến AI.

**Lý do**

Điều cần chuẩn hóa không phải Prompt mà là:

- AI cần làm gì.
- AI cần đọc Knowledge Sources nào.
- AI phải tuân theo những ràng buộc nào.
- AI phải tạo ra kết quả gì.

Framework trở nên độc lập với từng AI cụ thể và có khả năng mở rộng trong tương lai.

---

## F-011 — Intent Detection sử dụng Intent Graph

**Trạng thái:** Accepted

**Quyết định**

Intent Detection không trả về một Intent đơn lẻ.

Intent Detection trả về một Intent Graph.

Intent Graph là Output Contract của Intent Detection.

Intent Graph bao gồm:

- Chuỗi Intent cần thực hiện.
- Quan hệ phụ thuộc giữa các Intent.
- Confidence.
- Ambiguity.
- Missing Information.
- Execution Policy.

Giai đoạn đầu Intent Graph có thể là Linear Graph.

Framework phải thiết kế để sau này mở rộng thành Directed Acyclic Graph (DAG).

**Lý do**

Nhiều yêu cầu của người dùng bao gồm nhiều Intent nối tiếp nhau.

Ví dụ:

Review
↓

Fix

↓

Regression Test

Intent Graph tạo nền tảng cho:

- Multi-Agent
- AI Router
- Workflow Automation

mà không phải thay đổi Execution Pipeline.

---

## F-012 — Knowledge-first Reasoning

**Trạng thái:** Accepted

**Quyết định**

Framework ưu tiên suy luận từ Knowledge Sources thay vì để AI tự suy đoán.

Nguyên tắc:

AI không được suy đoán khi Framework có thể suy luận từ Knowledge Sources.

Framework ưu tiên:

```text
Knowledge-first
↓
Reasoning
↓
Execution

Thay vì:

Prompt-first
↓
Execution
```

Nếu Knowledge Sources chưa đủ thông tin:

- AI phải yêu cầu làm rõ.
- Không tự giả định.
- Không tự tạo Decision mới.

**Lý do**

Giảm hallucination.

Đảm bảo Single Source of Truth.

Tăng tính nhất quán của Framework.

---

## F-013 — Governance of Framework Documents

**Trạng thái:** Accepted

**Quyết định**

Framework phân biệt hai loại tài liệu:

### Living Documents

Có thể cập nhật để phản ánh trạng thái kiến trúc hiện tại.

Ví dụ:

- FRAMEWORK_SPEC.md
- ROADMAP.md
- WORKING_CONTEXT.md

### Historical Records

Không viết lại lịch sử.

Chỉ được:

- Thêm Decision
- Thêm ACR
- Thêm Note
- Sửa format
- Sửa lỗi trình bày

Ví dụ:

- FRAMEWORK_DECISIONS.md

**Lý do**

Đảm bảo khả năng truy vết (Traceability).

Giữ nguyên lịch sử tiến hóa của kiến trúc.

Phù hợp với mô hình Architecture Decision Record (ADR).

---

## F-014 — Kiến trúc tổng thể cập nhật

**Trạng thái:** Accepted

**Nguồn gốc**

Được chấp thuận thông qua ACR-002.

Quyết định này thay thế F-001 về kiến trúc tổng thể hiện hành.

**Quyết định**

AI Development Framework sử dụng bốn khối kiến trúc cấp cao:

1. Global Workspace
2. Project Workspace
3. AI Workflow
4. AI Execution Strategy

```text
AI Development Framework

├── Global Workspace
│
├── Project Workspace
│
├── AI Workflow
│
└── AI Execution Strategy
    ├── Intent Detection
    ├── Intent Graph
    ├── Context Resolver
    ├── Constraint Engine
    ├── Output Contract
    └── Prompt Renderer
```

**Ranh giới kiến trúc**

### Global Workspace

Chứa các chuẩn, chiến lược, template và checklist dùng chung cho mọi dự án.

### Project Workspace

Chứa Knowledge Sources và trạng thái riêng của từng dự án.

### AI Workflow

Quản lý vòng đời của phiên làm việc và trình tự thực hiện công việc của AI.

### AI Execution Strategy

Chuyển User Request thành AI Execution Context có cấu trúc trước khi gửi đến AI Agent.

AI Agent không còn là một khối kiến trúc cấp cao độc lập.

AI Agent là đích thực thi nhận Prompt do Prompt Renderer tạo ra.

Automation là thành phần mở rộng và sẽ được thiết kế ở giai đoạn sau.

**Lý do**

Kiến trúc mới phản ánh đúng trọng tâm của Framework:

- Knowledge được tổ chức ở đâu.
- Trạng thái dự án được quản lý ở đâu.
- AI làm việc theo quy trình nào.
- Yêu cầu được phân tích và chuyển thành Execution Context như thế nào.

Kiến trúc này đồng bộ với F-010, F-011 và F-012.

**Hệ quả**

- Các tài liệu và sơ đồ mới phải dùng bốn khối kiến trúc của F-014.
- Khi gặp tham chiếu cũ đến kiến trúc F-001, ưu tiên F-014.
- Không xóa F-001 khỏi lịch sử quyết định.

---

## F-015 — Intent Detection Contract v1

**Trạng thái:** Accepted

**Bối cảnh**

F-010 xác định Intent Detection là mô-đun đầu tiên của AI Execution Strategy.

F-011 yêu cầu Intent Detection trả về Intent Graph thay vì một Intent đơn lẻ.

F-012 yêu cầu Framework ưu tiên Knowledge-first Reasoning và không tự suy đoán khi thiếu thông tin.

Framework cần một contract rõ ràng để Intent Detection có thể hoạt động nhất quán và chuyển kết quả cho Context Resolver.

**Quyết định**

Intent Detection sử dụng Intent Graph Contract v1 có cấu trúc rõ ràng.

Intent Detection chỉ được sử dụng:

- User Request
- Session Context
- Conversation Context

Intent Detection không được:

- Đọc Knowledge Sources.
- Chọn file hoặc tài liệu cần đọc.
- Áp dụng Decisions, Standards hoặc Policies.
- Xây dựng Output Contract chi tiết.
- Thực thi yêu cầu.
- Tự suy đoán Knowledge của dự án.

**Intent Graph Contract v1**

Intent Graph gồm các trường bắt buộc:

- request_summary
- nodes
- edges
- graph_confidence
- ambiguity
- missing_information
- execution_policy

Mỗi Node gồm:

- id
- type
- objective
- confidence

Mỗi Edge gồm:

- from
- to
- relation

Trong phiên bản đầu, relation sử dụng giá trị `precedes`.

Edge `from: I1`, `to: I2`, `relation: precedes` có nghĩa I1 phải hoàn thành trước I2.

**Intent Type ban đầu**

Framework sử dụng taxonomy có kiểm soát nhưng cho phép mở rộng:

- initialize
- continue
- analyze
- design
- implement
- fix
- refactor
- review
- test
- document
- ui_polish
- database
- release
- other

**Confidence Model**

Confidence sử dụng ba mức:

- high
- medium
- low

Không dùng điểm số từ 0 đến 1 để tránh tạo cảm giác chính xác giả.

**Resolution Policy**

Mỗi Ambiguity hoặc Missing Information phải xác định một hướng xử lý:

- context_resolver
- ask_user
- stop

Intent Detection không hỏi người dùng ngay nếu thông tin có khả năng được tìm thấy trong Knowledge Sources.

Trường hợp đó phải chuyển cho Context Resolver xử lý.

**Execution Policy**

Execution Policy sử dụng bốn giá trị:

- proceed
- resolve_context
- clarify
- stop

Thứ tự ưu tiên khi xác định Execution Policy:

```text
stop
↓
clarify
↓
resolve_context
↓
proceed
```

**Graph Model**

Giai đoạn đầu chỉ thực thi Linear Graph.

Contract vẫn sử dụng Nodes và Edges để có thể mở rộng thành Directed Acyclic Graph trong tương lai mà không thay đổi giao diện giữa các mô-đun.

**Validation Rules**

- Graph phải có ít nhất một Node.
- ID của Node không được trùng.
- Mọi Edge phải tham chiếu đến Node hợp lệ.
- Graph không được có chu trình.
- Linear Graph là mô hình thực thi duy nhất của phiên bản đầu; mỗi Node có tối đa một Edge đi vào và một Edge đi ra.
- Mọi Ambiguity và Missing Information phải có hướng xử lý.
- Execution Policy phải phù hợp với trạng thái của Graph.
- Intent Graph không được chứa Knowledge dự án do AI tự suy đoán.

**Lý do**

Phương án Intent Graph có contract rõ ràng:

- Phù hợp với F-010 và F-011.
- Tách Intent Detection khỏi Context Resolver.
- Hỗ trợ yêu cầu gồm nhiều Intent có quan hệ phụ thuộc.
- Cho phép kiểm tra contract tự động.
- Chuẩn bị cho DAG, Multi-Agent và Workflow Automation trong tương lai.
- Tuân thủ Knowledge-first Reasoning của F-012.

**Hệ quả**

- Context Resolver phải nhận Intent Graph Contract v1 làm đầu vào.
- Các mô-đun sau không được tự diễn giải lại User Request nếu Intent Graph đã hợp lệ.
- Thay đổi không tương thích với contract này phải được quản lý bằng Decision mới hoặc ACR phù hợp.

---

## F-016 — Hybrid Context Resolution và Context Resolution Contract v1

**Trạng thái:** Accepted

**Bối cảnh**

F-010 xác định Context Resolver là mô-đun đứng sau Intent Detection và trước Constraint Engine.

F-012 yêu cầu Framework ưu tiên Knowledge-first Reasoning.

F-015 cung cấp Intent Graph Contract v1 làm đầu vào cho Context Resolver.

Framework cần chọn đúng Knowledge Sources mà không đọc toàn bộ tài liệu, không bỏ sót nguồn chuẩn và không để AI lựa chọn hoàn toàn tự do.

**Quyết định**

Context Resolver sử dụng Hybrid Context Resolution.

Phương pháp này kết hợp:

- Routing mặc định theo Intent và loại Knowledge.
- Metadata của Knowledge Sources.
- Liên kết giữa các nguồn.
- Mở rộng Context có giới hạn khi nguồn ban đầu chưa đủ.

Context Resolver hoạt động theo hai giai đoạn.

### Giai đoạn 1 — Source Selection

1. Xác định nhu cầu thông tin của từng Intent.
2. Xác định loại Knowledge Source chịu trách nhiệm.
3. Chọn nguồn required, supporting hoặc optional.
4. Xác định phạm vi đọc phù hợp.

### Giai đoạn 2 — Context Resolution

1. Nạp phần nội dung đã chọn.
2. Ghi nhận provenance.
3. Trích xuất các resolved facts có nguồn tham chiếu.
4. Phát hiện conflicts, gaps và nguồn lỗi thời.
5. Tạo Context Resolution Contract v1 để chuyển cho Constraint Engine.

**Đầu vào**

Context Resolver sử dụng:

- Intent Graph Contract v1 hợp lệ.
- Knowledge Source Catalog ở runtime.
- Metadata và liên kết của các Knowledge Sources có thể truy cập.

Knowledge Source Catalog là cấu trúc runtime phục vụ discovery và routing.

Nó không phải là một Single Source of Truth mới.

Context Resolver không được tự diễn giải lại User Request khi Intent Graph còn hợp lệ.

**Phân loại Knowledge Sources**

- governance
- product
- architecture
- working
- implementation
- evidence
- lessons

Không sử dụng một thứ tự ưu tiên duy nhất cho mọi loại thông tin.

Nguồn có thẩm quyền phụ thuộc vào câu hỏi:

- Hành vi mong muốn → Product Knowledge.
- Lý do quyết định → Decisions.
- Kiến trúc hiện hành → Design Knowledge.
- Hệ thống được triển khai thế nào → Source Code và Configuration.
- Hệ thống thực tế hoạt động thế nào → Tests, Logs và Runtime Evidence.
- Trạng thái công việc → Working Context và Tasks.
- Chuẩn dùng chung → Global Standards.

Nếu nguồn mô tả hành vi mong muốn khác với implementation hoặc runtime evidence, Context Resolver phải ghi nhận divergence thay vì tự chọn một nguồn là đúng.

**Context Resolution Contract v1**

Contract gồm các trường bắt buộc:

- intent_contexts
- context_status
- context_confidence
- next_action

Mỗi phần tử trong intent_contexts gồm:

- intent_id
- requirements
- selected_sources
- resolved_facts
- conflicts
- gaps

Mỗi requirement gồm:

- type
- purpose
- criticality

Criticality sử dụng:

- required
- supporting
- optional

Mỗi selected source gồm:

- source_id
- location
- authority
- load_scope
- reason

Authority sử dụng:

- primary
- supporting
- observational
- historical

Load Scope sử dụng:

- metadata_only
- relevant_sections
- full_source

Mặc định ưu tiên relevant_sections.

Mỗi resolved fact phải có:

- statement
- source_ref

**Context Status**

- resolved
- partial
- blocked

**Context Confidence**

- high
- medium
- low

**Next Action**

- constraint_engine
- clarify
- stop

Context Resolver chỉ dùng `clarify` sau khi đã xác định thông tin không thể lấy từ Knowledge Sources có thể truy cập.

**Ranh giới trách nhiệm**

Context Resolver không được:

- Sửa Intent Graph.
- Tự áp dụng Decisions, Standards hoặc Policies.
- Tự giải quyết xung đột giữa các nguồn có cùng thẩm quyền.
- Biến resolved facts thành Project Knowledge mới.
- Đọc full source khi relevant sections đã đủ.
- Đưa bí mật hoặc dữ liệu không cần thiết vào Context Package.

**Validation Rules**

- Mọi intent_id phải tham chiếu Node hợp lệ trong Intent Graph.
- Mỗi requirement có criticality `required` phải có selected source hoặc gap tương ứng.
- Mọi resolved fact phải có source_ref hợp lệ.
- Conflict và divergence không được bị loại bỏ âm thầm.
- Thiếu nguồn required phải làm context_status trở thành blocked.
- Context status partial chỉ được dùng khi phần thiếu không chặn Intent.
- next_action phải phù hợp với context_status và gaps.
- Context Package chỉ tồn tại trong phiên thực thi và không trở thành nguồn chuẩn mới.

**Lý do**

Hybrid Context Resolution:

- Hạn chế đọc dư Context.
- Giữ tính xác định tốt hơn lựa chọn hoàn toàn tự do.
- Cho phép mở rộng theo metadata và tài liệu dự án.
- Giữ provenance cho mọi resolved fact.
- Phát hiện khác biệt giữa intended behavior, implementation và runtime evidence.
- Tuân thủ Single Source of Truth và Knowledge-first Reasoning.

**Hệ quả**

- Constraint Engine phải nhận Context Resolution Contract v1 làm đầu vào.
- Workspace phải cung cấp metadata hoặc điểm vào đủ để tạo Knowledge Source Catalog ở runtime.
- Builder phải hỗ trợ kiểm tra provenance, gaps, conflicts và contract validation.
- Thay đổi không tương thích với contract này phải được quản lý bằng Decision mới hoặc ACR phù hợp.

---

## F-017 — Typed Constraint Engine và Constraint Evaluation Contract v1

**Trạng thái:** Accepted

**Bối cảnh**

F-008 yêu cầu mỗi phiên có Session Contract gồm Objective, Scope, Constraints và Deliverables.

F-010 xác định Constraint Engine đứng sau Context Resolver và trước Output Contract.

F-015 cung cấp Intent Graph Contract v1.

F-016 cung cấp Context Resolution Contract v1.

Framework cần hợp nhất các constraint từ nhiều nguồn, phát hiện xung đột và tạo pre-execution gate mà không để AI tự bỏ qua hoặc tự tạo quy tắc.

**Quyết định**

Constraint Engine sử dụng Typed Constraint Engine và tạo Constraint Evaluation Contract v1.

Constraint Engine nhận ba đầu vào có cấu trúc:

1. Intent Graph Contract v1.
2. Context Resolution Contract v1.
3. Session Contract.

Session Contract được truyền trực tiếp để giữ nguyên các constraint người dùng đã xác định mà không yêu cầu các mô-đun sau diễn giải lại User Request.

**Quy trình xử lý**

```text
Collect
↓
Normalize
↓
Scope
↓
Resolve Precedence
↓
Detect Conflicts
↓
Build Effective Constraint Set
↓
Pre-execution Gate
```

**Nguồn Constraint**

- Platform, Safety và Access Policies.
- Framework Decisions.
- Project Decisions.
- Session Contract.
- Project Rules.
- Global Standards.
- Tool và Environment Capabilities.
- User Preferences không mang tính bắt buộc.

**Constraint Types**

- safety
- permission
- scope
- architecture
- product
- data
- security
- privacy
- coding
- testing
- documentation
- tooling
- operational
- delivery
- other

**Enforcement Level**

- mandatory
- approval_required
- advisory

Constraint `mandatory` không được tự bỏ qua hoặc tự hạ cấp.

Constraint `approval_required` chỉ được giải quyết bằng phê duyệt rõ ràng hoặc Decision/ACR phù hợp.

Constraint `advisory` có thể không áp dụng nhưng phải ghi rõ lý do.

**Authority**

- platform_policy
- framework_decision
- project_decision
- session
- project_rule
- global_standard
- tool_environment
- preference

Không sử dụng riêng thứ tự nguồn để quyết định constraint nào thắng.

Constraint Engine phải xét đồng thời:

- Authority.
- Enforcement Level.
- Scope.
- Constraint Type.
- Trạng thái Decision.
- Ngoại lệ đã được ghi nhận chính thức.

**Quy tắc xử lý xung đột**

1. Safety, Access và Platform Policies không thể bị ghi đè.
2. Session Contract không tự thay thế Decision đã Accepted.
3. Yêu cầu thay đổi Decision đã Accepted phải chuyển sang Decision hoặc ACR.
4. Project Rule có thể khác Global Standard nếu ngoại lệ đã được ghi nhận chính thức.
5. Hai constraint cùng thẩm quyền nhưng mâu thuẫn phải chuyển sang clarify.
6. Constraint Engine không được tự tạo ngoại lệ.
7. Constraint không có provenance không được coi là constraint bắt buộc.

**Constraint Evaluation Contract v1**

Contract gồm các trường bắt buộc:

- intent_constraints
- constraint_status
- constraint_confidence
- next_action

Mỗi phần tử trong intent_constraints gồm:

- intent_id
- effective_constraints
- conflicts
- required_approvals
- request_violations

Mỗi effective constraint gồm:

- constraint_id
- type
- statement
- source_ref
- scope
- enforcement
- authority

**Constraint Status**

- resolved
- conditional
- blocked

**Constraint Confidence**

- high
- medium
- low

Confidence phản ánh độ đầy đủ và rõ ràng của constraint, không phản ánh khả năng AI thực hiện nhiệm vụ.

**Next Action**

- output_contract
- context_resolver
- clarify
- decision_or_acr
- stop

Quy tắc chuyển tiếp:

- Thiếu Knowledge để xác định constraint → context_resolver.
- Cần lựa chọn của người dùng → clarify.
- Yêu cầu thay đổi Decision đã Accepted → decision_or_acr.
- Vi phạm constraint không thể ghi đè → stop.
- Constraint đã được giải quyết → output_contract.

**Ranh giới trách nhiệm**

Constraint Engine không được:

- Tự cấp quyền hoặc coi im lặng là phê duyệt.
- Tự sửa Decision, Standard hoặc Session Contract.
- Tự bỏ qua constraint không thuận tiện.
- Đọc thêm Knowledge Sources ngoài Context Resolution Contract.
- Tự thiết kế Deliverables thay Output Contract.
- Đánh giá code sau thực thi thay Verification hoặc Self Review.
- Tạo constraint không có source_ref.

**Validation Rules**

- Mọi intent_id phải tồn tại trong Intent Graph.
- Mỗi constraint phải có source_ref hợp lệ.
- constraint_id không được trùng.
- Constraint mandatory không được tự hạ cấp.
- Conflict không được loại bỏ âm thầm.
- Required approval phải có trạng thái rõ ràng.
- Trạng thái resolved không được chứa conflict chưa xử lý.
- Trạng thái conditional phải có hành động tiếp theo.
- Trạng thái blocked không được chuyển sang Output Contract.
- Constraint Engine không được đưa constraint mới không có nguồn.

**Lý do**

Typed Constraint Engine:

- Giữ nguyên constraint người dùng từ Session Contract.
- Chuẩn hóa constraint từ nhiều nguồn.
- Cho phép truy vết bằng provenance.
- Phát hiện xung đột trước khi AI thực thi.
- Phân biệt constraint bắt buộc, cần phê duyệt và khuyến nghị.
- Tạo execution gate có thể kiểm tra tự động.
- Không phụ thuộc vào từng AI cụ thể.

**Hệ quả**

- Output Contract phải nhận Constraint Evaluation Contract v1 làm đầu vào.
- Khi Constraint Engine trả về conditional hoặc blocked, pipeline không được tự chuyển sang Output Contract.
- Builder phải hỗ trợ validation, conflict reporting và required approval state.
- Thay đổi không tương thích với contract này phải được quản lý bằng Decision mới hoặc ACR phù hợp.

---

## F-018 — Hybrid Output Contract và Output Contract v1

**Trạng thái:** Accepted

**Bối cảnh**

F-010 xác định Output Contract đứng sau Constraint Engine và trước Prompt Renderer.

F-015 cung cấp Intent Graph Contract v1. F-016 cung cấp Context Resolution Contract v1. F-017 cung cấp Constraint Evaluation Contract v1 và pre-execution gate.

Framework cần xác định rõ AI Agent phải tạo ra kết quả gì, kết quả phải đáp ứng điều kiện nào và phải được kiểm chứng như thế nào mà không diễn giải lại User Request hoặc thay đổi các contract phía trước.

**Quyết định**

Output Contract sử dụng Hybrid Execution Manifest, kết hợp:

- Một envelope chung cho toàn contract.
- Danh sách deliverable độc lập.
- Liên kết một deliverable với một hoặc nhiều Intent.
- Acceptance Criteria và Verification Requirements có ID riêng.
- Completion Protocol và Failure Handling dùng chung.
- Traceability xuyên suốt Intent, Context, Effective Constraints và đầu ra mong đợi.

Thiết kế hỗ trợ Linear Graph hiện tại và cho phép mở rộng sang DAG, Multi-Agent và Workflow Automation mà không thay đổi giao diện cốt lõi.

**Điều kiện đầu vào**

Output Contract nhận:

1. Intent Graph Contract v1 hợp lệ.
2. Context Resolution Contract v1 hợp lệ.
3. Constraint Evaluation Contract v1 hợp lệ.

Chỉ tạo Output Contract khi:

```text
constraint_status = resolved
AND
next_action = output_contract
```

Output Contract không nhận trực tiếp Session Contract. Constraint từ Session Contract được Constraint Engine hợp nhất vào Effective Constraint Set và truy vết qua `source_ref`.

**Output Contract v1**

Contract gồm các trường bắt buộc:

- contract_version
- contract_id
- execution_ref
- input_refs
- deliverables
- acceptance_criteria
- verification_requirements
- completion_protocol
- failure_handling
- traceability
- contract_status
- next_action

`input_refs` gồm:

- intent_graph_ref
- context_resolution_ref
- constraint_evaluation_ref

`execution_ref` đảm bảo các contract đầu vào thuộc cùng một phiên thực thi.

**Deliverable**

Mỗi deliverable gồm:

- id
- type
- intent_refs
- description
- required
- acceptance_criteria_refs
- verification_refs
- constraint_refs
- context_refs

Các trường `format` và `target` có thể được bổ sung khi đầu ra yêu cầu định dạng hoặc vị trí đích cụ thể.

`description` chỉ mô tả đầu ra cần tạo và không được diễn giải lại User Request.

**Deliverable Types**

- source_code
- patch
- configuration
- architecture_proposal
- design_specification
- sql_script
- database_migration
- test_plan
- test_case
- test_result
- documentation
- report
- command_sequence
- data_artifact
- ui_asset
- release_artifact
- other

Khi dùng `other`, phải cung cấp `custom_type`.

**Acceptance Criteria**

Mỗi Acceptance Criterion gồm:

- id
- deliverable_refs
- statement
- type
- required
- origin_refs

Acceptance Criterion phải nguyên tử, có thể xác định đạt hoặc không đạt và có nguồn gốc từ Intent, Context hoặc Effective Constraint. Không được tạo yêu cầu mới không có nguồn.

**Verification Requirements**

Mỗi Verification Requirement gồm:

- id
- deliverable_refs
- criterion_refs
- method
- required
- evidence_required
- expected_evidence
- execution_condition

Verification Methods ban đầu:

- schema_validation
- build
- automated_test
- regression_test
- lint
- static_analysis
- runtime_check
- manual_inspection
- document_review
- diff_review
- user_confirmation

Output Contract xác định cần kiểm chứng điều gì và cần bằng chứng gì. Nó không thực hiện verification và không thay thế Self Review.

**Ánh xạ Enforcement**

- Constraint `mandatory` phải được ánh xạ vào deliverable, Acceptance Criterion, Verification Requirement hoặc execution restriction phù hợp.
- Constraint `approval_required` chỉ được ánh xạ sau khi approval đã được Constraint Engine giải quyết.
- Constraint `advisory` có thể tạo criterion không bắt buộc; Output Contract không được tự quyết định bỏ qua advisory trái với kết quả của Constraint Engine.

**Completion Protocol**

Trạng thái kết quả mà AI Agent phải báo cáo:

- completed
- partial
- blocked
- failed
- skipped

`completed` chỉ được dùng khi mọi deliverable và Acceptance Criterion bắt buộc đã hoàn thành, đồng thời mọi Verification Requirement bắt buộc đã được thực hiện hoặc việc không thể thực hiện đã được báo cáo theo contract.

Output Contract chỉ định nghĩa giao thức báo cáo. Nó không được tuyên bố kết quả đã hoàn thành trước khi AI Agent thực thi.

**Failure và Partial-result Handling**

- Giữ lại các kết quả hợp lệ đã tạo.
- Không báo `completed` sai.
- Báo rõ deliverable, criterion và verification chưa hoàn thành.
- Báo blocker và execution uncertainty.
- Không tạo giả định mới để vượt qua Context hoặc Constraint còn thiếu.
- `skipped` chỉ được dùng cho đầu ra không bắt buộc hoặc khi Effective Constraint cho phép.

**Provenance và Traceability**

Output Contract phải duy trì chuỗi truy vết:

```text
Intent
↓
Resolved Facts
↓
Effective Constraints
↓
Deliverable
↓
Acceptance Criterion
↓
Verification Requirement
↓
Verification Evidence và Completion Result
```

Output Contract sử dụng tham chiếu thay vì sao chép toàn bộ User Request, Context hoặc Constraint.

**Chuyển tiếp sang Prompt Renderer**

Chỉ chuyển sang Prompt Renderer khi:

```text
contract_status = ready
AND
next_action = prompt_renderer
```

Mọi ID và tham chiếu phải hợp lệ và không được còn blocking condition.

Prompt Renderer phải giữ nguyên ý nghĩa của Deliverables, Acceptance Criteria, Verification Requirements và Completion Protocol.

**Ranh giới trách nhiệm**

Output Contract không được:

- Đọc lại hoặc diễn giải lại User Request.
- Thêm, xóa, hợp nhất hoặc sắp xếp lại Intent.
- Sửa Context hoặc resolved facts.
- Đọc thêm Knowledge Sources.
- Đánh giá lại, bỏ qua hoặc hạ cấp Effective Constraints.
- Tự xin, tự cấp hoặc suy đoán approval.
- Tạo giả định mới để vượt qua thông tin còn thiếu.
- Chọn AI Agent hoặc công cụ thực thi.
- Tạo Prompt.
- Thực thi công việc hoặc verification.
- Tuyên bố kết quả đã hoàn thành trước execution.
- Trở thành Single Source of Truth mới.

**Validation Rules**

- Ba input contract phải hợp lệ và thuộc cùng `execution_ref`.
- Constraint Evaluation Contract phải có `constraint_status: resolved` và `next_action: output_contract`.
- Contract phải có ít nhất một deliverable.
- ID của deliverable, Acceptance Criterion và Verification Requirement không được trùng.
- Mọi `intent_ref` phải tồn tại trong Intent Graph.
- Mọi `context_ref` phải tồn tại trong Context Resolution Contract.
- Mọi `constraint_ref` phải tồn tại trong `effective_constraints`.
- Mỗi deliverable bắt buộc phải có ít nhất một Acceptance Criterion bắt buộc.
- Mỗi Acceptance Criterion phải tham chiếu ít nhất một deliverable.
- Mỗi Acceptance Criterion bắt buộc phải có Verification Requirement hoặc được đánh dấu không thể kiểm chứng trực tiếp kèm lý do.
- Mỗi Verification Requirement phải tham chiếu criterion hợp lệ.
- Không được chứa yêu cầu mới không có upstream origin.
- Không được bỏ sót hoặc hạ cấp constraint `mandatory`.
- Không được còn conflict, required approval hoặc request violation mang tính blocking.
- Chỉ `contract_status: ready` mới được dùng `next_action: prompt_renderer`.

**Lý do**

Hybrid Output Contract:

- Giữ ranh giới rõ giữa specification và execution result.
- Hỗ trợ nhiều Intent và deliverable dùng chung.
- Cho phép validation tự động.
- Bảo toàn provenance và traceability.
- Phù hợp với Knowledge-first Reasoning.
- Tương thích Linear Graph hiện tại và DAG trong tương lai.
- Chuẩn bị cho Multi-Agent, AI Router và Workflow Automation.

**Hệ quả**

- Prompt Renderer phải nhận Output Contract v1 làm đầu vào.
- Builder phải hỗ trợ kiểm tra ID, tham chiếu, provenance, Acceptance Criteria và Verification Requirements.
- Runtime phải tách Output Contract khỏi báo cáo kết quả sau thực thi.
- Schema chi tiết cho Completion Result và Verification Evidence sẽ được hoàn thiện ở Builder Specification hoặc Decision tiếp theo nếu làm thay đổi kiến trúc.
- Thay đổi không tương thích với contract này phải được quản lý bằng Decision mới hoặc ACR phù hợp.

---

## F-019 — Hybrid Prompt Rendering và Prompt Renderer Contract v1

**Trạng thái:** Accepted

**Bối cảnh**

F-010 xác định Prompt Renderer đứng sau Output Contract và trước AI Agent.

F-015, F-016, F-017 và F-018 cung cấp lần lượt Intent Graph Contract v1, Context Resolution Contract v1, Constraint Evaluation Contract v1 và Output Contract v1.

Framework cần chuyển AI Execution Context có cấu trúc thành Prompt phù hợp với nhiều AI Agent khác nhau mà không diễn giải lại User Request, thay đổi Intent, làm sai lệch Context, hạ cấp Effective Constraints hoặc tạo thêm yêu cầu đầu ra.

Một Universal Prompt duy nhất không tận dụng được capability đặc thù của từng Agent. Renderer riêng hoàn toàn cho từng Agent lại tạo trùng lặp logic và làm Framework phụ thuộc nền tảng.

**Quyết định**

Prompt Renderer sử dụng Hybrid Prompt Rendering gồm:

```text
Upstream Contracts
        ↓
Canonical Execution Package
        ↓
Prompt Renderer Core
        ↓
Canonical Prompt Model
        ↓
Agent Adapter
        ↓
Rendered Prompt hoặc Message Set
        ↓
Runtime
        ↓
AI Agent
```

Canonical Execution Package giữ semantics chuẩn của execution.

Prompt Renderer Core tạo cấu trúc Prompt trung lập với từng AI Agent.

Agent Adapter chỉ chuyển Canonical Prompt Model sang format mà Target Agent hỗ trợ.

Runtime hoặc AI Router chọn Target Agent và Agent Adapter. Prompt Renderer không được tự chọn Agent, model hoặc adapter.

Rendered Prompt là runtime artifact, không phải Single Source of Truth hoặc contract thay thế các contract phía trước.

**Đầu vào**

Prompt Renderer nhận:

1. Intent Graph Contract v1 hợp lệ.
2. Context Resolution Contract v1 hợp lệ.
3. Constraint Evaluation Contract v1 hợp lệ.
4. Output Contract v1 có `contract_status: ready` và `next_action: prompt_renderer`.
5. Context Payload do Context Resolver chuẩn bị ở runtime.
6. Target Agent Profile do Runtime hoặc AI Router cung cấp.
7. Rendering Policy và Runtime Metadata.

Các đầu vào phải thuộc cùng một `execution_ref`.

**Context Payload**

Context Payload:

- Chứa nội dung đã được Context Resolver cho phép chuyển tiếp.
- Liên kết với Context Resolution Contract v1 bằng reference và provenance.
- Chỉ tồn tại trong execution runtime.
- Không phải Knowledge Source hoặc Single Source of Truth mới.
- Không được Prompt Renderer tự tạo, tự mở rộng hoặc rút gọn ngữ nghĩa.

Quyết định này không thay đổi Context Resolution Contract v1. Context Payload là package runtime liên kết với contract đó.

**Canonical Execution Package**

Canonical Execution Package gồm tối thiểu:

- package_version
- package_id
- execution_ref
- input_refs
- intent_graph
- context_resolution
- constraint_evaluation
- output_contract
- context_payload
- target_agent_profile
- rendering_policy
- runtime_metadata

Package sử dụng các contract upstream làm nguồn và không được tạo bản diễn giải mới của User Request.

**Target Agent Profile**

Target Agent Profile gồm tối thiểu:

- profile_version
- agent_id
- agent_family
- model_id
- adapter_id
- capabilities
- limits
- supported_formats
- security
- reporting

Agent Capability Model phải mô tả tối thiểu:

- instruction_channels
- structured_input
- structured_output
- tool_calling
- filesystem_read
- filesystem_write
- command_execution
- code_editing
- patch_application
- web_access
- file_attachment
- multi_turn
- continuation
- parallel_execution
- verification_execution

Mỗi capability có trạng thái `native`, `emulated` hoặc `unavailable` và có thể kèm limits hoặc conditions.

**Prompt Renderer Contract v1**

Contract gồm các trường bắt buộc:

- contract_version
- render_id
- execution_ref
- package_ref
- target_agent_profile_ref
- adapter_ref
- input_validation
- capability_evaluation
- canonical_prompt
- rendering
- rendered_artifact
- render_status
- next_action
- failure_report

`canonical_prompt` gồm:

- instruction_layers
- sections
- response_schema
- provenance_map

`rendering` gồm:

- format
- token_budget
- estimated_tokens
- context_packaging
- preservation_manifest

`rendered_artifact` gồm:

- artifact_type
- content
- content_hash

**Render Status**

- ready
- blocked
- invalid
- requires_repackaging
- unsupported

**Next Action**

- agent_adapter
- ai_agent
- context_resolver
- runtime_planner
- agent_router
- clarify
- stop

**Canonical Prompt Sections**

1. Execution Identity.
2. Role và Execution Objective.
3. Instruction Precedence.
4. Authorized Intent Graph.
5. Authorized Context.
6. Effective Constraints.
7. Required Deliverables.
8. Acceptance Criteria.
9. Verification Requirements.
10. Execution Restrictions.
11. Completion Protocol.
12. Failure và Partial-result Protocol.
13. Required Response Schema.
14. Provenance và Traceability.

Agent Adapter có thể thay đổi cú pháp trình bày nhưng không được thay đổi ý nghĩa, ID, quan hệ hoặc thứ tự thực thi Intent.

**Instruction Precedence**

Prompt Renderer không được tự tính lại hoặc giải quyết precedence.

Renderer chỉ biểu diễn precedence đã được Platform, Runtime, Constraint Engine và các contract phía trước xác định.

Nếu package còn instruction mâu thuẫn với Effective Constraint, Renderer phải trả `blocked` thay vì tự chọn instruction thắng.

**Context Packaging**

Prompt Renderer chỉ được thực hiện biến đổi lossless:

- Sắp xếp Context theo Intent và reference.
- Gắn tiêu đề, index và provenance.
- Chuyển encoding hoặc format trình bày.
- Loại bỏ bản sao byte-identical khi policy cho phép và vẫn giữ đủ reference.
- Compact phần trình bày không mang semantics.

Prompt Renderer không được tóm tắt Context bằng suy luận, loại bỏ resolved fact, đọc thêm Knowledge Source, hợp nhất fact thành kết luận mới, giải quyết conflict hoặc che giấu gap.

Rút gọn ngữ nghĩa Context thuộc Context Resolver hoặc Context Packaging component do Context Resolver kiểm soát.

**Constraint Preservation**

Prompt Renderer phải tạo Constraint Preservation Manifest cho mọi Effective Constraint.

Mỗi bản ghi gồm tối thiểu:

- constraint_id
- source_ref
- enforcement
- scope
- rendered_location
- semantic_status

Mọi constraint `mandatory` phải được render và không được thêm, xóa, hạ cấp, mở rộng scope, thu hẹp scope hoặc diễn giải sai.

**Deliverable và Completion Rendering**

Mỗi Deliverable phải được render cùng các Intent, Context, Effective Constraints, Acceptance Criteria và Verification Requirements liên quan.

Completion Protocol phải giữ nguyên các trạng thái:

- completed
- partial
- blocked
- failed
- skipped

Failure và Partial-result Protocol phải yêu cầu AI Agent giữ lại kết quả hợp lệ, không báo `completed` sai, báo các ID chưa hoàn thành, blocker và execution uncertainty.

**Capability Handling**

- Capability `native` → tiếp tục.
- Capability `emulated` → chỉ tiếp tục khi Runtime Policy và contract cho phép; phải ghi rõ cách emulation.
- Capability `unavailable` chỉ ảnh hưởng thành phần không bắt buộc → có thể tiếp tục khi Output Contract cho phép và phải báo warning.
- Capability `unavailable` làm chặn Deliverable, Acceptance Criterion hoặc Verification Requirement bắt buộc → `render_status: unsupported`, `next_action: agent_router`.

Prompt Renderer không được tự chọn Agent thay thế, hạ cấp requirement hoặc thay đổi verification method.

**Context Window Handling**

Prompt Renderer phải ước lượng token trước khi chuyển tiếp.

Khi vượt context window:

1. Thực hiện compact lossless.
2. Loại bỏ bản sao byte-identical khi được phép.
3. Sử dụng reference hoặc tool-access khi capability và Runtime Policy cho phép.
4. Nếu vẫn vượt giới hạn, trả `requires_repackaging` cho Context Resolver.
5. Nếu nhiệm vụ cần nhiều execution step, chuyển Runtime Planner.

Prompt Renderer không được tự cắt Context, chia Intent, tạo execution step hoặc thay đổi thứ tự thực thi.

**Provenance và Traceability**

Runtime Metadata lưu đầy đủ Contract IDs, source references, hashes, Renderer version, Adapter version, Target Agent Profile, Preservation Manifest và correlation metadata.

Rendered Prompt phải giữ tối thiểu các ID cần cho AI Agent báo cáo:

- intent_id
- context_ref
- constraint_id
- deliverable_id
- criterion_id
- verification_id

**Validation Rules**

- Tất cả input contract phải hợp lệ và thuộc cùng `execution_ref`.
- Output Contract phải có `contract_status: ready` và `next_action: prompt_renderer`.
- Target Agent Profile và Agent Adapter phải có version hợp lệ.
- Mọi Intent phải được render và giữ quan hệ `precedes`.
- Mọi Deliverable, Acceptance Criterion và Verification Requirement bắt buộc phải được render.
- Mọi constraint `mandatory` phải giữ nguyên enforcement, scope và provenance.
- Mọi reference trong Prompt phải tồn tại trong upstream contracts.
- Không được xuất hiện requirement mới không có upstream origin.
- Token estimate phải nằm trong giới hạn an toàn.
- Mọi capability bắt buộc phải được hỗ trợ hoặc emulated hợp lệ.
- Response Schema phải tương thích Target Agent.
- Preservation Manifest phải đầy đủ và vượt qua validation.
- Chỉ dùng `render_status: ready` khi mọi validation bắt buộc đều đạt.

**Điều kiện chuyển tiếp**

Chỉ chuyển sang AI Agent khi:

```text
input_validation = valid
AND capability_evaluation = supported
AND render_status = ready
AND token_budget = valid
AND preservation_validation = passed
AND không còn blocking condition
AND next_action = ai_agent
```

Nếu Agent Adapter là bước tách riêng, Prompt Renderer Core dùng `next_action: agent_adapter`; chỉ Agent Adapter đã validation thành công mới được dùng `next_action: ai_agent`.

Runtime phải kiểm tra execution gate cuối trước khi gửi Prompt.

**Phân định trách nhiệm**

Prompt Renderer Core:

- Validate Canonical Execution Package.
- Tạo Canonical Prompt Model.
- Bảo toàn semantics và provenance.
- Ước lượng token.
- Tạo Preservation Manifest.

Agent Adapter:

- Chuyển Canonical Prompt Model sang format đặc thù Agent.
- Không chứa logic nghiệp vụ hoặc thay đổi semantics.

Runtime hoặc Orchestrator:

- Chọn Agent và Adapter.
- Quản lý execution, timeout, retry và kết quả.
- Kiểm tra gate cuối.
- Điều phối về Context Resolver, Runtime Planner hoặc Agent Router khi cần.

AI Agent:

- Thực thi yêu cầu.
- Tạo Deliverables.
- Thực hiện Verification được giao.
- Trả Completion Result và Verification Evidence.

**Những việc Prompt Renderer không được phép làm**

- Diễn giải lại User Request.
- Sửa Intent Graph Contract v1.
- Thay đổi thứ tự thực thi Intent.
- Sửa Context Resolution Contract v1 hoặc đọc thêm Knowledge Sources.
- Sửa Constraint Evaluation Contract v1.
- Thêm, xóa, hạ cấp hoặc diễn giải sai Effective Constraints.
- Sửa Output Contract v1.
- Tự tạo Deliverable, Acceptance Criterion hoặc Verification Requirement.
- Tự chọn AI Agent, model, adapter hoặc công cụ nghiệp vụ.
- Tự rút gọn ngữ nghĩa Context.
- Tự chia execution thành nhiều bước.
- Chứa logic nghiệp vụ.
- Thực thi yêu cầu hoặc Verification.
- Tuyên bố kết quả hoàn thành.

**Lý do**

Hybrid Prompt Rendering:

- Giữ semantic core độc lập với từng AI Agent.
- Tận dụng capability đặc thù thông qua Agent Adapter.
- Tránh trùng lặp logic giữa các Agent-specific Renderer hoàn chỉnh.
- Cho phép validation tự động trước execution.
- Bảo toàn Effective Constraints và provenance.
- Xử lý an toàn khi thiếu capability hoặc vượt context window.
- Phù hợp với DAG, Multi-Agent, AI Router và Workflow Automation trong tương lai.

**Hệ quả**

- Builder phải hỗ trợ Canonical Execution Package, Prompt Renderer Contract v1, Target Agent Profile và Constraint Preservation Manifest.
- Mỗi Agent family cần một Agent Adapter có version và compatibility rules.
- Runtime hoặc AI Router phải cung cấp Target Agent Profile và chịu trách nhiệm chọn Agent.
- Context Resolver phải cung cấp Context Payload runtime có reference và provenance.
- Runtime Planner chịu trách nhiệm chia execution khi cần nhiều bước.
- Runtime phải tách Rendered Prompt khỏi các contract nguồn và Completion Result.
- Prompt Library sau này phải xây dựng trên Canonical Prompt Model, không được trở thành nơi chứa logic nghiệp vụ hoặc thay thế AI Execution Strategy.
- Thay đổi không tương thích với contract này phải được quản lý bằng Decision mới hoặc ACR phù hợp.

---

## F-020 — Hybrid Prompt Asset Library và Prompt Asset Contract v1

**Trạng thái:** Accepted

**Bối cảnh**

F-009 yêu cầu chỉ xây Prompt Library sau khi Prompt Strategy được xác định.

F-010 mở rộng Prompt Strategy thành AI Execution Strategy và xác định Prompt chỉ là lớp chuyển đổi cuối trước khi gửi yêu cầu đến AI Agent.

F-019 xác lập Hybrid Prompt Rendering, Canonical Execution Package, Canonical Prompt Model, Prompt Renderer Core, Agent Adapter và Prompt Renderer Contract v1.

Framework cần một Prompt Library có khả năng tái sử dụng, versioning và thích ứng nhiều AI Agent mà không trở thành nơi chứa logic nghiệp vụ, không thay thế các upstream contracts và không làm thay đổi ranh giới giữa Prompt Renderer Core, Agent Adapter và Runtime.

**Quyết định**

Prompt Library sử dụng Hybrid Prompt Asset Model gồm ba lớp:

1. Canonical Prompt Assets.
2. Agent-specific Presentation Assets.
3. Composition Manifest.

Prompt Library là kho asset thụ động được Prompt Renderer Core sử dụng khi tạo Canonical Prompt Model.

Prompt Library không phải một bước thực thi độc lập trong AI Execution Strategy, không tự xử lý Canonical Execution Package và không tạo execution contract thay thế các contract phía trước.

**Canonical Prompt Assets**

Canonical Prompt Assets:

- Xây dựng trên Canonical Prompt Model của F-019.
- Trung lập với từng AI Agent.
- Xác định cấu trúc section, insertion point, structural fragment và response schema có thể tái sử dụng.
- Không chứa dữ liệu execution cụ thể.
- Không tạo hoặc thay đổi semantics của Intent, Context, Effective Constraints hoặc Output Contract.

**Agent-specific Presentation Assets**

Agent-specific Presentation Assets chỉ mô tả cách trình bày phù hợp với một agent family, instruction channel hoặc supported format.

Presentation Asset không được thay đổi nghĩa, ID, provenance, enforcement, scope hoặc thứ tự thực thi Intent.

Logic chuyển Canonical Prompt Model thành system message, user message, message set, API payload, attachment hoặc tool schema cụ thể thuộc Agent Adapter, không thuộc Prompt Library.

**Composition Manifest**

Composition Manifest khai báo:

- Asset cần compose.
- Dependency.
- Section order.
- Insertion point.
- Compatibility requirement.
- Override hoặc replacement được phép.

Composition Manifest không được chứa Intent routing, Agent selection, Prompt Decision Tree, workflow logic hoặc execution decision.

**Prompt Asset Taxonomy**

Canonical assets ban đầu:

- canonical_section_template
- canonical_structural_fragment
- instruction_precedence_template
- response_schema_template
- completion_protocol_template
- failure_protocol_template
- provenance_template

Presentation assets ban đầu:

- agent_presentation_fragment
- message_channel_mapping
- formatting_profile
- attachment_presentation
- tool_schema_presentation

Composition assets ban đầu:

- composition_manifest
- asset_bundle
- compatibility_profile

Test-only assets ban đầu:

- prompt_fixture
- composition_fixture
- snapshot_baseline
- invalid_asset_fixture

Prompt hoàn chỉnh không phải đơn vị lưu trữ chuẩn. Nó chỉ có thể tồn tại dưới dạng fixture, snapshot, example hoặc runtime artifact phục vụ test, audit, debugging và replay.

Rendering rule có ảnh hưởng semantics thuộc Prompt Renderer Core. Prompt Library chỉ lưu declarative presentation rule không thay đổi semantics.

**Prompt Asset Contract v1**

Prompt Asset là đơn vị lưu trữ, quản trị, versioning và compatibility của Prompt Library.

Prompt Asset Contract v1 gồm các trường bắt buộc:

- contract_version
- asset_id
- asset_version
- asset_type
- name
- description
- scope
- semantic_class
- lifecycle_status
- canonical_model
- compatibility
- bindings
- composition
- security
- provenance
- deprecation

`scope` sử dụng `global` hoặc `project`.

`semantic_class` sử dụng:

- structural
- presentation
- composition
- test_only

`lifecycle_status` sử dụng:

- draft
- review
- approved
- active
- deprecated
- retired
- blocked

Compatibility phải khai báo tối thiểu:

- Canonical Prompt Model version.
- Prompt Renderer version.
- Agent Adapter version.
- Agent family.
- Required capabilities.
- Supported formats.

Bindings phải khai báo allowed sources và insertion points.

Composition phải khai báo dependencies, conflicts, order constraints, override policy, inheritance hoặc replacement nếu có.

Provenance phải chứa owner, source reference, Decision reference, timestamps và content hash.

Deprecation phải cho phép khai báo replacement, sunset và migration note.

**Global và Project Prompt Library**

Global Workspace chứa Canonical Prompt Assets, cấu trúc chuẩn, presentation asset dùng chung theo agent family và Composition Manifest mặc định.

Project Workspace chỉ được chứa presentation preference, formatting profile, project-level Composition Manifest và extension hoặc replacement asset có provenance chính thức.

Project Prompt Asset không được chứa logic hoặc dữ liệu nghiệp vụ dự án.

**Override và Inheritance**

Không cho phép Project Workspace silent override Global Prompt Asset bằng cùng `asset_id`.

Project replacement phải:

- Có `asset_id` riêng.
- Khai báo asset và version được thay thế.
- Có provenance từ Project Decision hoặc Project Rule.
- Chỉ thay đổi field được allowlist cho phép.
- Không thay đổi semantic obligations.
- Vượt qua Semantic Preservation Test.

Override Policy sử dụng:

- locked
- presentation_only
- extend_only
- replace_with_approval
- project_replaceable

Asset biểu diễn Effective Constraints, Instruction Precedence, Required Deliverables, Acceptance Criteria, Verification Requirements, Completion Protocol, Failure Protocol và Provenance phải là `locked` hoặc `presentation_only`.

Inheritance không được dùng văn bản tự do, mỗi asset có tối đa một `extends` trực tiếp và inheritance graph không được có chu trình.

**Prompt Asset Selection**

Runtime hoặc AI Router chọn Target Agent và Agent Adapter, sau đó cung cấp Target Agent Profile và Rendering Policy.

Prompt Asset Selection thuộc Prompt Renderer Core và phải sử dụng deterministic compatibility matching dựa trên:

- Rendering Policy.
- Target Agent Profile.
- Agent family.
- Supported formats.
- Required capabilities.
- Canonical Prompt Model version.
- Prompt Renderer version.
- Agent Adapter version.
- Project overlay đã được phê duyệt.

Prompt Library chỉ cung cấp candidate asset phù hợp với truy vấn và không được tự chọn AI Agent, model hoặc adapter.

Prompt Library không có Prompt Decision Tree riêng.

Nếu không có asset tương thích, Prompt Renderer không được tự sửa asset hoặc hạ cấp requirement. Renderer phải trả `unsupported` và chuyển sang `agent_router` hoặc `stop` theo F-019 khi không còn candidate hợp lệ.

**Composition và Instruction Precedence**

Composition phải có kết quả xác định, stable ordering, không dependency cycle, không silent override, không duplicate mandatory section và không làm mất provenance hoặc scope.

Instruction Precedence phải giữ đúng thứ tự F-019:

1. Platform và Runtime Instructions.
2. Effective Constraints.
3. Execution Restrictions.
4. Intent execution order.
5. Deliverables.
6. Acceptance Criteria.
7. Verification Requirements.
8. Completion và reporting format.

Prompt Asset không được thay đổi precedence này.

**Insertion Points**

Canonical insertion points ban đầu:

- execution.identity
- execution.objective
- instruction.precedence
- intent.graph
- context.authorized
- constraints.effective
- deliverables.required
- acceptance.criteria
- verification.requirements
- execution.restrictions
- completion.protocol
- failure.protocol
- response.schema
- provenance.traceability

Prompt Asset chỉ xác định vị trí và cách trình bày. Dữ liệu tại insertion point phải lấy từ Canonical Execution Package và các nguồn runtime đã được F-019 cho phép.

**Constraint và Output Preservation**

Prompt Asset không được chứa Effective Constraint của execution cụ thể mà chỉ chứa insertion point và cấu trúc trình bày.

Prompt Asset không được thay đổi enforcement, scope, constraint ID hoặc provenance.

Prompt Asset không được chứa danh sách Deliverable, Acceptance Criteria hoặc Verification Requirements cố định. Các nội dung này chỉ được bind từ Output Contract v1.

Prompt Renderer vẫn phải tạo và validate Constraint Preservation Manifest theo F-019 sau composition.

**Versioning và Compatibility**

Prompt Asset sử dụng Semantic Versioning:

- MAJOR cho thay đổi không tương thích về schema hoặc semantics.
- MINOR cho bổ sung tương thích ngược.
- PATCH cho sửa lỗi trình bày không thay đổi semantics.

Không sử dụng asset chỉ dựa trên suy đoán tương thích. Compatibility phải được khai báo và validation rõ ràng.

**Lifecycle và Deprecation**

Chỉ Prompt Asset có trạng thái `active` mới được dùng mặc định trong production.

Asset `deprecated` chỉ được dùng trong compatibility window có cảnh báo.

Asset `retired` không được dùng cho render mới nhưng không được xóa khi còn execution record tham chiếu.

Asset thay thế phải khai báo `replacement_ref`, lý do, sunset và migration note.

**Provenance và Traceability**

Mỗi lần render phải ghi nhận Asset ID và version, Composition Manifest, content hash, Renderer version, Adapter version, Target Agent Profile, project overlay, upstream contract references, insertion-point binding map, Preservation Manifest và rendered artifact hash.

Mỗi phần được render phải truy vết được từ upstream contract element qua insertion point, Prompt Asset, Canonical Prompt section và Adapter mapping đến rendered location.

**Validation Rules**

Prompt Asset phải vượt qua:

- Schema Validation.
- Structural Validation.
- Semantic Validation.
- Compatibility Validation.
- Security Validation.
- Provenance Validation.

Validation phải xác nhận:

- Không có dependency hoặc inheritance cycle.
- Mọi insertion point và binding hợp lệ.
- Section order phù hợp F-019.
- Không tạo requirement mới.
- Không làm mất upstream requirement.
- Không thay đổi Intent hoặc thứ tự thực thi.
- Không thay đổi enforcement hoặc scope.
- Không làm mất ID hoặc provenance.
- Không chứa logic nghiệp vụ.
- Renderer, Adapter, Target Agent Profile, capability và format tương thích.

**Security và Prompt Injection**

Prompt Asset được coi là trusted configuration đã qua governance.

Context Payload và nội dung runtime được chèn vào được coi là untrusted data.

Framework phải sử dụng typed insertion points, escaping theo target format, instruction/data separation và placeholder allowlist.

Context Payload không được thay đổi template structure, section order hoặc Instruction Precedence và không được tự động biến thành system-level instruction.

Asset phải có content hash và provenance. Instruction-bearing asset phải được review. Production không được tải asset động từ nguồn chưa tin cậy.

Prompt Library không được tự giải quyết prompt injection hoặc instruction conflict trong Context Payload.

**Kiểm soát Logic nghiệp vụ và Unsourced Requirement**

Prompt Asset phải được kiểm tra bằng schema allowlist, static lint, origin validation và Semantic Preservation Test.

Mọi câu tạo obligation nhưng không phải cấu trúc cố định được F-019 hoặc F-020 cho phép và không có upstream binding phải bị từ chối.

**Testing Strategy**

Prompt Library phải hỗ trợ:

- schema validation
- composition test
- snapshot test
- semantic preservation test
- constraint preservation test
- adapter compatibility test
- provenance test
- prompt-injection test
- deprecation test
- regression test

Snapshot Test không thay thế Semantic Preservation Test hoặc Constraint Preservation Test.

**Production Gate**

Prompt Asset chỉ được dùng trong production khi:

```text
lifecycle_status = active
AND schema_validation = passed
AND structural_validation = passed
AND semantic_validation = passed
AND compatibility_validation = passed
AND security_validation = passed
AND composition_dependencies = resolved
AND provenance_validation = passed
AND regression_validation = passed
```

Sau composition, Prompt Renderer vẫn phải vượt qua toàn bộ execution gate của Prompt Renderer Contract v1 tại F-019.

**Những việc Prompt Library không được phép làm**

Prompt Library không được:

- Chứa logic nghiệp vụ.
- Diễn giải lại User Request.
- Tạo, sửa hoặc sắp xếp lại Intent.
- Chọn Knowledge Sources hoặc đọc thêm Context.
- Tạo hoặc thay đổi resolved facts.
- Áp dụng lại, thêm, xóa, hạ cấp hoặc diễn giải sai Effective Constraints.
- Chứa Effective Constraints của execution cụ thể.
- Tạo Deliverable, Acceptance Criterion hoặc Verification Requirement.
- Chứa danh sách đầu ra bắt buộc cố định thay Output Contract.
- Chọn AI Agent, model hoặc Agent Adapter.
- Điều phối execution hoặc chứa Prompt Decision Tree cho Agent routing.
- Thực thi yêu cầu hoặc Verification.
- Tuyên bố execution đã hoàn thành.
- Được sử dụng trực tiếp để bỏ qua Prompt Renderer trong production.
- Trở thành Single Source of Truth mới cho Intent, Context, Constraint hoặc Output.

**Lý do**

Hybrid Prompt Asset Model:

- Phù hợp trực tiếp với Hybrid Prompt Rendering tại F-019.
- Giữ Canonical Prompt semantics độc lập với từng AI Agent.
- Cho phép thích ứng cách trình bày mà không sao chép toàn bộ Prompt cho từng Agent.
- Giảm template drift và semantic drift.
- Cho phép versioning, compatibility validation, provenance và deprecation.
- Giữ ranh giới giữa Prompt Renderer Core, Agent Adapter và Runtime.
- Cho phép Global reuse và Project extension có quản trị.
- Giữ Framework độc lập với ChatGPT, Codex, Cline, Claude và AI Agent tương lai.

**Hệ quả**

- Builder phải hỗ trợ Prompt Asset Contract v1, Asset Registry, deterministic selection, composition và validation.
- Global Workspace phải cung cấp Canonical Prompt Assets và Composition Manifest mặc định.
- Project Workspace có thể cung cấp controlled overlay nhưng không được chứa business logic trong Prompt Asset.
- Prompt Renderer Core chịu trách nhiệm Asset Selection và composition.
- Runtime hoặc AI Router tiếp tục chịu trách nhiệm chọn Target Agent và Agent Adapter.
- Agent Adapter tiếp tục chịu trách nhiệm format conversion đặc thù Agent.
- Prompt Renderer Contract v1 và các contract F-015 đến F-018 không thay đổi.
- Prompt Library được coi là hoàn thành về kiến trúc sau Decision này; giai đoạn tiếp theo là Coding Standards.
- Thay đổi không tương thích với Decision này phải được quản lý bằng Decision mới hoặc ACR phù hợp.

---

## F-021 — Hybrid Coding Standards và Coding Rule Contract v1

**Trạng thái:** Accepted

**Bối cảnh**

F-002 xác định Global Workspace là nơi chứa chuẩn dùng chung.

F-014 xác định kiến trúc hiện hành gồm Global Workspace, Project Workspace, AI Workflow và AI Execution Strategy.

F-016 xác định Context Resolver chọn và nạp Knowledge Sources nhưng không tự áp dụng Standards hoặc Policies.

F-017 xác định Typed Constraint Engine hợp nhất Global Standards và Project Rules thành Effective Constraints có provenance.

F-018 và F-019 yêu cầu bảo toàn Effective Constraints qua Output Contract và Prompt Renderer đến AI Agent.

F-020 hoàn thành Prompt Library và xác định Coding Standards là giai đoạn tiếp theo.

Framework cần chuẩn hóa cách AI Agent tạo, sửa, refactor, review và kiểm chứng code trong nhiều dự án và technology stack mà không biến Standards thành văn bản tự do khó kiểm tra, không chứa logic nghiệp vụ và không thay đổi các contract F-015 đến F-020.

**Quyết định**

Coding Standards sử dụng Hybrid Coding Rule Pack gồm:

1. Pack Manifest.
2. Human-readable Guidance.
3. Atomic Coding Rules theo Coding Rule Contract v1.
4. Verification Mappings.
5. Checklists cho Self Review hoặc manual review.

Standard Pack là đơn vị phân phối, composition, compatibility và release.

Coding Rule là đơn vị applicability, provenance, enforcement, exception và traceability.

Pack và Rule đều có version. Pack version không thay thế Rule version.

**Vị trí trong kiến trúc**

Coding Standards không phải một bước thực thi độc lập và không trở thành khối kiến trúc cấp cao mới.

Luồng tích hợp:

```text
Global và Project Coding Standard Packs
        ↓
Coding Standards Catalog ở runtime
        ↓
Context Resolver chọn và nạp Standard Sources
        ↓
Constraint Engine chọn applicable Coding Rules
        ↓
Candidate Coding Constraints
        ↓
Precedence và Conflict Resolution
        ↓
Effective Constraints
        ↓
Output Contract
        ↓
Prompt Renderer
        ↓
AI Agent
        ↓
Verification và Self Review
```

Coding Standards Catalog chỉ là runtime index phục vụ discovery và không phải Single Source of Truth mới.

Context Resolver chịu trách nhiệm khám phá, chọn và nạp Standard Sources, ghi provenance, gaps, conflicts và nguồn lỗi thời.

Constraint Engine chịu trách nhiệm applicability matching ở cấp Coding Rule, tạo Candidate Coding Constraint, xử lý scope, authority, enforcement, precedence, conflict và exception trước khi tạo Effective Constraint theo F-017.

Coding Rule không trực tiếp trở thành Effective Constraint.

**Global và Project Coding Standards**

Global Workspace có thể chứa chuẩn dùng chung về language, framework, architecture, security, data, testing, documentation, performance, accessibility, observability, tooling và delivery.

Project Workspace có thể chứa quy tắc kỹ thuật phù hợp architecture và technology stack của dự án, Project Verification Mapping, approved override và temporary exception.

Project Coding Standard không được chứa logic nghiệp vụ, Product Requirement hoặc quyết định kiến trúc chưa được ghi nhận chính thức.

**Coding Standard Taxonomy**

Taxonomy ban đầu:

- language
- framework
- architecture
- security
- data
- testing
- documentation
- performance
- accessibility
- observability
- tooling
- delivery

**Coding Rule Contract v1**

Coding Rule Contract v1 gồm các trường bắt buộc:

- contract_version
- rule_id
- rule_version
- name
- description
- category
- scope
- lifecycle_status
- enforcement
- authority
- applicability
- obligation
- verification
- precedence
- compatibility
- security
- provenance
- deprecation

`scope` sử dụng `global` hoặc `project`.

`lifecycle_status` sử dụng:

- draft
- review
- approved
- active
- deprecated
- retired
- blocked

`enforcement` giữ nguyên taxonomy của F-017:

- mandatory
- approval_required
- advisory

`applicability` xác định Intent Type, Deliverable Type, Artifact Type, Project Type, technology stack, file type và conditions.

`obligation` xác định action, statement, prohibited actions và allowed exceptions.

`verification` xác định mode, methods, evidence, capability requirements và manual review checklist khi cần.

`precedence` xác định override policy, conflicts, inheritance, override và supersession.

`compatibility` xác định compatibility với Framework, contract, language, framework và tool capability liên quan.

`provenance` phải chứa source reference, Decision reference, owner, timestamps và content hash.

`deprecation` phải cho phép khai báo replacement, sunset và migration note.

Human-readable rationale, example và non-example có thể nằm trong Guidance và liên kết bằng `rule_id`. Constraint Engine chỉ sử dụng machine-readable fields để xác định obligation.

**Applicability và Effective Constraint**

Một Coding Rule chỉ trở thành Candidate Coding Constraint khi:

- Có lifecycle `active`.
- Schema và provenance hợp lệ.
- Standard Pack tương thích.
- Phù hợp Intent, Deliverable hoặc Artifact.
- Phù hợp technology stack, file scope và project type.
- Không nằm ngoài compatibility window.
- Không bị loại trừ bởi approved exception còn hiệu lực.

Constraint Engine tiếp tục xử lý precedence và conflict trước khi chuyển rule thành Effective Constraint.

Constraint `mandatory` không được tự hạ cấp.

Constraint `approval_required` chỉ được giải quyết bằng approval, Project Decision hoặc ACR phù hợp.

Constraint `advisory` có thể không áp dụng nhưng phải ghi nhận lý do khi rule đã được xác định là applicable.

**Override, Inheritance và Exception**

Không cho phép Project silent override Global Coding Rule bằng cùng `rule_id`.

Project override phải có ID riêng, khai báo rule và version bị override, có scope, tuân thủ override policy và có Project Decision hoặc ACR khi thay đổi nghĩa hoặc enforcement.

Override Policy ban đầu:

- locked
- extend_only
- project_configurable
- override_with_project_decision
- override_with_acr

Platform, safety, access và security baseline được đánh dấu `locked` không thể bị Project Rule ghi đè.

Inheritance không dùng văn bản tự do, mỗi rule có tối đa một `extends` trực tiếp và graph không được có chu trình.

Temporary Exception phải có ID, rule reference, scope, reason, approver, Decision reference, thời hạn, compensating controls và status.

Exception không được áp dụng cho rule `locked`, không được mặc định vĩnh viễn và phải được phê duyệt lại khi gia hạn.

**Conflict và Precedence**

Precedence phải xét đồng thời authority, enforcement, scope, constraint type, Decision status và approved exception.

Platform, safety và access policy không thể bị ghi đè.

Accepted Framework Decision không thể bị Project Rule thay đổi.

Project Coding Rule chỉ có thể khác Global Coding Rule khi override policy cho phép và governance đã hoàn tất.

Hai rule cùng authority và scope nhưng mâu thuẫn phải chuyển `clarify`, `decision_or_acr` hoặc `stop` theo F-017.

Constraint Engine không được tự tạo ngoại lệ hoặc tự chọn rule thắng khi conflict chưa được giải quyết.

Coding Standards không sử dụng Coding Decision Tree riêng trong v1. Applicability sử dụng deterministic declarative matching.

**Verification Mapping**

Coding Rule có thể ánh xạ đến formatter, lint, compiler, static analysis, unit test, integration test, security scan, runtime check hoặc manual review.

Rule khai báo Verification Method trung lập với tool. Tool hoặc provider cụ thể được ánh xạ bởi Environment hoặc Tool Profile.

Coding Rule không tự chọn hoặc chạy tool.

Output Contract ánh xạ Effective Coding Constraint thành Deliverable, Acceptance Criterion, Verification Requirement hoặc Execution Restriction phù hợp theo F-018.

Rule không thể kiểm tra tự động phải khai báo manual review, checklist và expected evidence phù hợp.

**Versioning, Compatibility và Lifecycle**

Standard Pack và Coding Rule sử dụng Semantic Versioning:

- MAJOR cho thay đổi không tương thích về schema, obligation, enforcement hoặc semantics.
- MINOR cho bổ sung tương thích ngược hoặc mở rộng applicability có kiểm soát.
- PATCH cho sửa mô tả hoặc metadata không thay đổi obligation.

Chỉ rule `active` được chọn mặc định trong production.

Rule `deprecated` chỉ được dùng trong compatibility window có cảnh báo.

Rule `retired` không được áp dụng cho execution mới nhưng phải được giữ khi còn execution record tham chiếu.

Replacement phải khai báo replacement reference, sunset và migration note.

**Validation và Testing Strategy**

Coding Standard Pack và Coding Rule phải hỗ trợ:

- schema validation
- unique ID validation
- dependency và inheritance validation
- applicability validation
- conflict test
- enforcement mapping test
- tool compatibility test
- provenance validation
- override và exception validation
- deprecation test
- duplicate rule detection
- business-logic contamination test
- unsourced-requirement test
- semantic preservation test
- regression test

Mọi obligation bắt buộc phải có provenance. Rule chứa domain behavior hoặc requirement không có nguồn phải bị từ chối hoặc chuyển về Knowledge/Decision chịu trách nhiệm.

**Security**

Standard Pack được coi là trusted configuration sau governance; Project overlay không mặc nhiên được tin cậy.

Rule phải có content hash và provenance, không được chứa secret hoặc executable command tùy ý.

Tool Mapping phải dùng allowlist và capability validation.

Context Payload và source code không được sửa hoặc điều khiển Coding Rule.

Production không được tải Standard Pack động từ nguồn chưa xác minh.

**Production Gate**

Coding Rule chỉ được dùng trong production khi:

```text
lifecycle_status = active
AND schema_validation = passed
AND applicability_validation = passed
AND conflict_validation = passed
AND compatibility_validation = passed
AND provenance_validation = passed
AND security_validation = passed
AND enforcement_mapping_validation = passed
AND override_exception_validation = passed
AND regression_validation = passed
```

Coding Rule chỉ trở thành Effective Constraint khi Production Gate đã đạt, applicability đã match, precedence đã resolved và Constraint Engine đã chấp nhận rule theo F-017.

**Những việc Coding Standards không được phép làm**

Coding Standards không được:

- Chứa logic nghiệp vụ hoặc Product Requirement.
- Thay thế Project Decisions hoặc Architecture Knowledge.
- Tạo requirement không có provenance.
- Diễn giải lại User Request hoặc sửa Intent Graph.
- Chọn Knowledge Sources thay Context Resolver.
- Tự trở thành Effective Constraint mà không qua Constraint Engine.
- Tự tạo Deliverable, Acceptance Criterion hoặc Verification Requirement.
- Tự chọn AI Agent, model, Agent Adapter, tool hoặc execution strategy.
- Tự chạy Verification hoặc tuyên bố code đạt chuẩn.
- Tự cấp approval, tạo override hoặc ngoại lệ.
- Thay đổi các contract F-015 đến F-020.
- Trở thành Single Source of Truth mới cho Intent, Context, Product, Architecture hoặc Decisions.

**Lý do**

Hybrid Coding Rule Pack:

- Kết hợp khả năng đọc và quản trị của human-readable guidance với khả năng validation của machine-readable rules.
- Giữ Constraint Engine độc lập với việc diễn giải văn bản tự do.
- Cho phép Global reuse và Project specialization có quản trị.
- Bảo toàn provenance từ Standard đến Effective Constraint, Output Contract, Prompt và Verification Evidence.
- Hỗ trợ nhiều ngôn ngữ, framework, AI Agent và tool trong tương lai.
- Hạn chế duplicate rule, rule drift và policy drift.
- Phù hợp với Hybrid Context Resolution, Typed Constraint Engine, Hybrid Output Contract, Hybrid Prompt Rendering và Hybrid Prompt Asset Model.

**Hệ quả**

- Builder phải hỗ trợ Coding Rule Contract v1, Standard Pack Manifest, Coding Standards Catalog, deterministic applicability matching và validation.
- Global Workspace phải cung cấp schema và các Standard Pack dùng chung.
- Project Workspace có thể cung cấp Project Rule, approved override và temporary exception theo governance.
- Context Resolver chọn Standard Sources; Constraint Engine chọn applicable rules và tạo Effective Constraints.
- Output Contract và Prompt Renderer tiếp tục sử dụng Effective Constraints theo F-017 đến F-019.
- Verification và Self Review sử dụng Verification Mapping nhưng không bị Coding Standards thay thế.
- Không tạo Coding Decision Tree riêng trong v1.
- Các contract F-015 đến F-020 không thay đổi.
- Coding Standards được coi là hoàn thành về kiến trúc sau Decision này; giai đoạn tiếp theo là Automation.
- Thay đổi không tương thích với Decision này phải được quản lý bằng Decision mới hoặc ACR phù hợp.

---

## F-022 — Hybrid Workflow Automation và Automation Contracts v1

**Trạng thái:** Accepted

**Bối cảnh**

F-007 xác định AI Workflow gồm tám bước từ Open Session đến Close Session.

F-008 xác định Session Contract gồm Objective, Scope, Constraints và Deliverables.

F-014 xác định kiến trúc hiện hành gồm Global Workspace, Project Workspace, AI Workflow và AI Execution Strategy; Automation là thành phần mở rộng, không phải khối kiến trúc cấp cao độc lập.

F-015 đến F-019 xác định pipeline từ Intent Detection đến Prompt Renderer. F-020 và F-021 tích hợp Prompt Library và Coding Standards mà không thay đổi nghĩa các contract phía trước.

Framework cần tự động hóa workflow và execution, hỗ trợ manual, scheduled, event-driven và conditional trigger, đồng thời không thay thế quyền quyết định của người dùng, không vượt governance, không tự cấp quyền và không làm Automation trở thành Single Source of Truth mới.

**Quyết định**

Automation sử dụng Hybrid Declarative Workflow Automation gồm:

1. Declarative Automation Definition làm nguồn định nghĩa workflow đã được quản trị.
2. Directed Acyclic Graph để biểu diễn dependency giữa các step.
3. State Machine để quản lý lifecycle của workflow và từng step tại runtime.
4. Controlled Action Adapter cho tích hợp imperative đã được allowlist và kiểm soát capability, permission, provenance.

Script tùy ý không phải đơn vị Automation chuẩn.

Automation Engine là logical component thuộc AI Workflow và runtime orchestration. Nó không phải khối kiến trúc cấp cao thứ năm và không thay đổi kiến trúc F-014.

Runtime thực thi capability, tool và AI execution. AI Router tiếp tục chịu trách nhiệm chọn AI Agent, model và adapter khi cần. Automation chỉ khai báo capability requirement và execution policy đã được phê duyệt.

**Hai contract riêng**

Automation sử dụng:

1. Automation Definition Contract v1.
2. Automation Run Contract v1.

Automation Definition là design-time artifact có version, lifecycle, compatibility, governance và provenance.

Automation Run là runtime record được tạo từ một Definition version đã pin. Run giữ state, event, approval, permission, checkpoint, retry, failure, compensation, output và audit trail.

Không hot-swap Definition version của Run đang hoạt động. Migration chỉ được thực hiện khi có migration plan, state mapping, compatibility validation và governance phù hợp.

Checkpoint và resume nằm trong Automation Run Contract v1 trong phiên bản đầu; chưa tạo Checkpoint Contract độc lập.

**Automation Definition Contract v1**

Contract gồm các trường bắt buộc:

- contract_version
- automation_id
- automation_version
- name
- description
- scope
- lifecycle_status
- entrypoints
- triggers
- inputs
- workflow
- session_policy
- intent_input_policy
- approval_policy
- permission_policy
- failure_policy
- retry_policy
- timeout_policy
- idempotency_policy
- concurrency_policy
- compensation_policy
- checkpoint_policy
- compatibility
- security
- governance
- provenance
- deprecation

`scope` sử dụng `global` hoặc `project`.

`lifecycle_status` sử dụng:

- draft
- review
- approved
- active
- deprecated
- retired
- blocked

`workflow` gồm steps, dependencies và transitions.

Mỗi step phải xác định ID, type, dependency, condition, input/output binding, required capability, permission, approval, timeout, retry, idempotency, compensation, verification và success/failure transition phù hợp.

Dependency graph không được có chu trình. Condition sử dụng typed declarative expression hoặc DSL giới hạn, không dùng executable code tùy ý.

**Automation Run Contract v1**

Contract gồm các trường bắt buộc:

- contract_version
- run_id
- automation_ref
- pinned_automation_version
- execution_refs
- session_ref
- trigger_instance
- initiator
- input_snapshot
- current_state
- step_runs
- approvals
- permission_evaluations
- capability_evaluations
- checkpoints
- events
- outputs
- verification_results
- failures
- retry_history
- compensation_history
- concurrency_control
- provenance
- audit_trail
- started_at
- updated_at
- completed_at
- result_status

Một Run có thể tạo nhiều `execution_ref`. Mỗi AI execution có `execution_ref` riêng và liên kết với cùng `run_id`.

Run phải pin Automation ID, Automation version, Definition content hash, trigger instance, Runtime hoặc Engine version, input snapshot hoặc immutable references và contract versions sử dụng.

**Trigger và Intent Detection**

Trigger taxonomy ban đầu:

- manual
- scheduled
- event
- conditional
- webhook
- workflow_completion
- automation_invocation

Automation không được tạo Intent Graph trực tiếp.

Manual trigger chuyển User Request vào Intent Detection theo pipeline F-015.

Scheduled hoặc event-driven trigger tạo Synthetic Request Envelope từ Trusted Event Envelope, approved trigger purpose, Session Context được phép sử dụng và provenance tương ứng. Synthetic Request Envelope phải được đánh dấu machine-originated và không được giả mạo thành lời người dùng.

Event phải được kiểm tra schema, source identity, signature khi có, replay window, event ID và duplicate detection trước khi tạo Run.

**Session Contract và execution_ref**

Automation được phép khởi tạo quy trình tạo Session Contract theo approved policy nhưng không được tự suy đoán Objective, Scope, Constraints hoặc Deliverables khi thiếu căn cứ.

Nếu thiếu quyền hoặc thiếu quyết định của người dùng, Run phải chuyển `waiting_approval`, `blocked` hoặc yêu cầu làm rõ.

`run_id` định danh toàn Automation Run; `execution_ref` định danh từng AI execution trong Run.

**Bảo toàn AI Execution Strategy**

Mọi AI execution do Automation khởi tạo vẫn phải đi qua:

```text
Intent Detection
↓
Intent Graph Contract v1
↓
Context Resolver
↓
Context Resolution Contract v1
↓
Typed Constraint Engine
↓
Constraint Evaluation Contract v1
↓
Output Contract v1
↓
Prompt Renderer Contract v1
↓
Runtime
↓
AI Agent
```

Automation không được bỏ qua, sửa hoặc thay đổi nghĩa bất kỳ upstream contract nào.

**Approval, Permission và Capability**

Approval sử dụng các trạng thái:

- not_required
- pending
- approved
- rejected
- expired
- revoked

Approval phải được lưu bền vững trong Automation Run và gắn với approver identity hoặc role, action scope, input hash, Definition version và thời hạn.

Im lặng, không phản hồi hoặc timeout không được coi là approval.

Permission và capability phải được đánh giá trước execution theo Definition, initiator, Runtime hoặc Environment, tool, Agent và approval requirement.

Automation không được tự cấp quyền, tự tạo approval hoặc yêu cầu AI Agent thực hiện thao tác Runtime không cho phép.

**Retry, Timeout và Idempotency**

Retry mặc định áp dụng ở cấp action hoặc step. Chỉ retry toàn workflow khi toàn bộ workflow được chứng minh idempotent.

Retry strategy ban đầu:

- none
- fixed_delay
- exponential_backoff
- bounded_custom

Retry chỉ áp dụng cho failure được phân loại retryable hoặc transient và phải có attempt limit, timeout và execution budget.

Mỗi side-effecting action phải có idempotency key hoặc cơ chế deduplication tương đương. Trigger instance phải có event hoặc invocation ID để ngăn duplicate Run và duplicate side effect.

**Failure, Partial Result và Compensation**

Automation phải phân loại failure về validation, compatibility, permission, approval, capability, timeout, contract, verification, security, duplicate event, concurrency, external dependency hoặc failure khác phù hợp.

Kết quả hợp lệ đã tạo phải được giữ lại. Run không được báo `completed` khi Deliverable hoặc Verification bắt buộc chưa đạt.

Rollback chỉ dùng cho transaction cục bộ thực sự hỗ trợ atomic rollback.

Cấp workflow sử dụng compensation như inverse action, restore snapshot, invalidate artifact, supersede artifact, corrective action hoặc manual recovery.

Compensation không mặc định bảo đảm khôi phục hoàn toàn trạng thái ban đầu.

**Checkpoint, Resume và Concurrency**

Checkpoint phải giữ Definition version đã pin, workflow và step state, completed outputs, contract references, approval state, retry counters, event cursor, idempotency keys, compensation state và runtime compatibility snapshot.

Resume chỉ được thực hiện khi Definition version còn truy cập được, transition hợp lệ, permission và approval còn hiệu lực, environment tương thích và input references chưa thay đổi trái policy.

Concurrency control phải hỗ trợ optimistic concurrency cho Run state, lease hoặc lock cho step cần độc quyền, unique trigger instance, resource lock khi cần, parallel step theo DAG và deterministic join policy.

**Global và Project Automation**

Global Workspace có thể chứa Automation schema, template, workflow pattern, approval, failure, retry, checkpoint và audit pattern dùng chung. Global Automation không được chứa logic nghiệp vụ dự án.

Project Workspace có thể chứa Project Automation Definition, project binding, configuration và workflow nghiệp vụ có provenance từ Product Knowledge, Project Decision hoặc nguồn có thẩm quyền.

Project Automation được phép biểu diễn hoặc tham chiếu business logic đã có nguồn nhưng không được phát minh requirement hoặc trở thành nguồn chuẩn mới.

Không cho phép Project silent override Global Automation bằng cùng `automation_id`.

Override Policy ban đầu:

- locked
- extend_only
- project_configurable
- override_with_project_decision
- override_with_acr

Project Decision được dùng cho thay đổi trong phạm vi dự án khi Global policy cho phép. ACR được yêu cầu khi thay đổi Framework semantics, locked policy hoặc Accepted Contract.

**Automation Catalog**

Automation Catalog hoặc Registry tồn tại ở runtime để phục vụ discovery, version resolution, lifecycle filtering, compatibility matching, trigger routing và provenance lookup.

Catalog chỉ là runtime index hoặc projection, không phải Single Source of Truth và không thay thế Automation Definition trong Global hoặc Project Workspace.

Không tạo Automation Decision Tree riêng trong v1. Trigger matching, condition evaluation và state transition sử dụng deterministic declarative rules.

**Nested Automation và Runaway Protection**

Automation có thể kích hoạt Automation khác khi Definition và policy cho phép, đồng thời phải có explicit dependency, allowlist, cycle detection, depth limit, execution budget, rate limit, correlation ID, separate run ID, permission re-evaluation và kill switch.

Automation không được gọi chính nó trực tiếp hoặc gián tiếp.

**Security và Untrusted Input**

Definition chỉ chứa secret reference; secret được resolve just-in-time theo least privilege và không được ghi vào Prompt, log, checkpoint hoặc audit payload.

Event payload, webhook content, file content và Context Payload được coi là untrusted data.

Framework phải validate schema và source, phân tách instruction khỏi data, sử dụng typed binding và allowlist, không cho untrusted data thay đổi workflow structure, permission hoặc approval và phải bảo toàn content hash cùng provenance.

Automation không được dùng untrusted input để bỏ qua Intent Detection, Context Resolver, Constraint Engine hoặc Prompt Renderer.

**Versioning, Compatibility và Lifecycle**

Automation Definition sử dụng Semantic Versioning:

- MAJOR cho thay đổi không tương thích về schema, workflow semantics, permission, approval hoặc state model.
- MINOR cho bổ sung tương thích ngược.
- PATCH cho sửa metadata hoặc lỗi không thay đổi semantics.

Run đang hoạt động tiếp tục sử dụng pinned Definition version.

Definition `deprecated` không được dùng mặc định cho Run mới và chỉ được dùng trong compatibility window có cảnh báo.

Definition `retired` không được tạo Run mới nhưng phải được giữ khi còn Run tham chiếu.

Nếu Agent, tool hoặc environment không tương thích, Automation phải chuyển Runtime Planner, AI Router, `blocked` hoặc `failed` theo policy; không được tự hạ cấp requirement hoặc tự chọn Agent thay thế.

**Provenance và Audit**

Audit trail phải ghi Definition identity và hash, Run và execution references, trigger, input references, state transitions, condition result, permission, capability, approval, Agent, Adapter, tool, environment, contract references, output, Verification Evidence, Completion Result, retry, timeout, checkpoint, resume, failure và compensation event.

Audit trail là execution evidence, không phải Knowledge Source hoặc Single Source of Truth mới.

**Testing Strategy**

Automation phải hỗ trợ tối thiểu:

- schema validation
- graph và cycle validation
- state transition test
- trigger test
- condition test
- permission test
- approval test
- retry và idempotency test
- duplicate event và replay test
- timeout test
- compensation test
- checkpoint và resume test
- concurrency và race-condition test
- version pinning và migration test
- compatibility test
- security và secret-leakage test
- prompt-injection và untrusted-event test
- business-logic contamination test
- unsourced-requirement test
- provenance và audit test
- Output Contract và Verification linkage test
- partial-result test
- deprecation test
- nested-automation runaway test
- regression test

**Production Gate**

Automation Definition chỉ được dùng trong production khi:

```text
lifecycle_status = active
AND schema_validation = passed
AND graph_validation = passed
AND state_transition_validation = passed
AND trigger_validation = passed
AND condition_validation = passed
AND permission_validation = passed
AND approval_validation = passed
AND compatibility_validation = passed
AND security_validation = passed
AND provenance_validation = passed
AND idempotency_validation = passed
AND timeout_retry_validation = passed
AND compensation_validation = passed
AND concurrency_validation = passed
AND regression_validation = passed
AND governance_approval = valid
```

Mỗi Run vẫn phải vượt qua trigger trust, permission, capability, approval, contract, execution và verification gate tương ứng.

**Những việc Automation không được phép làm**

Automation không được:

- Trở thành khối kiến trúc cấp cao thứ năm.
- Trở thành Single Source of Truth mới.
- Sửa hoặc thay đổi nghĩa của Decision hoặc Accepted Contract.
- Tạo hoặc sửa Intent Graph trực tiếp.
- Bỏ qua Context Resolver, Constraint Engine, Output Contract hoặc Prompt Renderer.
- Tự cấp permission, approval, override hoặc exception.
- Coi im lặng hoặc timeout là approval.
- Tự chọn AI Agent, model hoặc adapter khi quyền đó thuộc Runtime hoặc AI Router.
- Tạo logic nghiệp vụ hoặc requirement không có nguồn.
- Dùng untrusted event hoặc Context Payload làm instruction điều khiển workflow.
- Chứa secret value.
- Retry vô hạn, recursion không giới hạn hoặc chạy ngoài execution budget.
- Tuyên bố completed khi Deliverable hoặc Verification bắt buộc chưa đạt.
- Tự thay đổi Definition version của Run đang hoạt động.
- Thay đổi các contract F-015 đến F-021.

**Lý do**

Hybrid Declarative Workflow Automation:

- Kết hợp dependency model rõ ràng của DAG với lifecycle control của State Machine.
- Tách design-time definition khỏi runtime state.
- Hỗ trợ approval, permission, retry, timeout, checkpoint, resume, compensation và audit.
- Giữ AI Execution Strategy và các Accepted Contract làm nguồn semantics.
- Hỗ trợ ChatGPT, Codex, Cline, Claude và AI Agent tương lai.
- Giữ Framework độc lập với scheduler, CI/CD, tool provider và Agent cụ thể.
- Hạn chế imperative script, privilege escalation, duplicate side effect và runaway execution.

**Hệ quả**

- Builder phải hỗ trợ Automation Definition Contract v1 và Automation Run Contract v1.
- Builder phải cung cấp schema validator, graph validator, state transition engine, trigger adapter, action adapter, durable run store, approval store, idempotency control, checkpoint/resume, audit và production gate.
- Global Workspace phải cung cấp Automation schema, template và reusable pattern.
- Project Workspace có thể cung cấp Project Automation và controlled override theo governance.
- Runtime hoặc AI Router tiếp tục chọn Agent và Adapter.
- Mọi AI execution tiếp tục sử dụng các contract F-015 đến F-019; Prompt Library và Coding Standards tiếp tục tích hợp theo F-020 và F-021.
- Các contract F-015 đến F-021 không thay đổi.
- Automation được coi là hoàn thành về kiến trúc sau Decision này; giai đoạn tiếp theo là Builder Specification.
- Thay đổi không tương thích với Decision này phải được quản lý bằng Decision mới hoặc ACR phù hợp.

---

## F-023 — Technology-Neutral Builder Specification, Modular Package Architecture và Reference Implementation Strategy

**Trạng thái:** Accepted

**Bối cảnh**

F-014 xác định bốn khối kiến trúc cấp cao của Framework.

F-015 đến F-019 xác định AI Execution Strategy từ Intent Detection đến Prompt Renderer. F-020, F-021 và F-022 hoàn thành Prompt Library, Coding Standards và Automation về kiến trúc.

Các Decision và Contract đã xác định semantics nhưng chưa chỉ rõ đầy đủ module boundary, interface, schema, validation, registry, storage, compatibility, security, observability, testing và cách tổ chức implementation.

Framework cần một Builder Specification đủ rõ để Codex hoặc một đội phát triển có thể xây dựng Framework mà không phải tự sáng tác lại kiến trúc, đồng thời không làm implementation detail trở thành nguồn thay thế FRAMEWORK_SPEC.md hoặc FRAMEWORK_DECISIONS.md.

**Quyết định**

Builder sử dụng:

1. Technology-neutral Builder Specification làm đặc tả hướng triển khai.
2. Monorepo nhiều package với dependency boundary có thể kiểm tra.
3. Reference implementation để chứng minh specification có thể triển khai.
4. Modular monolith làm deployment model ban đầu của reference implementation.
5. Contract-first development.
6. End-to-end vertical slice với Mock Agent trước khi tích hợp AI Agent thật.
7. Conformance Test Suite bắt buộc đối với implementation tuyên bố tương thích Framework.

Builder Specification không phải Single Source of Truth mới và không thay đổi nghĩa F-001 đến F-022.

**Phân vùng trách nhiệm**

Builder phân biệt:

- Framework Core.
- Runtime.
- Adapter và Plugin.
- Registry và Catalog.
- Storage.
- Tooling và Conformance.

Framework Core chứa contract models, deterministic engine, semantic validation, compatibility và provenance logic. Core không phụ thuộc AI provider, Runtime, database driver, scheduler, filesystem, network hoặc platform SDK cụ thể.

Runtime điều phối execution, Automation Run, permission, approval, capability, secret, verification, storage coordination và telemetry.

AI Router thuộc Runtime và chịu trách nhiệm chọn Agent, model và adapter. Automation chỉ khai báo capability requirement và không tự chọn Agent.

Registry và Catalog là runtime index hoặc projection phục vụ discovery, version resolution, compatibility và routing. Chúng không phải Single Source of Truth và không thay thế governed artifact trong Global hoặc Project Workspace.

**Contract serialization và schema**

Canonical serialization sử dụng JSON UTF-8.

Normative contract schema sử dụng JSON Schema Draft 2020-12.

YAML được phép dùng để human-authoring nhưng phải được chuyển thành canonical JSON trước validation, hashing và execution.

OpenAPI chỉ dùng để mô tả Runtime API hoặc transport binding. Protocol Buffers không phải normative contract format trong v1 nhưng có thể được sử dụng làm transport optimization nếu giữ nguyên semantics và vượt qua conformance test.

Mỗi contract schema phải có stable schema ID, semantic version, validation rules, compatibility declaration, valid và invalid test vectors, canonical content hash và Decision traceability.

**Validation và Contract Version Registry**

Validation pipeline gồm syntax, schema, structural, semantic, cross-contract, compatibility, provenance và execution gate validation.

Contract Version Registry lưu metadata và projection cho contract identity, version, lifecycle, compatibility, migration, hash và traceability. Registry không được trở thành nguồn semantics mới.

Validation failure phải trả typed error và không được âm thầm sửa contract.

**Identifier, error và state model**

Identifier là opaque string. Builder chuẩn hóa tối thiểu `contract_id`, `execution_ref`, `run_id`, `session_ref`, `source_ref`, `artifact_ref`, `correlation_id` và `causation_id`.

Framework sử dụng typed error model có category, severity, retryability, module, reference và redacted details.

Session, AI Execution, Automation Run và Automation Step giữ state machine riêng. Common lifecycle classification chỉ dùng để quan sát và tích hợp, không thay thế state taxonomy đã Accepted.

**Provenance và Audit**

Mỗi derived artifact phải giữ source reference, content hash, producing module và version, contract/schema version, actor hoặc runtime identity, timestamp và execution/run/session reference phù hợp.

Audit event phải ghi actor, action, outcome, correlation, causation, input/output reference, policy reference và integrity metadata.

Audit cho Automation, permission, approval, security và side effect phải append-only về mặt logic. Correction tạo event mới thay vì ghi đè lịch sử.

Audit trail là execution evidence, không phải Knowledge Source hoặc Single Source of Truth.

**Storage, transaction, idempotency và concurrency**

Builder sử dụng port cho Definition, Contract, Run, Checkpoint, Artifact, Audit, Approval, Idempotency Ledger, Registry Projection và Cache.

Secret Store nằm ngoài Framework storage thông thường.

Versioned contract, Definition, Prompt Asset, Coding Rule, input snapshot, evidence, approval record và audit event là immutable artifact. Run projection, Registry projection, cache, lease và lock là mutable runtime state.

Atomic transaction chỉ được cam kết trong local consistency boundary. Không giả định distributed transaction xuyên AI Agent, tool hoặc provider. Workflow sử dụng outbox hoặc inbox, idempotency, retry có giới hạn và compensation.

Side-effecting command phải có idempotency key hoặc deduplication tương đương. Run state sử dụng optimistic concurrency; step độc quyền sử dụng lease hoặc lock có thời hạn khi cần.

**Permission, approval, secret và trust boundary**

Framework Core chỉ biểu diễn requirement và policy. Runtime xác thực actor, đánh giá environment permission, kiểm tra capability, resolve approval và enforce execution gate.

Approval phải explicit, durable và gắn với identity hoặc role, action scope, input hash, version và expiry. Im lặng, không phản hồi hoặc timeout không phải approval.

Contract và Definition chỉ chứa secret reference. Secret được resolve just-in-time theo least privilege và không được ghi vào Prompt, Context Payload, log, trace, checkpoint, error hoặc audit payload.

User content, event, webhook, Knowledge content, file, Context Payload, tool output và AI Agent output được coi là untrusted data. Untrusted data không được thay đổi workflow structure, permission, approval hoặc adapter selection.

**Adapter và Plugin model**

Builder cung cấp capability-based Adapter SDK cho Agent, Tool, Trigger, Storage, Knowledge Source và Verification.

V1 sử dụng static registration hoặc explicit allowlist. Dynamic plugin loading chỉ được thêm khi có integrity verification, isolation, lifecycle governance và security review.

ChatGPT, Codex, Cline và Claude được hỗ trợ qua Target Agent Profile, capability model, rendering profile và Agent Adapter. Framework Core không hard-code platform cụ thể.

**Global và Project configuration**

Configuration resolution tuân theo locked Framework default, Global policy, Project configuration được phép, approved Project Decision hoặc override, Session configuration được phép, Runtime binding và explicit approval cho action cụ thể.

Override sử dụng typed merge strategy và phải giữ authority, provenance, scope, compatibility và resolution trace. Conflict không giải quyết được phải chuyển `clarify`, `decision_or_acr` hoặc `stop` phù hợp.

**Compatibility, migration và deprecation**

Migration không sửa immutable artifact. Migration tạo version mới có provenance và validation result.

Automation Run đang hoạt động tiếp tục dùng pinned Definition version. Runtime migration chỉ được thực hiện khi có migration plan, state mapping, compatibility validation và governance phù hợp.

Deprecated version phải có compatibility window và retirement condition. Retired artifact không được dùng cho execution mới nhưng phải được giữ khi còn reference hợp lệ.

**Observability và Conformance**

Builder phải hỗ trợ structured log, metric, distributed trace và audit. Log, metric và trace không thay thế audit.

Conformance Test Suite kiểm tra tối thiểu schema, semantic behavior, cross-contract linkage, constraint preservation, provenance, audit, state transition, error, compatibility, security, Adapter contract, Automation Definition, Automation Run và Production Gate.

Implementation không được tuyên bố production-ready nếu chưa vượt qua conformance, security, secret leakage, permission, approval, idempotency, concurrency, recovery, migration, provenance, audit và operational readiness gate.

**Implementation phases**

Builder được triển khai theo phase:

1. Builder Baseline.
2. Contract Foundation.
3. End-to-End Vertical Slice.
4. Workspace và Catalog.
5. Runtime Foundation.
6. Automation.
7. Reference Adapter.
8. Production Hardening.

Minimum Viable Framework gồm Session Contract, Linear Intent Graph, deterministic Context Resolver bằng catalog fixture, Typed Constraint Engine, Output Contract Builder, Prompt Renderer Core, Agent Adapter, Mock Agent, contract validation, provenance, audit tối thiểu, in-memory storage và conformance test cho F-015 đến F-019.

Automation trong Minimum Viable Framework chỉ cần Definition validation và một Run nhỏ gọi AI execution vertical slice. AI Agent, scheduler, approval provider và secret provider có thể dùng Mock trong phase đầu.

**Technology stack**

Builder Specification không chọn .NET, TypeScript hoặc Python làm normative technology.

Technology stack của reference implementation phải được xác định trong một Reference Implementation Technology Profile riêng sau F-023. Lựa chọn stack không được thay đổi normative contract hoặc module boundary.

**Governance**

Decision mới được dùng cho lựa chọn implementation architecture mới không thay đổi semantics đã Accepted.

ACR được yêu cầu khi thay đổi, thay thế hoặc làm suy yếu Accepted Decision, locked policy hoặc Accepted Contract.

Nếu implementation phát hiện kiến trúc không khả thi, implementation phải dừng, ghi evidence và đề xuất Decision hoặc ACR; không được tự sửa semantics.

**Lý do**

Phương án này:

- Giữ Framework độc lập với công nghệ và platform cụ thể.
- Tạo boundary đủ rõ để nhiều đội hoặc implementation cùng tuân thủ.
- Cho phép khởi động đơn giản bằng modular monolith nhưng vẫn có khả năng tách package hoặc process sau.
- Chứng minh kiến trúc bằng reference implementation mà không biến code thành nguồn chuẩn mới.
- Giảm rủi ro xây distributed system quá sớm.
- Cho phép kiểm chứng F-015 đến F-022 bằng conformance suite.
- Hỗ trợ triển khai từng phase và tạo giá trị sớm qua vertical slice.

**Hệ quả**

- Builder Specification được coi là hoàn thành về kiến trúc sau Decision này.
- FRAMEWORK_SPEC.md phải chứa module boundary, schema strategy, common models, storage, security, observability, testing, repository structure, phases và Minimum Viable Framework.
- Builder repository phải tổ chức theo monorepo nhiều package và enforce dependency direction.
- Reference implementation ban đầu dùng modular monolith và Mock Agent cho vertical slice.
- Conformance Test Suite là deliverable bắt buộc.
- Registry và Catalog không được trở thành Single Source of Truth.
- AI Router thuộc Runtime.
- Technology stack được quyết định riêng trong giai đoạn tiếp theo.
- F-001 đến F-022 và các Accepted Contract không thay đổi.
- Thay đổi không tương thích với Decision này phải được quản lý bằng Decision mới hoặc ACR phù hợp.
---

## F-024 — Framework Deliverable Profile và Template Package Specification

**Trạng thái:** Accepted

**Bối cảnh**

ACR-003 xác lập Documentation & Template Framework là sản phẩm chính của AI Development Framework nhưng chưa xác định đầy đủ bộ deliverable tối thiểu, cấu trúc package, trách nhiệm từng file, dependency và điều kiện hoàn thành Framework v1.

Framework cần một Deliverable Profile đủ rõ để người dùng và AI Agent biết chính xác phải đọc, sử dụng và cập nhật tài liệu nào, đồng thời giữ sản phẩm nhẹ, độc lập technology stack và không đưa Executable Reference Implementation trở lại critical path.

**Quyết định**

Framework v1 được phân phối dưới dạng Documentation & Template Package gồm:

1. Root Guide.
2. Global Workspace Package.
3. Project Workspace Template Package.
4. Guides Package.
5. Tiêu chí review, pilot và release ở mức tài liệu.

Deliverable được phân loại thành:

- `required`: bắt buộc để Framework v1 hoàn thành và phát hành.
- `recommended`: nên có hoặc nên sử dụng nhưng không chặn mọi trường hợp sử dụng.
- `conditional`: bắt buộc khi project type hoặc task type thuộc phạm vi áp dụng.
- `optional`: có thể bổ sung mà không ảnh hưởng compatibility cơ bản.
- `future_extension`: hướng mở rộng không thuộc critical path của Framework v1.

**Cấu trúc package chuẩn**

```text
AI-DEVELOPMENT-FRAMEWORK/
├── README.md
├── global-workspace/
│   ├── standards/
│   ├── workflows/
│   ├── templates/
│   │   └── prompts/
│   ├── checklists/
│   └── skills/                 # Optional; chỉ tạo khi có skill thực tế
├── project-template/
│   ├── README.md
│   ├── PRODUCT.md
│   ├── DESIGN.md
│   ├── ROADMAP.md
│   ├── DECISIONS.md
│   ├── WORKING_CONTEXT.md
│   ├── TASKS.md
│   ├── CHANGELOG.md
│   └── AGENTS.md
└── guides/
```

Không tạo thư mục rỗng chỉ để giữ chỗ. `skills/` chỉ được tạo khi có deliverable skill thực tế đã xác định scope, dependency và fallback.

**Framework Deliverable Profile**

Các deliverable `required` của Framework v1 gồm:

- Root `README.md` làm điểm vào, quick start và document map.
- Documentation Standards.
- Coding Standards trung lập technology stack.
- AI Working Standards.
- Knowledge Management Standards.
- Testing và Review Standards.
- Security và Privacy Guidance phù hợp với dự án cá nhân.
- Session Workflow.
- AI Execution Workflow.
- Knowledge Lifecycle Workflow.
- Documentation Update Workflow.
- Project Workspace Template gồm chín file đã Accepted tại F-003.
- Prompt Templates cho các workflow cốt lõi.
- Start Project, Open Session, Close Session, Documentation Review và Release hoặc Handover Checklists.
- Hướng dẫn khởi tạo, tiếp tục, bàn giao và migration dự án.
- Hướng dẫn sử dụng với ChatGPT, Codex, Cline và Claude.

Các deliverable `conditional` gồm:

- Frontend Design Standards.
- Frontend Design Workflow.
- Frontend Brief Template.
- Frontend Design và Frontend Review Prompt Templates.
- Frontend UI, Responsive, Accessibility và Visual QA Checklists.
- Hướng dẫn sử dụng Impeccable.
- Code Review Checklist khi task tạo, sửa, refactor hoặc review code.

Các deliverable frontend là bắt buộc đối với package Framework v1 để hỗ trợ project có frontend, nhưng chỉ được áp dụng trong project hoặc task có frontend.

Automation Guidance là `recommended`. Nội dung này biểu diễn F-022 bằng workflow, template, checklist, approval gate và pattern thủ công hoặc bán tự động; không yêu cầu Automation Engine chạy thật.

Skills là `optional`.

Machine-readable schema, Runtime Orchestrator, AI Router, persistent storage, Adapter SDK, CLI, Web API, database, message broker, durable workflow engine, Conformance Test Suite implementation và Executable Reference Implementation là `future_extension`.

**Global Workspace Package**

`standards/` chứa chuẩn dùng chung, độc lập dự án và technology stack. Baseline gồm:

- Documentation Standards.
- Coding Standards.
- AI Working Standards.
- Knowledge Management Standards.
- Testing và Review Standards.
- Security và Privacy Guidance.
- Frontend Design Standards.

Global Coding Standards không chọn .NET, TypeScript, Python, database hoặc frontend stack làm chuẩn chung. Project Workspace được phép bổ sung stack-specific rule có provenance và governance phù hợp.

`workflows/` chứa:

- Session Workflow.
- AI Execution Workflow.
- Knowledge Lifecycle Workflow.
- Documentation Update Workflow.
- Frontend Design Workflow.
- Automation Guidance.

`templates/` chứa reusable input hoặc document template dùng chung. `templates/prompts/` là vị trí chuẩn duy nhất của Prompt Templates. Không tạo thư mục `prompts/` song song ở root hoặc trong Project Workspace.

`checklists/` chứa checklist ngắn, action-oriented và dùng trạng thái `Pass`, `Fail` hoặc `Not applicable` cùng evidence khi cần. Checklist không sao chép toàn bộ Standard.

`skills/` là extension point tùy chọn cho skill thực tế. Skill phải có scope, capability assumption, dependency, giới hạn và fallback; không được trở thành dependency bắt buộc của mọi project.

Global Workspace không được chứa Product Requirement, business logic, lỗi, database schema, Roadmap, task, Working Context, Decision kỹ thuật hoặc secret riêng của project.

Mở rộng Global Workspace phải dùng deliverable mới hoặc version mới có tên và trách nhiệm rõ. Không silent override nội dung hiện hành và không thay đổi project đang dùng version cũ nếu chưa có migration guidance.

**Project Workspace Template Package**

Giữ nguyên chín file đã Accepted tại F-003; không bổ sung file bắt buộc mới trong Framework v1:

- `README.md`: điểm vào, trạng thái khái quát, quick start và document map; không thay thế Product, Design hoặc Tasks.
- `PRODUCT.md`: Single Source of Truth cho Product Requirement và intended behavior; không chứa implementation detail hoặc task tạm thời.
- `DESIGN.md`: Single Source of Truth cho kiến trúc và thiết kế hiện hành; không chứa backlog, session log hoặc requirement chưa được chấp thuận.
- `ROADMAP.md`: Single Source of Truth cho milestone, dependency và trạng thái lộ trình; không xác lập Decision.
- `DECISIONS.md`: Historical Record cho Project Decision và lý do; không bị viết lại như Living Document.
- `WORKING_CONTEXT.md`: Single Source of Truth cho trạng thái làm việc hiện tại, blocker và next action; không chứa toàn bộ lịch sử hoặc knowledge lâu dài.
- `TASKS.md`: Single Source of Truth cho actionable work item; không thay thế Product Requirement, Design hoặc Roadmap.
- `CHANGELOG.md`: Single Source of Truth cho thay đổi đã hoàn thành hoặc phát hành đáng chú ý; không chứa work-in-progress hoặc decision rationale.
- `AGENTS.md`: Single Source of Truth cho cách AI Agent làm việc trong project, read order, command, boundary và project-specific rule; không chứa secret hoặc sao chép Product Requirement.

Quan hệ trách nhiệm:

```text
PRODUCT.md         → phải xây gì và hành vi mong muốn
DESIGN.md          → hệ thống hiện hành được thiết kế thế nào
DECISIONS.md       → vì sao lựa chọn được chấp thuận
ROADMAP.md         → milestone đi theo thứ tự nào
TASKS.md           → việc cụ thể còn phải làm
WORKING_CONTEXT.md → hiện đang ở đâu và tiếp theo là gì
CHANGELOG.md       → đã hoàn thành hoặc phát hành gì
AGENTS.md          → AI được làm việc theo cách nào
README.md          → điểm vào và bản đồ đến các nguồn trên
```

File phải được đọc theo Intent và Knowledge Source authority, không dùng một thứ tự cố định cho mọi task. File được cập nhật khi thông tin thuộc trách nhiệm của file thay đổi; không sao chép cùng một fact thành nhiều Single Source of Truth.

**AI Workflow và Contract Representation**

F-007, F-008 và F-015 đến F-022 được hiện thực trong Framework v1 bằng tài liệu và template như sau:

- Session Contract → section hoặc worksheet gồm Objective, Scope, Constraints và Deliverables.
- Intent Detection và Intent Graph → danh sách Intent có ID, objective, confidence, ambiguity và dependency; Linear Graph là mặc định.
- Context Resolution → read map theo Intent, source authority, selected source, resolved fact, gap, conflict và provenance.
- Constraint Evaluation → bảng constraint có source, type, scope, enforcement, conflict, approval và next action.
- Output Contract → deliverable, Acceptance Criteria, Verification Requirement, Completion Protocol và partial hoặc failure handling.
- Prompt Rendering → composition template giữ nguyên Intent, authorized Context, Effective Constraints, Deliverables và Verification.
- Coding Standards → Global baseline, Project rule, applicability và review checklist.
- Automation → declarative workflow guidance, approval gate và fallback thủ công hoặc bán tự động.

Việc biểu diễn bằng tài liệu phải giữ semantics và ranh giới của Accepted Contract nhưng không mặc nhiên yêu cầu JSON, schema, Runtime module hoặc persistent record.

Workflow phải có lớp hướng dẫn đơn giản cho người không phải Dev chuyên nghiệp. Tên contract và mapping kỹ thuật có thể nằm trong phần nâng cao, không bắt buộc người dùng viết JSON hoặc YAML để sử dụng Framework.

**Prompt Template Package**

Prompt Templates tối thiểu gồm:

- `start-project.md`
- `continue-session.md`
- `handover-session.md`
- `analyze-requirement.md`
- `design-solution.md`
- `implement-task.md`
- `fix-bug.md`
- `review-code.md`
- `update-documentation.md`
- `frontend-design.md`
- `frontend-review.md`

Các Prompt Template trên là manual entry hoặc composition template dành cho người và AI Agent. Chúng không phải Rendered Prompt runtime, không thay thế Prompt Asset Contract v1 và không được chứa Product Requirement hoặc business logic cố định.

Mỗi Prompt Template phải xác định tối thiểu:

- Khi nào sử dụng.
- Input cần cung cấp.
- Knowledge Sources phải đọc.
- Session Contract.
- Authorized Intent hoặc goal.
- Context gap và ambiguity handling.
- Constraints, permission và approval boundary.
- Deliverables và Acceptance Criteria.
- Verification.
- File được phép cập nhật.
- Completion, partial, blocked và failure reporting.
- Agent capability note hoặc liên kết sang Agent-specific Guide.

Không hợp nhất các template khi Intent, read set, acceptance, verification hoặc completion protocol khác nhau. Frontend Design Prompt được phép bao phủ cả thiết kế mới và cải tiến frontend; không cần template `improve-frontend.md` riêng.

**Frontend Design và Impeccable Package**

Package frontend gồm:

- Frontend Design Standards.
- Frontend Design Workflow.
- Frontend Brief Template.
- Frontend Design Prompt.
- Frontend Review Prompt.
- Frontend UI Review Checklist.
- Responsive Review Checklist.
- Accessibility Review Checklist.
- Visual QA Checklist.
- Impeccable Usage Guide.
- Section Frontend Design trong Project `DESIGN.md`.
- Section Frontend và Impeccable trong Project `AGENTS.md`.

Impeccable được khuyến nghị cho project có frontend nhưng không phải dependency bắt buộc của mọi project.

Impeccable và AI Agent không được thay đổi Product Requirement, business logic, architecture, technology stack hoặc Project Decision. Mọi hoạt động phải tuân theo `PRODUCT.md`, `DESIGN.md`, Coding Standards, Project Decisions và `AGENTS.md`.

Khi Impeccable không được cài đặt hoặc không khả dụng, fallback là sử dụng cùng Frontend Brief, Standards, Workflow, Prompt và Checklists bằng capability sẵn có của AI Agent. Không hạ thấp Acceptance Criteria chỉ vì thiếu Impeccable.

Framework không chọn ASP.NET Core MVC, React, Vue hoặc frontend stack cụ thể làm yêu cầu chung.

**Guides Package**

Guides tối thiểu gồm:

- `how-to-start-a-project.md`
- `how-to-continue-a-project.md`
- `how-to-use-with-chatgpt.md`
- `how-to-use-with-codex.md`
- `how-to-use-with-cline.md`
- `how-to-use-with-claude.md`
- `how-to-use-impeccable.md`
- `how-to-migrate-an-existing-project.md`

Agent-specific Guide mô tả capability, file access, continuation, verification, limitation và fallback của Agent nhưng không sao chép toàn bộ Standards hoặc Workflow.

Existing-project Migration Guide phải dùng quy trình:

1. Inventory memory, tài liệu cũ, chat summary, prompt, source code, issue và evidence.
2. Phân loại thành Product, Design, Decision, Roadmap, Task, Working Context, Changelog, Agent Rule, supporting evidence hoặc discard candidate.
3. Xác định authority và provenance.
4. Ghi nhận conflict hoặc gap; không tự chọn giữa hai nguồn cùng thẩm quyền.
5. Deduplicate và đưa mỗi fact về một Single Source of Truth.
6. Chỉ promote knowledge đã được kiểm chứng.
7. Tạo Working Context từ trạng thái hiện tại thay vì sao chép lịch sử.
8. Cấu hình `AGENTS.md` từ rule đã xác minh.
9. Chạy Documentation Review và thử Open Session.
10. Giữ nguồn cũ làm historical hoặc supporting evidence khi cần, không tiếp tục dùng song song như Single Source of Truth.

Memory của AI chỉ là supporting hoặc historical source cho đến khi được đối chiếu với tài liệu, code hoặc evidence có thẩm quyền.

**Dependency giữa deliverable**

```text
F-024 Accepted
    ↓
Package structure và ownership rules
    ↓
Documentation, Knowledge và AI Working Standards
    ↓
Project Workspace Templates
    ↓
Session và AI Execution Workflows
    ↓
Prompt Templates
    ↓
Checklists và Guides
    ↓
Frontend và Impeccable conditional package
    ↓
Cross-Agent validation
    ↓
Pilot project
    ↓
Framework v1 release review
```

Coding, Testing, Security và Frontend Standards có thể được soạn song song sau khi ownership và Documentation Standards ổn định. Prompt Templates phụ thuộc Project Workspace và Workflow vì phải chỉ rõ file cần đọc và cập nhật.

**Completion Criteria của Framework v1**

Hoàn thành về thiết kế khi:

- F-024 đã Accepted.
- Cấu trúc package, classification, ownership, dependency và applicability đã rõ.
- Có một vị trí chuẩn cho mỗi loại deliverable.
- F-015 đến F-022 đã có mapping sang hiện thực bằng tài liệu.
- Runtime và technology stack không nằm trong critical path.

Hoàn thành về nội dung khi:

- Mọi deliverable `required` có nội dung sử dụng được và không còn placeholder quan trọng.
- Deliverable `conditional` cho frontend đã hoàn thành.
- Chín Project Workspace Template có section, read rule, update rule và Single Source of Truth rõ.
- Standards, Workflows, Templates, Checklists và Guides không trùng trách nhiệm.
- Internal link và document map hợp lệ.
- Impeccable có fallback.

Sẵn sàng pilot khi:

- Có thể khởi tạo, thực hiện, đóng, tiếp tục và bàn giao project bằng package.
- Có thể migrate một project hiện hữu.
- Prompt cốt lõi đã được dry-run cho analyze, design, implement hoặc fix, review, document và frontend.
- Vấn đề phát hiện được ghi làm pilot feedback và không thay đổi Accepted semantics một cách ngầm định.

Sẵn sàng phát hành Framework v1 khi:

- Đã pilot trên ít nhất một dự án cá nhân.
- Prompt Templates đã được kiểm thử với ChatGPT, Codex, Cline và Claude hoặc limitation và fallback đã được ghi rõ.
- Documentation Review và Release hoặc Handover Checklist đạt.
- Không còn broken link, conflicting ownership hoặc template bắt buộc rỗng.
- Quick Start có thể được người không phải Dev chuyên nghiệp thực hiện.
- Package version và release note đã được xác định.
- Không yêu cầu Executable Runtime, Builder repository hoặc Reference Implementation để tuyên bố hoàn thành.

**Governance**

Decision mới được dùng khi bổ sung deliverable hoặc quy tắc package không thay đổi Accepted semantics.

ACR được yêu cầu khi:

- Thay đổi chín file Project Workspace đã Accepted tại F-003.
- Đưa Runtime hoặc Reference Implementation trở lại điều kiện hoàn thành.
- Làm suy yếu hoặc thay đổi nghĩa F-015 đến F-022.
- Cho Prompt Template thay thế upstream contract hoặc trở thành nguồn business logic.
- Biến Impeccable thành dependency bắt buộc của mọi project.

Thứ tự soạn package, người thực hiện, project được chọn để pilot và lịch phát hành thuộc implementation plan hoặc Roadmap.

**Lý do**

Phương án này:

- Xác định chính xác Framework v1 phải cung cấp gì.
- Giữ cấu trúc nhẹ và dễ tìm đối với người không phải Dev chuyên nghiệp.
- Cho AI Agent biết nguồn nào phải đọc và cập nhật.
- Giữ Framework độc lập AI Agent và technology stack.
- Hiện thực các Accepted Contract bằng tài liệu mà không bắt buộc Runtime.
- Giữ Frontend Design và Impeccable có giá trị nhưng không áp dụng sai cho mọi project.
- Tạo điều kiện pilot và release có thể kiểm chứng.

**Hệ quả**

- Framework Deliverable Profile và Template Package Specification được coi là hoàn thành về thiết kế.
- Bước tiếp theo của Roadmap sản phẩm chính là Global Workspace Structure và nội dung baseline.
- Project Workspace Template Package được thực hiện sau khi Documentation, Knowledge và AI Working Standards ổn định.
- Prompt Templates được tạo sau Project Workspace và AI Workflow để tránh read hoặc update mapping không nhất quán.
- F-023 tiếp tục được giữ nguyên để truy vết lịch sử.
- Builder Specification và Executable Reference Implementation tiếp tục là hướng mở rộng tùy chọn, không thuộc critical path của Framework v1.
- F-001 đến F-023 và các Accepted Contract không bị thay đổi nghĩa bởi Decision này.

---

## Ghi chú triển khai — Global Workspace Structure

**Trạng thái:** Completed trong Roadmap

Global Workspace Structure được làm rõ trong `FRAMEWORK_SPEC.md` như một cập nhật Living Document triển khai F-024.

Ghi chú này không phải Architecture Decision mới và không thay đổi F-024, ACR-003, F-023 hoặc các Accepted Contract.

Các nội dung được làm rõ gồm:

- Vai trò, authority và ranh giới Global Workspace.
- Trách nhiệm, dependency, applicability và Completion Criteria của Standards, Workflows, Templates và Checklists.
- No-silent-override và cách áp dụng precedence theo F-017 và F-021.
- Intent-based reading và update map.
- Versioning và migration guidance tối giản ở mức package tài liệu.
- Điều kiện để tạo `skills/` khi có skill thực tế.
- Completion Criteria của Global Workspace.

Không tạo F-025 vì các nội dung trên cụ thể hóa các semantics đã Accepted và không cần thiết lập một governance system, registry, package manager hoặc lifecycle engine mới.

Thứ tự triển khai được ghi nhận là hoàn thiện baseline của Documentation Standards, Knowledge Management Standards và AI Working Standards trước khi điền chín Project Workspace Template. Đây là implementation plan, không phải Architecture Decision.

---

## Ghi chú triển khai — Baseline Content Specification của ba Standards nền tảng

**Trạng thái:** Completed về đặc tả nội dung

Baseline content specification cho `documentation.md`, `knowledge-management.md` và `ai-working.md` đã được xác nhận và phản ánh trong `FRAMEWORK_SPEC.md`.

Ghi chú này không phải Architecture Decision mới. Nội dung chỉ cụ thể hóa F-004 đến F-008, F-012 đến F-019 và F-024, không thay đổi ACR-003, F-023, F-024 hoặc Accepted Contract.

Ba baseline xác định:

- Documentation ownership, Living và Historical boundary, update gate, conflict, divergence, deduplication và review.
- Memory layers, Knowledge Source authority, Context Selection, promotion lifecycle, provenance, staleness và knowledge review.
- Session Contract, Intent, Context, Constraint, Output, execution boundary, verification, document update, completion reporting và failure handling cho AI Agent.

Không tạo thêm Project Workspace file, không chọn technology stack hoặc AI Agent, không yêu cầu Runtime, Registry, database, schema hoặc persistent memory.

Dependency tiếp theo là Project Workspace Template Package gồm chín file đã Accepted tại F-003 và F-024. Chín file package thực tế sau đó đã được tạo tại `/project-template/` theo phạm vi đã xác nhận; validation và dry-run vẫn phải tuân theo các checkpoint triển khai tương ứng.

---

## Ghi chú triển khai — Project Workspace Template Package Specification

**Trạng thái:** Completed trong Roadmap

Project Workspace Template Package đã được làm rõ trong `FRAMEWORK_SPEC.md` như một cập nhật Living Document triển khai F-003 và F-024.

Ghi chú này không phải Architecture Decision mới, không tạo F-025 và không thay đổi F-003, F-004, F-013, ACR-003, F-023, F-024 hoặc Accepted Contract.

Nội dung được làm rõ gồm:

- Purpose, authority, audience, ownership và boundary của đúng chín file đã Accepted.
- Required và conditional sections.
- Intent-based read rule và responsibility-based update rule.
- Inputs, dependency, cross-file relationship, conflict, gap và divergence handling.
- Template guidance và Completion Criteria của từng file và toàn package.
- Initialization flow và migration flow cho project hiện hữu.
- Cross-file ownership, consistency model và update matrix.
- Quy tắc giữ `WORKING_CONTEXT.md` nhẹ và bảo toàn `DECISIONS.md` như Historical Record.
- Frontend sections conditional trong `DESIGN.md` và `AGENTS.md`.
- Impeccable usage profile và fallback không hạ Acceptance Criteria.

Không bổ sung file Project Workspace bắt buộc, không dùng Roadmap để xác lập Decision, không cho `AGENTS.md` thay Product, Design hoặc Decisions, không chọn technology stack và không yêu cầu Runtime, schema, CLI, Web API, database, Registry hoặc Reference Implementation.

Roadmap trước tiên chuyển `Project Workspace Template Package` từ `Proposed` sang `In Progress` khi đặc tả thiết kế hoàn thành. Sau khi đúng chín template được tạo, structural validation, cross-file semantic validation và documentation dry-run cho Initialize, Migration, Open, Close, Continue và Handover đều đạt, hạng mục được chuyển sang `Completed`.

Completion của Project Workspace Template Package không tự tuyên bố toàn Framework sẵn sàng pilot hoặc phát hành. Các Standards, Workflows, Prompt Templates, Checklists, Guides, cross-Agent validation và pilot tiếp tục theo Roadmap. Nếu thay đổi danh sách chín file, Accepted ownership, historical boundary, Impeccable applicability hoặc critical path của Framework v1 thì phải dừng và dùng ACR phù hợp.

## Ghi chú triển khai — Standards và Checklists Package

Standards và Checklists Package đã được tạo tại `/global-workspace/standards/` và `/global-workspace/checklists/` theo danh sách F-024. Structural validation, cross-file semantic validation và documentation dry-run cho các scenario initialize, session, implementation/review, frontend, release, missing capability, authority conflict, permission/approval, untrusted input và Impeccable fallback đã đạt.

Ghi chú này không phải Architecture Decision mới, không tạo F-025 và không thay đổi F-003, F-004, F-013, F-021, ACR-003, F-023, F-024 hoặc Accepted Contract. Coding Standards được hiện thực ở mức Documentation & Template Framework; Frontend Design tiếp tục conditional; Workflows, Prompt Templates, Guides, cross-Agent validation và pilot project vẫn là dependency của các Roadmap item sau. Completion ở phạm vi package này không tuyên bố toàn Framework sẵn sàng pilot hoặc phát hành.
