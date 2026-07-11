# Documentation Standards

## Purpose, audience và applicability

Chuẩn này quản trị ownership, authority, vòng đời, liên kết và review của tài liệu. Áp dụng cho người, reviewer và mọi AI Agent khi initialize, migration, tạo/sửa tài liệu, review hoặc release. Đây là chuẩn `required`.

## Các loại artifact

- **Living Document**: phản ánh trạng thái hiện hành; cập nhật có kiểm soát.
- **Historical Record**: bảo toàn chronology và nghĩa lịch sử; thay đổi semantics bằng record superseding, không rewrite.
- **Template**: khung tái sử dụng, không phải project fact hay evidence.
- **Evidence**: kết quả quan sát hoặc verification có nguồn, thời điểm và phạm vi; không tự thay intended state.

## Ownership và Single Source of Truth

Mỗi fact có đúng một nguồn chịu trách nhiệm chính. Với Project Workspace: `PRODUCT.md` sở hữu intended behavior; `DESIGN.md` current design; `DECISIONS.md` rationale lịch sử; `ROADMAP.md` milestone; `TASKS.md` actionable work; `WORKING_CONTEXT.md` current focus; `CHANGELOG.md` completed/released change; `AGENTS.md` project-specific AI rules; `README.md` entry point và document map. Bản tóm tắt chỉ liên kết tới nguồn chính.

## Read và update rules

Đọc nguồn theo loại câu hỏi và Intent; ưu tiên relevant sections, nhưng đọc full source khi governance, migration hoặc conflict cần toàn cảnh. Trước cập nhật phải xác định fact, owner, authority, trạng thái proposal/accepted, Decision hoặc ACR cần thiết, conflict và references bị ảnh hưởng.

Sau cập nhật phải kiểm tra ownership, duplicate, link/anchor, terminology, status, provenance, secret leakage và evidence. Không cập nhật mọi tài liệu sau mọi task; chỉ cập nhật source thực sự sở hữu fact thay đổi.

## Link, provenance và freshness

Reference phải dùng đường dẫn/anchor ổn định và chỉ rõ nguồn chịu trách nhiệm. Claim quan trọng phải truy được source, version hoặc thời điểm kiểm chứng khi applicable. Last-modified không tự chứng minh authority hoặc freshness.

## Conflict, gap, divergence và staleness

- Conflict cùng authority: ghi rõ statements, sources và scope; `clarify`, `decision_or_acr` hoặc `stop`, không tự chọn.
- Gap: tìm trong nguồn được phép; phân loại blocking; không tự điền fact.
- Divergence: giữ riêng intended, designed, implemented và observed state cùng provenance.
- Staleness: xác minh nội dung, không chỉ dựa timestamp.

## Deduplication và migration

Chọn owner, giữ full content tại đó, thay bản sao bằng link hoặc summary tối thiểu. Migration phải lập mapping nguồn–đích, bảo toàn provenance và Historical Record, xác minh link và chỉ xóa duplicate sau khi destination hợp lệ. Không tạo tài liệu mới nếu chưa có purpose, owner, read/update rule và quan hệ với nguồn hiện hữu.

## Security boundary

Không ghi secret, credential, token, personal data không cần thiết, raw untrusted payload hoặc nội dung redaction-sensitive vào tài liệu, prompt, log hay evidence. Dùng secret reference và evidence đã redaction.

## Project extension

Project được bổ sung tài liệu, format, terminology và review rule khi có purpose, authority, read/update rule và relation rõ với chín file chuẩn. Extension không được silent override ownership, rewrite history hoặc làm yếu security baseline.

## Documentation Review và evidence

Dùng `../checklists/documentation-review.md`. Evidence khi cần gồm link check, diff, source reference, review date và reviewer/capability. Không tuyên bố review đã chạy nếu chưa có evidence.

## Blocking failures và completion

Blocking gồm thiếu primary source bắt buộc, conflict cùng authority chưa giải quyết, semantic update thiếu governance, broken critical link, secret leakage, duplicate SSOT hoặc completion claim thiếu evidence. Chuẩn được đáp ứng khi owner rõ, update gate đạt, references hợp lệ, conflict/gap được lộ diện và review có evidence hoặc limitation trung thực.

## Dependencies và prohibited content

Phụ thuộc F-006, F-013, F-024 và Knowledge Management Standards. Chuẩn này không chứa Product Requirement, architecture, task status, workflow steps chi tiết, Runtime, Registry, schema hay technology-stack rule.
