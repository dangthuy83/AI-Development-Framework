# Handover Session Prompt Template

## Use

**Purpose/applicability:** Pause, close or transfer a session. **User/capability:** Current executor and next owner/Agent.

## Compose

- Project, recipient and handover authority: `[input]`
- Session Contract and Intent dependency state: `[objective/scope/constraints/deliverables; completed/remaining nodes]`
- Required reads: AI Working, Documentation, Knowledge, Security; Session and Documentation Update Workflows; Working Context, Tasks and relevant owner sources.
- Context behavior: reconcile actual artifacts/evidence, flag stale/conflicting claims; never use memory as SSOT.
- Deliverables: concise current state, valid outputs, blockers, decisions needed, next actions, verification refs and owner updates.
- Acceptance/verification: Close Session Checklist; Release/Handover Checklist when ownership/release transfer applies.
- Dependencies: `[remaining Intent, artifact, approval and next-owner dependencies]`.
- Permissions/updates: `[Working Context/Tasks/Changelog owners]`; no external transfer/publish without explicit approval; no secret or raw sensitive evidence.

## Report and fallback

Do not replace upstream contracts or create Prompt Assets. Report `completed|partial|blocked|failed|skipped`; never hide failed/skipped verification. If next Agent/tool unavailable, produce a technology-neutral manual handover with criteria unchanged. Project extension comes from sourced Project Rules.
