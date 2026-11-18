# Ảnh tham chiếu — thư mục refs/

Ảnh khóa của diễn viên v19 + ảnh thật sản phẩm nằm ở đây, dạng `.b64` (base64 của file
ảnh gốc). Ảnh nhị phân không đẩy trực tiếp lên GitHub qua connector được, nên repo lưu
bản base64; Muse US tự tải về và giải mã thành file ảnh bằng lệnh `base64 -d <file>.b64 > <file>.jpg`.

| File | Ảnh gì |
|---|---|
| `v19-vay-trang.jpg.b64` | Ảnh chính: váy trắng hai dây ngắn, vòng 1 đúng 106cm (ảnh mặc định) |
| `v19-chan-122cm.jpg.b64` | Ảnh chân 122cm |
| `v13-vong1.jpg.b64` | Ảnh vòng 1 chuẩn (v13) |
| `v19-vay-body-den.jpg.b64` | Ảnh váy body đen tự thiết kế |
| `v19-ho-eo.jpg.b64` | Ảnh eo/cơ bụng tốt nhất (crop top trắng hở eo) |
| `v19-nha-tam.jpg.b64` | Ảnh v19 trong nhà tắm, áo thun xám, cầm miếng YUJIAO (ảnh tham chiếu cảnh nhà tắm) |
| `yujiao-logo.jpg.b64` | Ảnh thật miếng YUJIAO: logo YUJIAO chữ xám đậm in chéo + ký hiệu YJ (ảnh tham chiếu LOGO) |
| `yujiao-hinh-dang.jpg.b64` | Ảnh thật miếng YUJIAO: lớp mài xanh ngọc + đế xanh lá nhạt (ảnh tham chiếu HÌNH DÁNG/MÀU) |
| `v19-neo-mat-chinh-dien.jpg.b64` | Bộ neo trung tính: mặt chính diện, biểu cảm trung tính, áo thun xám, ánh sáng nhà tắm (neo mặt chính cho video) |
| `v19-neo-can-mat.jpg.b64` | Bộ neo trung tính: cận mặt (đầu + vai), biểu cảm trung tính, áo thun xám (neo mặt chính cho video) |

Muse US đọc queue.json sẽ tự lấy ảnh trong thư mục này — không cần ai đính kèm ảnh trong
chat. Ảnh sản phẩm mới (.b64) cũng đẩy lên đây theo hướng dẫn trong `lenh-runbook.md` mục 4.
