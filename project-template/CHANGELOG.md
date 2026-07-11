# CHANGELOG.md

> Single Source of Truth cho thay đổi đã hoàn thành hoặc phát hành đáng chú ý. Không ghi work in progress.

## Convention

- Chỉ thêm entry khi change đã đạt Completion Criteria và có evidence.
- Nhóm theo version và date; project không version release có thể nhóm theo milestone completion.
- Taxonomy đề xuất: `Added`, `Changed`, `Fixed`, `Removed`, `Security`.
- Decision rationale thuộc `DECISIONS.md`; actionable work thuộc `TASKS.md`.

## Unreleased `[Conditional]`

> Chỉ chứa change đã hoàn thành nhưng chưa được gắn vào release. Không chứa work đang làm.

### Added

- `[Thay đổi đã hoàn thành]` — `[T-ID hoặc evidence ref]`

### Changed

- `[Thay đổi đã hoàn thành]` — `[T-ID hoặc evidence ref]`

### Fixed

- `[Lỗi đã sửa và verified]` — `[T-ID hoặc evidence ref]`

### Removed

- `[Nội dung đã bỏ]` — `[T-ID hoặc Decision ref]`

### Security

- `[Tóm tắt an toàn, không lộ sensitive detail]` — `[Advisory hoặc evidence ref]`

## [Version hoặc milestone] — [YYYY-MM-DD]

### Added

- `[User-impact hoặc project-impact outcome]` — `[T-ID]`

### Changed

- `[Outcome]` — `[T-ID hoặc D-ID]`

### Fixed

- `[Outcome]` — `[T-ID]`

### Removed

- `[Outcome]` — `[T-ID hoặc D-ID]`

### Security

- `[Outcome]` — `[Safe reference]`

### Breaking changes and migration `[Conditional]`

- Breaking impact: `[Mô tả]`
- Required migration: `[Bước hoặc link]`
- Compatibility limitation: `[Mô tả]`

### Known limitations `[Conditional]`

- `[Limitation đã xác nhận]`

## Quy tắc bảo trì template

- AI đọc khi release, migration, impact analysis hoặc historical change review.
- Release owner hoặc maintainer chịu trách nhiệm; AI chỉ draft từ completed task có evidence.
- Code tồn tại không tự chứng minh đã release.
- Nếu completion claim không được evidence hỗ trợ, ghi divergence và sửa sau review.
- Không chứa backlog, WIP, raw commit log, session notes hoặc Decision rationale đầy đủ.
- Xóa heading taxonomy không có entry trong release cụ thể.

## Completion Checklist cho release hoặc grouping

- [ ] Version hoặc milestone và date rõ.
- [ ] Mỗi entry đã completed và có reference.
- [ ] Breaking, migration, security và limitation được nêu khi applicable.
- [ ] Không có WIP hoặc claim chưa verification.
- [ ] Nội dung tập trung vào outcome, không sao chép commit log.

