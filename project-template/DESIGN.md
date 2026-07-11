# DESIGN.md

> Single Source of Truth cho current architecture và current design. Rationale lịch sử thuộc `DECISIONS.md`.

## Metadata

- Trạng thái tài liệu: `[Draft | Active | Under Review]`
- Design authority: `[Tên hoặc vai trò]`
- Cập nhật gần nhất: `[YYYY-MM-DD]`
- Phạm vi design: `[Toàn project hoặc phạm vi con]`

## Design overview

[Tóm tắt current design, boundary chính và cách design đáp ứng Product.]

## Architecture boundaries and components

| Component hoặc boundary | Responsibility | Không chịu trách nhiệm | Product refs |
|---|---|---|---|
| `[Tên]` | `[Trách nhiệm]` | `[Boundary]` | `[PR/BR ID]` |

## Interactions and information flow

[Mô tả flow cần thiết. Chỉ thêm diagram khi giúp làm rõ boundary hoặc sequence.]

## External dependencies and integrations

| Dependency | Purpose | Boundary hoặc contract | Failure consideration |
|---|---|---|---|
| `[Tên]` | `[Mục đích]` | `[Interface hoặc link]` | `[Behavior khi lỗi]` |

## Project technology profile

> Ghi lựa chọn của project, không coi đây là stack mặc định của Framework.

| Area | Current choice | Version hoặc constraint | Provenance |
|---|---|---|---|
| `[Area]` | `[Technology hoặc Not applicable]` | `[Version]` | `[Decision hoặc evidence]` |

## Data model `[Conditional]`

[Entity, ownership, lifecycle và invariant cần cho current design. Không đưa schema chi tiết nếu không cần.]

## APIs and interfaces `[Conditional]`

| Interface | Consumer | Contract hoặc behavior | Compatibility rule |
|---|---|---|---|
| `[Tên]` | `[Consumer]` | `[Mô tả hoặc link]` | `[Rule]` |

## Security and trust boundaries

- Trust boundaries: `[Mô tả]`
- Sensitive data: `[Loại dữ liệu hoặc Không có]`
- Permission hoặc approval boundaries: `[Mô tả]`
- Untrusted inputs: `[Nguồn và cách xử lý ở mức design]`

## Operational and deployment model `[Conditional]`

[Current environment, topology, deployment hoặc operational boundary đã được xác nhận.]

## Performance, concurrency and resilience `[Conditional]`

[Chỉ giữ khi Product hoặc current design có requirement tương ứng.]

## Migration and compatibility `[Conditional]`

[Current migration boundary, backward compatibility hoặc data transition requirement.]

## Frontend Design

> Giữ section này khi project có user-facing UI, design system, component library hoặc task thay đổi presentation hay interaction.

### Impeccable usage policy

- Usage policy: `[disabled | optional | preferred | required-if-available]`
- Authority hoặc provenance: `[Project Decision, owner confirmation hoặc source ref]`
- Tool-required override: `[None | User instruction hoặc Project Decision yêu cầu bắt buộc]`

Usage policy mô tả lựa chọn ổn định của project. Trạng thái công cụ thực tế và fallback của phiên làm việc được khai báo trong `AGENTS.md`; Impeccable không phải technology stack và không được thay Product, Design hoặc Decision.

### Scope and surfaces

- `[UI surface và phạm vi]`

### User flows and information architecture

- `[Flow hoặc link Product journey]`

### Layout and component boundaries

| Surface hoặc component | Responsibility | States | Product refs |
|---|---|---|---|
| `[Tên]` | `[Trách nhiệm]` | `[Default, loading, empty, error, success...]` | `[PR/BR ID]` |

### Visual direction and design tokens

[Visual direction hoặc token đã được project xác nhận; không để tool tự chọn lại Product hoặc architecture.]

### Responsive behavior

[Breakpoints hoặc behavior theo available space; không mặc định stack.]

### Accessibility requirements

[Keyboard, focus, semantics, contrast, motion hoặc project requirement tương ứng.]

### Visual QA expectations

- `[Evidence hoặc review cần có]`

## Observability `[Conditional]`

[Signals cần thiết để hiểu actual system behavior.]

## Design constraints

| ID | Constraint | Source | Enforcement |
|---|---|---|---|
| `DC-001` | `[Nội dung]` | `[PRODUCT, DECISION hoặc policy]` | `[Mandatory \| Approval required \| Advisory]` |

## Traceability to Product and Decisions

| Design area | Product refs | Decision refs | Evidence refs |
|---|---|---|---|
| `[Area]` | `[PR/BR]` | `[D-xxx hoặc None]` | `[Code, config, test hoặc evidence]` |

## Known design gaps and divergences

| ID | Type | Description | Sources in tension | Impact | Next action |
|---|---|---|---|---|---|
| `DG-001` | `[Gap \| Conflict \| Divergence \| Staleness]` | `[Nội dung]` | `[Source refs]` | `[Impact]` | `[Clarify \| Decision \| Task \| Stop]` |

## Quy tắc bảo trì template

- AI đọc relevant sections khi design, implement, architecture-sensitive fix hoặc refactor, database, integration, security, frontend và design review.
- Cập nhật khi current design đã được chấp thuận và verification phù hợp đã có.
- Design khác Product là conflict cần xử lý theo authority; Design khác code hoặc runtime là divergence.
- Link Decision thay vì chép rationale; mô tả current state thay vì chronology.
- Không chứa backlog, task status, session log hoặc requirement chưa Accepted.

## Completion Checklist

- [ ] Boundary, component, responsibility và interaction đủ rõ.
- [ ] Traceability đến Product và Decisions hợp lệ.
- [ ] Current state phân biệt planned hoặc actual divergent state.
- [ ] Security/trust boundary đã được xem xét.
- [ ] Conditional sections được giữ hoặc bỏ theo applicability.
