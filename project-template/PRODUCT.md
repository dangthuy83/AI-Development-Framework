# PRODUCT.md

> Single Source of Truth cho Product Requirement, product scope và intended behavior.

## Metadata

- Trạng thái tài liệu: `[Draft | Active | Under Review]`
- Product authority: `[Tên hoặc vai trò]`
- Cập nhật gần nhất: `[YYYY-MM-DD]`
- Review gần nhất: `[YYYY-MM-DD hoặc Chưa review]`

## Product vision

[Project tạo giá trị gì và trạng thái tương lai mong muốn là gì?]

## Problem statement

[Vấn đề cần giải quyết, đối tượng bị ảnh hưởng và bằng chứng hoặc provenance nếu có.]

## Target users and stakeholders

| Nhóm | Nhu cầu hoặc trách nhiệm | Authority liên quan |
|---|---|---|
| `[Nhóm]` | `[Nhu cầu]` | `[Quyền xác nhận nếu có]` |

## Goals

- `[G-001] [Kết quả mong muốn có thể kiểm chứng]`

## Non-goals

- `[NG-001] [Nội dung chủ động nằm ngoài scope]`

## Product scope

### In scope

- `[Phạm vi đã được xác nhận]`

### Out of scope

- `[Phạm vi không thuộc product hiện hành]`

## Functional requirements and capabilities

| ID | Requirement hoặc capability | Status | Provenance | Acceptance reference |
|---|---|---|---|---|
| `PR-001` | `[Hành vi mong muốn, không mô tả cách triển khai]` | `[Proposed \| Accepted \| Deferred]` | `[Nguồn hoặc authority]` | `[AC hoặc link]` |

## Behavioral rules

| ID | Tình huống | Intended behavior | Provenance |
|---|---|---|---|
| `BR-001` | `[Điều kiện]` | `[Hành vi quan sát được]` | `[Nguồn]` |

## Product-level acceptance expectations

- `[PA-001] [Điều kiện đạt ở mức sản phẩm]`

## Assumptions and product constraints

| ID | Loại | Nội dung | Trạng thái | Nguồn |
|---|---|---|---|---|
| `PC-001` | `[Assumption \| Product constraint]` | `[Nội dung]` | `[Confirmed \| Unconfirmed]` | `[Nguồn]` |

## User journeys or use cases `[Conditional]`

> Giữ khi user journey giúp làm rõ intended behavior.

### `[UJ-001] [Tên journey]`

1. `[Bước hoặc user intent]`
2. `[Kết quả mong đợi]`

## Domain terminology `[Conditional]`

| Thuật ngữ | Nghĩa đã xác nhận | Không được hiểu là |
|---|---|---|
| `[Thuật ngữ]` | `[Định nghĩa]` | `[Phân biệt nếu cần]` |

## Quality and policy expectations `[Conditional]`

- Data hoặc privacy: `[Requirement hoặc link]`
- Accessibility: `[Requirement hoặc link]`
- Localization: `[Requirement hoặc link]`
- External product dependency: `[Requirement hoặc link]`

## Open product gaps

| ID | Gap hoặc ambiguity | Criticality | Resolution owner | Next action |
|---|---|---|---|---|
| `PG-001` | `[Nội dung chưa đủ]` | `[Required \| Supporting]` | `[Tên hoặc vai trò]` | `[Clarify \| Stop \| Resolve source]` |

## Traceability

- Current Design: [DESIGN.md](DESIGN.md)
- Product Decisions: [DECISIONS.md](DECISIONS.md)
- Delivery Roadmap: [ROADMAP.md](ROADMAP.md)
- Actionable Tasks: [TASKS.md](TASKS.md)

## Quy tắc bảo trì template

- AI phải đọc relevant sections khi analyze, design, implement hoặc fix behavior, test acceptance và functional review.
- Chỉ Product authority được xác nhận intended behavior mới hoặc thay đổi requirement.
- Không suy requirement từ code, chat summary hoặc AI memory chưa kiểm chứng.
- Nếu Product khác code, test hoặc runtime evidence, ghi divergence; không silent override.
- Same-authority conflict phải clarify hoặc block.
- Không chứa technology stack, module hoặc schema design, task tạm thời, session state hay Decision rationale đầy đủ.

## Completion Checklist

- [ ] Vision, problem, target users, goals và non-goals rõ.
- [ ] Scope và intended behavior đủ để design.
- [ ] Requirement quan trọng có status và provenance.
- [ ] Product gap và ambiguity được ghi nhận.
- [ ] Không chứa implementation detail hoặc backlog.
