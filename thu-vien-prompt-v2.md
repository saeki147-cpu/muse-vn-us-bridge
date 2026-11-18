# Thư viện Prompt v2.0 — 15/11/2026, 19:14
Nâng cấp từ v1.0 sau research đánh giá thực tế. Saek lệnh: video đẹp, mỗi video ngắn đều có câu chuyện, khắc phục lỗi AI nhìn không giống người thật.

## Nguồn kiểm chứng hôm nay
- Runway test 01/2026, 1.043 người xem clip 5 giây: đoán đúng thật/giả chỉ 57,1%, gần như tung đồng xu. Nhưng clip có mặt, tay, người đang làm việc thì người xem đoán đúng 58-65%. Nghĩa là mặt/tay càng lộ càng dễ bị bắt lỗi. Nguồn: predis.ai/resources/your-ai-video-looks-fake-for-five-fixable-reasons/
- T2VPhysBench: 10 model text-to-video, 12 định luật vật lý, model nào cũng dưới 0,60 điểm. Chuyển động không có trọng lượng là lỗi chung, không riêng Muse.
- AI Video Toolbox: da nhựa, mắt không track, tay lỗi là 3 lỗi đầu tiên phá ảo giác.
- Instagram Natalie Levi Aharon, 15/11/2026: chữ "visible pores" trong cận cảnh làm mặt già hơn. Giữ "natural skin texture" + "85mm lens", bỏ "visible pores" ở cận cảnh, giữ lại ở cảnh nửa người.

## Lỗi 5: Da nhựa như sáp
- Dấu hiệu: da mịn quá, không lỗ chân lông, không nếp nhăn, bóng như búp bê.
- Sửa: mô tả da thật, không mô tả da đẹp. "natural skin texture, fine facial detail, soft specular highlights, realistic pores, restrained contrast, no beauty-filter smoothing" + "film grain, 35mm lens, shallow depth of field".
- Cận cảnh: bỏ "visible pores", giữ "natural skin texture, 85mm lens".
- Nửa người / toàn thân: giữ "visible pores" được.
- Negative: plastic skin, airbrushed skin, wax skin, CGI, cartoon.

## Lỗi 6: Mắt chết, nhìn chằm chằm, không chớp
- Dấu hiệu: mắt nhìn thẳng camera không nhúc nhích, không chớp, không có chuyển động nhỏ.
- Sửa: người thật chớp 15-20 lần/phút, mắt luôn chuyển động nhỏ. Cho mắt 1 việc: nhìn sang trái, nhìn xuống sản phẩm, nhìn theo tay. Cắt cảnh mỗi 6-10 giây, không để 1 mặt nhìn thẳng quá lâu.
- Áp dụng YUJIAO: cảnh 18-28s, cô gái nhìn gương rồi nhìn xuống vòi, gật đầu 1 lần, không nhìn thẳng camera quá 2 giây.

## Lỗi 7: Miệng / răng mờ khi nói
- Dấu hiệu: nói thì răng mờ, môi không khớp tiếng, miệng méo.
- Sửa: giọng đọc trước, cảnh cắt theo giọng (đã có từ bài học 5). Mỗi cảnh chỉ 1 câu thoại ngắn, dưới 8 chữ. Không để nhân vật nói dài trong cận cảnh. Cảnh nói thì quay trung cảnh, không cận miệng.
- Áp dụng: 4 câu thoại YUJIAO, mỗi câu 1 cảnh, câu dài nhất 11 chữ, đã chia sẵn.

## Lỗi 8: Chuyển động không có trọng lượng, robot
- Dấu hiệu: tay di chuyển đều đều, đầu quay nhanh, vật không có quán tính.
- Sửa: 1 cảnh chỉ 3-5 giây, 1 hành động. Mô tả chuyển động cơ thể, không mô tả cảm xúc. "shoulders slump, head drops" thay vì "feels sad". Tay đang chuyển động thì ít bị soi hơn tay đứng yên cận cảnh.
- Đã có ở v1.0, giữ nguyên, thêm giới hạn 3-5 giây/cảnh.

