# Hệ thống tự động làm video có truyện — Gia dụng, Nhà cửa
Saek lệnh 15/11/2026 19:14: phát triển hệ thống tự động, Muse tạo video đẹp, mỗi video ngắn đều có câu chuyện, khắc phục lỗi AI nhìn không giống người thật.
File này là bản thiết kế hệ thống, dùng cho mọi video sau này. Thư viện Prompt chi tiết ở hidden_files/thu-vien-prompt-v2.md.

## Hệ thống chạy thế nào — 6 bước, không đợi Saek nhắc
1. **Chọn sản phẩm:** kiểm chứng 5 câu Saek chốt — vì sao chọn, tại sao bây giờ, căn cứ số bán 7 ngày/GMV/hoa hồng/giá/đánh giá + nguồn + ngày, có tạo được thu nhập không, rủi ro gì. Không qua 5 câu thì không làm.
2. **Chọn truyện:** lấy 1 trong 5 mẫu truyện dưới đây, khớp với sản phẩm. Không làm video chỉ quay sản phẩm.
3. **Viết giọng đọc trước:** 4 câu thoại, mỗi câu 1 cảnh, câu dưới 8-11 chữ. Giọng đọc xong mới cắt cảnh theo giọng.
4. **Khóa nhân vật:** 1 ảnh chân dung rõ mặt, mặt trước, tóc + quần áo khóa, dùng làm ảnh đầu mọi cảnh. Nhân vật tùy sản phẩm: nam, nữ, ông, bà.
5. **Tạo clip:** mỗi cảnh 3-5 giây, 1 hành động, trung cảnh, ánh sáng có nguồn rõ, giữ nguyên mọi cảnh. Dán negative prompt v2.0 vào mọi lệnh.
6. **Kiểm tra 10 giây:** xem có tiếng + không tiếng trên điện thoại. 1 mục không đạt thì làm lại cảnh đó. Đạt mới gửi Saek duyệt, Saek duyệt mới đăng.

## 5 mẫu truyện dùng cho ngách Gia dụng — mỗi video chỉ dùng 1 mẫu
### Mẫu 1: Vấn đề — Thử — Chứng minh
Kính ố trắng, lau hoài không sạch → chà thử 1 bên → 1 bên còn ố, 1 bên trong veo.
Dùng cho: YUJIAO Ngày 1, chất tẩy cặn, nước giặt.
### Mẫu 2: Mất điện / sự cố ban đêm
2h sáng mất điện, đi trong tối vấp ngã → đèn tự bật → cả nhà an toàn.
Dùng cho: đèn năng lượng (bản test truyện, không phải sản phẩm chính).
### Mẫu 3: So sánh thật
Sản phẩm cũ vs sản phẩm mới, cùng 1 vết bẩn, cùng 1 thời gian → bên nào sạch hơn, dai hơn, thấm hơn.
Dùng cho: TOPGIA vs Caipiao, nước giặt Tidy Home.
### Mẫu 4: Trước — Sau 1 lần dùng
Nhà tắm trước: gương mờ, vòi ố → sau 1 lần chà: gương sáng, vòi sáng.
Dùng cho: YUJIAO, Mise giấy treo tường.
### Mẫu 5: Người thân dùng
Mẹ già / ông bà dùng sản phẩm, đi lại an toàn, nhà sạch hơn → kết: 1 món đồ nhỏ, cả nhà yên tâm.
Dùng cho: đèn, khăn giấy, đồ gia dụng cho người lớn tuổi.

## YUJIAO Ngày 1 — áp dụng hệ thống v2.0
- Truyện: Mẫu 1, Vấn đề — Thử — Chứng minh.
- 4 cảnh, 35 giây, 9:16, giọng đọc trước:
  1. 0-3s: "Kính nhà tắm ố trắng thế này, lau hoài không sạch."
  2. 3-18s: "Chà thử miếng này xem — một bên còn ố, một bên trong veo."
  3. 18-28s: "Sạch thật, cả gương với vòi cũng sáng luôn."
  4. 28-35s: "Kính sạch trong 1 lần chà."
- Nhân vật khóa: phụ nữ Việt ~28 tuổi, tóc dài đen buộc thấp, áo thun xám nhạt, da tự nhiên, film grain, 35mm, ánh sáng nhà tắm buổi sáng từ cửa sổ bên trái, giữ nguyên mọi cảnh.
- Tay: cầm miếng YUJIAO xanh lá + trắng, đang chà, cảnh ngắn, không cận tay đứng yên.
- Mắt: nhìn gương rồi nhìn xuống vòi, gật 1 lần, không nhìn thẳng camera quá 2 giây.
- Negative v2.0 đã dán vào lệnh.

## Tự động nghĩa là gì ở đây — nói thật
- Tự động ở khâu chuẩn bị: Ziggy tự chọn sản phẩm bằng số liệu, tự chọn mẫu truyện, tự viết giọng + kịch bản, tự kiểm tra QA, tự chuẩn bị bản nháp sẵn.
- Không tự động ở khâu đăng: Saek duyệt bản cuối mới đăng. Không tự động ở khâu tạo video bằng tài khoản Muse Mỹ: vẫn cần người thân paste lệnh, hoặc test tool GitHub bằng tài khoản phụ, vì Muse chưa có API video chính thức.
- Mỗi video đăng xong, ghi lại: diễn viên nào, góc nào, giữ người xem ở giây 3, giây 10, xem hết bao nhiêu %. Số liệu đó quyết định video sau dùng diễn viên/góc nào, không đoán.
