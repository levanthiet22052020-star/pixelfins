# PixelFins — Rules dự án

Bộ rules tối thiểu mà AI (và người) làm dự án này phải theo. Kịch bản chi tiết: `docs/scenario.md`.

## 1. Nguồn sự thật & quyền quyết định

- `../docs/scenario.md` = GDD chuẩn. Code phải khớp nó. Thấy mâu thuẫn → báo user, không tự đổi thiết kế.
- Giá cá tham chiếu thật ở `../docs/gia-ca-canh-trung-tin.md` — không bịa giá, không đổi số liệu kinh tế khi code.
- Sửa GDD, số liệu, tên NPC/loài → user quyết. AI chỉ đề xuất.

## 2. Phạm vi theo giai đoạn

- Đang làm GĐ1: chỉ GĐ1. Cấm làm trước GĐ2/GĐ3 (lai tạo, bệnh, hệ số mùa, quest, mảnh ký ức).
- Danh mục GĐ1 cố định: 4 loài (bảy màu, betta, cá vàng, mún); thức ăn cám viên/trùn chỉ/bo bo; lò sưởi; 2 NPC giản lược (Cô Hai Tiên, Bác Tám). Không thêm.

## 3. Stack & kỹ thuật

- PixiJS + TypeScript strict. Không thêm engine/framework/library lớn khi không hỏi.
- Web, chuột = input duy nhất. Mọi UI phải thao tác bằng chuột được.
- Data-driven: loài, thức ăn, giá, gene, nhiệt độ → data file riêng (TS/JSON), không hardcode rải trong logic.
- Save GĐ1 = localStorage; thiết kế schema sẵn để migrate IndexedDB ở GĐ2. Đổi schema → bắt buộc kèm migration.

## 4. Ngôn ngữ & asset

- UI + hội thoại game: tiếng Việt. Tên biến/hàm/comment: tiếng Anh.
- Pixel art AI vào `public/assets/`, snake_case (vd `guppy_adult.png`); không sửa art tay.

## 5. Quy trình

- Git đã có ở root repo này. Commit nhỏ, mỗi commit chạy được.
- Cấu trúc thư mục chốt trước để AI không tự chế: `src/core` (vòng ngày/đêm), `src/fish`, `src/tank`, `src/economy`, `src/npc`, `src/ui`, `src/save`.
- Trước khi báo "xong": chạy được, save/load không mất tiến độ (đúng mục 8 GDD).

## 6. Giao tiếp (mặc định — user có thể xóa)

- AI trả lời tiếng Việt, ngắn.
- User báo lỗi theo số dòng (`:n`) → luôn đọc đĩa để verify trước khi sửa lại.
- Sửa file text đang mở trong editor → nhắc user reload (VS Code: File → Revert File).