## Lỗi 9: Ánh sáng không khớp
- Dấu hiệu: mặt sáng từ trái, bóng đổ sang phải, nền sáng kiểu khác, màu thay đổi giữa các cảnh.
- Sửa: ghi rõ nguồn sáng trong mọi cảnh. Ví dụ: "soft daylight from bathroom window camera left, warm bounce from tiles, light direction constant in all scenes". Dùng ảnh tham chiếu trước, không dùng text-only.
- Áp dụng YUJIAO: ánh sáng nhà tắm buổi sáng, cửa sổ bên trái, giữ nguyên mọi cảnh.

## Lỗi 10: Tay vẫn là điểm yếu nhất 2026
- Đã có ở v1.0, bổ sung theo research mới: khung hình từ ngực trở lên để tay khỏi khung hình khi không cần tay. Khi cần tay, tay phải cầm vật có hình rõ (miếng YUJIAO xanh lá + trắng), tay đang chuyển động, cảnh ngắn dưới 5 giây.
- Negative chung: extra fingers, deformed hands, fused fingers, extra limbs, morphing face, inconsistent face, blurry face, distorted eyes, flickering, watermark, text overlay, logo.

## Lỗi 11: Logo/chữ trên sản phẩm bị vẽ sai, bắt làm lại cũng không sửa được (mới, quét 06:49 ngày 17/11/2026)
- Dấu hiệu: Muse vẽ sai logo áo đoàn/công đoàn/hội sinh viên; train lại rồi tắt máy, hôm sau nó kêu làm lại mà chỗ sai vẫn y nguyên. Nguồn: bài nhóm Muse AI Việt Nam 03:55 ngày 17/11/2026 (4 bình luận) + cách khắc phục trong bình luận.
- Sửa: đưa ảnh thật của sản phẩm/logo cho Muse học trước rồi mới kêu tạo; prompt ghi rõ copy đúng y ảnh mẫu, không tự bịa chữ/logo. Nếu vẫn sai thì lấy ảnh sang phần mềm khác chỉnh tiếp ở hậu kỳ, đừng bắt Muse làm lại mãi.
- Áp dụng YUJIAO: gửi kèm ảnh thật miếng YUJIAO làm ảnh tham chiếu; prompt đã thêm dòng copy đúng hình dáng, màu xanh lá + trắng và logo, không bịa chữ; checklist đã thêm mục kiểm tra logo/chữ.

## Công thức chuẩn cho 1 cảnh giống người thật — dùng cho mọi video
1. Ảnh tham chiếu trước: 1 ảnh chân dung rõ mặt, mặt trước, tóc + quần áo khóa, dùng làm ảnh đầu cho mọi cảnh.
2. Khung trung cảnh, không cận cảnh quá 2 giây.
3. 1 cảnh 3-5 giây, 1 hành động, 1 câu thoại.
4. Ánh sáng có nguồn rõ, giữ nguyên mọi cảnh.
5. Da thật, film grain, 35mm, shallow depth of field.
6. Tay: hoặc ngoài khung, hoặc đang cầm vật, hoặc đang chuyển động.
7. Cắt cảnh mỗi 6-10 giây, không để 1 góc quá lâu.

## Negative prompt chuẩn v2.0 — dán vào mọi lệnh
```
extra fingers, deformed hands, fused fingers, extra limbs, morphing face, inconsistent face, shifting facial features, blurry face, distorted eyes, plastic skin, airbrushed skin, wax skin, CGI, cartoon, unnatural movement, flickering, watermark, text overlay, logo, low quality
```

## Checklist QA v2.0 — test 10 giây trước khi gửi Saek
- Xem 1 lần có tiếng, 1 lần không tiếng, trên điện thoại.
- Mặt và tay giữ nguyên hình suốt clip?
- Mọi thứ chuyển động có trọng lượng không?
- Ánh sáng có khớp nhau không?
- Mắt có chớp, có nhìn đúng hướng không?
- Miệng có khớp giọng không?
- 1 mục không đạt thì làm lại cảnh đó, không làm lại cả video.

## Phiên bản
- v1.0 — 15/11/2026: 4 lỗi tay, mắt, mặt, chuyển động.
- v2.0 — 15/11/2026 19:14: thêm 6 lỗi da nhựa, mắt chết, miệng, trọng lượng, ánh sáng, tay nâng cao + công thức chuẩn + checklist test 10 giây.
- v2.1 — 17/11/2026 06:49: thêm Lỗi 11 (logo/chữ trên sản phẩm vẽ sai — đưa ảnh thật làm mẫu, sai thì sửa ở hậu kỳ, không bắt Muse làm lại mãi).
