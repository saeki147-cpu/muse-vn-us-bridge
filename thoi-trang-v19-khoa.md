# Thời trang v19 — KHÓA 1 KIỂU DUY NHẤT (18/11/2026)

Quy tắc: quần áo + đầu tóc của v19 LUÔN GIỮ 1 KIỂU trong mọi clip, mọi video.
Đổi kiểu chỉ khi Saek duyệt. Không tự đổi.

## 1. Kiểu đã khóa cho mọi cảnh Ở NHÀ (nhà tắm, dọn nhà, bếp...)

Lấy đúng từ ảnh tham chiếu v19-nha-tam (ảnh v19 trong nhà tắm cầm miếng YUJIAO,
đã nằm trong repo refs/v19-nha-tam.jpg.b64):

- **Áo:** áo hai dây trắng, vải mỏng nhẹ, ôm sát người (fitted, không rộng), cổ chữ V nhẹ,
  thấy rõ vòng 1 106cm và eo 58cm qua vải. Không hở da dưới xương quai xanh quá mức,
  không xuyên thấu.
- **Quần:** quần short trắng, vải nhẹ, ngắn trên đầu gối, ôm vừa người.
- **Tóc:** tóc nâu dài, BUỘC ĐUÔI NGỰA CAO, có vài sợi tóc mai rủ 2 bên mặt.
  Không xõa, không búi cao, không đổi kiểu giữa các clip.
- **Trang điểm:** nhẹ tự nhiên, môi hồng nhạt (giữ như v19 gốc).
- **Phụ kiện:** chỉ 1 sợi dây chuyền mảnh (như trong ảnh). Không thêm phụ kiện khác.

Đây là bộ đồ ở nhà thật (bộ ngủ/pyjama), vải thoáng mát nhẹ, thu hút nhưng không hở hang,
không phải đồ đi chơi (không jeans, không áo thun đi chơi).

## 2. Đính chính — bỏ áo thun xám v2.2

Khối IDENTITY v2.2 ghi "áo thun xám FITTED" là do Ziggy tự viết bằng chữ, KHÔNG khớp
ảnh tham chiếu v19-nha-tam (ảnh thật là áo hai dây trắng + short trắng + đuôi ngựa cao).
Từ nay bỏ áo thun xám, khóa đúng bộ áo hai dây trắng + short trắng + đuôi ngựa cao.
Mọi prompt, mọi luật, mọi lệnh cho US đều dùng bộ này.

## 3. Các kiểu khác (chỉ dùng khi Saek duyệt)

- **Váy trắng hai dây ngắn** (ảnh v19-vay-trang): kiểu chính cho ảnh chân dung/quảng cáo
  ngoài nhà, không dùng cho cảnh dọn nhà.
- **Đồ bơi trắng** (ảnh v19-do-boi-khoe-uu-diem): chỉ dùng cho cảnh biển/bể bơi,
  Saek đã duyệt 18/11/2026.
- **Váy body đen / crop top hở eo** (ảnh v19-vay-body-den, v19-ho-eo): chỉ dùng khi
  sản phẩm cần khoe eo/cơ bụng, Saek duyệt từng lần.

## 4. Cách khóa trong prompt video (cho US)

- Ảnh tham chiếu thời trang: refs/v19-nha-tam.jpg.b64 — dùng làm first frame cho mọi
  clip cảnh ở nhà (cùng với ảnh hero v19-do-boi-khoe-uu-diem làm chuẩn mặt/body).
- Mô tả thời trang lặp NGUYÊN VĂN mọi lần (tiếng Anh, để trong prompt video):
  "white fitted spaghetti-strap camisole and white shorts, brown hair in a high ponytail,
  light natural makeup, light pink lips"
- Không tả lại kiểu tóc/quần áo bằng lời khác, không thêm bớt món nào.
- Kiểm tra cuối: so khung hình trong clip với ảnh v19-nha-tam — áo khác, quần khác,
  tóc khác (xõa/búi) là LỖI CHẶN CỨNG, làm lại clip.

## 5. Quy tắc tiết kiệm token video

- KHÔNG làm clip test riêng để kiểm tra thời trang (Saek 18/11/2026: không có dư token
  để test). Thời trang chỉ được kiểm tra trong video thật (bản làm lại / video ngày mới),
  bằng ảnh tham chiếu + prompt khóa, không tốn thêm clip test.
- Ảnh tham chiếu thời trang làm bằng ảnh (token ảnh của Ziggy), không tốn token video của US.
