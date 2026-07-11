# [Tên project]

> [Mô tả project trong một câu. Không chép toàn bộ Product Requirement.]

## Trạng thái

- Lifecycle: `[Khởi tạo | Đang phát triển | Bảo trì | Tạm dừng | Đã đóng]`
- Phiên bản hoặc release hiện hành: `[Nếu có]`
- Cập nhật gần nhất: `[YYYY-MM-DD]`
- Review gần nhất: `[YYYY-MM-DD hoặc Chưa review]`
- Người chịu trách nhiệm: `[Tên hoặc vai trò]`

## Quick Start

> Chỉ ghi command hoặc bước đã được kiểm chứng. Nếu chưa có executable artifact, ghi rõ `Chưa áp dụng`.

1. `[Điều kiện tiên quyết]`
2. `[Lệnh hoặc bước khởi động]`
3. `[Cách xác nhận project hoạt động]`

## Project entry points

- Workspace hoặc source chính: `[Đường dẫn hoặc mô tả]`
- Cách nhận hỗ trợ: `[Người, kênh hoặc quy trình]`
- Entry constraint đã biết: `[Không có | Mô tả ngắn và link nguồn]`

## Document Map

| Câu hỏi | Nguồn chuẩn |
|---|---|
| Phải xây gì và hành vi mong muốn là gì? | [PRODUCT.md](PRODUCT.md) |
| Hệ thống hiện hành được thiết kế thế nào? | [DESIGN.md](DESIGN.md) |
| Milestone đi theo thứ tự nào? | [ROADMAP.md](ROADMAP.md) |
| Vì sao lựa chọn được chấp thuận? | [DECISIONS.md](DECISIONS.md) |
| Hiện đang ở đâu và bước tiếp theo là gì? | [WORKING_CONTEXT.md](WORKING_CONTEXT.md) |
| Việc cụ thể nào còn phải làm? | [TASKS.md](TASKS.md) |
| Đã hoàn thành hoặc phát hành gì? | [CHANGELOG.md](CHANGELOG.md) |
| AI Agent phải làm việc theo quy tắc nào? | [AGENTS.md](AGENTS.md) |

## Usage entry `[Conditional]`

> Giữ section này khi project có demo, package, service hoặc artifact cho người dùng.

- Cách sử dụng: `[Tóm tắt và link đến nguồn chuyên trách]`
- Demo hoặc artifact: `[Link]`

## Frontend entry `[Conditional]`

> Giữ section này khi project có frontend.

- Frontend scope: [DESIGN.md#frontend-design](DESIGN.md#frontend-design)
- Frontend working rules: [AGENTS.md#frontend-and-impeccable](AGENTS.md#frontend-and-impeccable)

## Quy tắc bảo trì template

- Đây là nguồn chuẩn cho entry point, onboarding, Quick Start và Document Map.
- AI đọc file này khi initialize, onboarding hoặc chưa biết source map.
- Chỉ cập nhật khi entry point, Quick Start, Document Map hoặc status khái quát đã kiểm chứng thay đổi.
- File chuyên trách có authority trong domain tương ứng; README chỉ tóm tắt và liên kết.
- Nếu summary khác source chuyên trách, ghi nhận divergence và sửa summary sau verification.
- Không chứa Product Requirement chi tiết, kiến trúc chi tiết, backlog, Decision rationale, session history hoặc secret.

## Completion Checklist

- [ ] Project name và one-line summary rõ.
- [ ] Lifecycle status là hiện hành.
- [ ] Quick Start khả dụng hoặc ghi rõ chưa áp dụng.
- [ ] Link đến đủ tám file còn lại hợp lệ.
- [ ] Không duplicate knowledge thuộc source chuyên trách.
