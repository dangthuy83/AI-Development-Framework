# Frontend Brief

> Conditional Document Template. Tổng hợp context có provenance; không phải Product, Design hoặc Decision SSOT.

**Purpose:** cung cấp task context có nguồn cho Frontend Workflow. **Dependencies:** Product, Project Design, Tasks, Frontend Standards/Workflow/Checklists. **Permission boundary:** template không tự cấp approval hay quyền sửa owner source.

## Control

- Project/task: `[ref]`
- Owner / status / updated: `[owner]` / `[draft|approved-for-task]` / `[date]`
- Applicability: `[user-facing UI reason]`

## Authorized context

- Product context: `[PRODUCT.md refs; không chép requirement mới]`
- Users and goals: `[refs]`
- Authorized scope: `[task/user instruction refs]`
- Out of scope: `[explicit boundaries]`
- Product / Design / Decision references: `[links/anchors + authority/freshness]`
- Open gaps, assumptions and approvals: `[gap; source checked; blocking?; approver]`

## Experience

- Frontend surfaces and user flows: `[entry → states → outcome]`
- Visual direction and references: `[authoritative vs inspiration; provenance/licence]`
- Interaction states: `[default/loading/empty/error/success/disabled/validation]`
- Responsive requirements: `[target viewports/containers/content priority]`
- Accessibility requirements: `[semantic, keyboard/focus, contrast, alternatives, announcements, motion]`
- Constraints: `[architecture, current stack, component system, security/privacy, compatibility]`

## Impeccable

- Usage policy: `[disabled|optional|preferred|required-if-available + DESIGN/AGENTS ref]`
- Availability: `[available|unavailable|not_applicable + evidence]`
- Fallback: `[native/manual capability; criteria unchanged]`

## Output contract

- Deliverables: `[artifact IDs and descriptions]`
- Acceptance Criteria: `[observable criterion → deliverable → upstream ref]`
- Verification Requirements: `[criterion → method → evidence; include responsive/accessibility/visual QA]`
- Allowed updates: `[owner files only]`
- Approval gates: `[material direction, asset/dependency, side effect]`

## Completion rule

Complete only when required context has sources, gaps are resolved or explicitly blocking, deliverables/criteria/verification are traceable, and applicable frontend checklists pass. Report `completed|partial|blocked|failed|skipped`; do not lower criteria when Impeccable or visual capability is unavailable.
