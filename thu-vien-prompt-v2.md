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

## Lỗi 12: Body v19 mất — vòng 1 106cm biến mất trong clip (mới, 18/11/2026, Saek phát hiện)
- Dấu hiệu: 3 clip 2b/3/4 do US làm 18/11 — diễn viên mặc áo ba lỗ trắng + quần short trắng (không phải áo thun xám như prompt), dáng mảnh, vòng 1 không thấy. Clip 1 cũng đã trôi mặt.
- Nguyên nhân:
  1. Prompt ghi "plain light grey t-shirt" mà không ghi độ ôm → model vẽ áo rộng, che mất vòng 1. Số đo 106cm bằng chữ không tự dịch thành tỉ lệ thấy được.
  2. Không có lệnh khung hình giữ thân → model cắt khung trên ngực hoặc quay xa làm dáng mảnh đi.
  3. Model tự đổi trang phục (áo ba lỗ trắng thay áo thun xám) — prompt không khóa đủ mạnh.
- Sửa: khối IDENTITY v2.2 dưới đây — bắt buộc cho mọi clip từ Ngày 2 trở đi. Áo phải ghi FITTED/snug, không loose/oversized; mô tả vòng 1 thấy rõ qua vải áo ôm (rãnh tự nhiên, không hở da dưới xương quai xanh); khung hình trung cảnh giữ toàn bộ thân từ ngực tới đầu gối trong mọi cảnh, không cắt trên vòng 1, không quay dáng mảnh.

## Khối IDENTITY v2.2 — dán nguyên văn vào ĐẦU mọi prompt, không đổi 1 chữ
```
IDENTITY (frozen, do not change a word): the woman is the v19 actress — oval face, big bright sparkling eyes, light natural makeup, light pink lips, white-pink healthy skin with real texture, long brown hair in a low ponytail, no hair covering chest. Body: tall 190cm, bust 106cm full and firm with a deep natural line through her top, waist 58cm with light visible abs, hips 90cm, long legs 122cm. She wears a FITTED light grey t-shirt (snug, close to the body, NOT loose, NOT oversized) that follows her curves and clearly shows her full 106cm bust and slim 58cm waist — real home clothes, modest, no skin exposed below the collarbone, no see-through fabric. Camera: medium shot, her full torso from chest to knees stays in frame in every shot, never crop above the bust, never frame her as slim. Same face, same fitted grey t-shirt, same bathroom light in every clip — do not change anything.
```

## Checklist TIẾT KIỆM TOKEN — kiểm tra xong mới được tạo (Saek lệnh 18/11/2026)
- Prompt đã có: khối IDENTITY v2.2 nguyên văn, độ ôm áo ghi rõ, khung hình giữ thân, ảnh tham chiếu đính kèm, 1 hành động/cảnh, negative đầy đủ. Thiếu 1 mục thì chưa tạo.
- Tối đa 2 lần tạo/cảnh (1 chính + 1 làm lại). Lần 2 vẫn lỗi thì dùng bản tốt hơn, sửa ở hậu kỳ, KHÔNG tạo lần 3.
- Ngân sách tuần tài khoản US (18/11/2026): đã dùng 13%, đặt lại 25/11, còn 87% ≈ 33 clip (mỗi clip ~2,6%). 1 video/ngày = 4 clip → 6 ngày còn lại (19–24/11) hết 24 clip, dư ~9 clip làm lại. Không làm video ngoài kế hoạch 1/ngày.

## Lỗi 13: Tiết tấu chậm như quay chậm (mới, 18/11/2026, Saek nhận xét video Ngày 1)
- Dấu hiệu: động tác chà chậm lặp lại 7–10 giây/clip; chuyển cảnh hòa trộn 0,5 giây làm ì; hook 3 giây đầu quay chậm không giật được chú ý; năng lượng phẳng cả 35 giây.
- Sửa: prompt ghi rõ tốc độ — "quick, energetic strokes" (chà nhanh, dứt khoát), mỗi động tác 2–3 giây, 1 clip 10 giây phải có 2–3 nhịp động tác; chuyển cảnh cắt cứng (hard cut), hòa trộn tối đa 0,2 giây; hook: 1 giây đầu là vấn đề (kính ố rõ), giây 2–3 mới đưa sản phẩm vào; nhịp nhanh ở demo, chậm lại ở CTA để người xem kịp đọc chữ.

## Lỗi 14: Khung split trước/sau không hiện (mới, 18/11/2026, video Ngày 1)
- Dấu hiệu: câu thoại hứa "một bên còn ố, một bên trong veo" nhưng video chỉ cho kính sạch dần, không có khung chia đôi nào. Prompt có ghi "split view" nhưng model không vẽ; chuyển động chà phá vỡ khung chia đôi.
- Sửa: cảnh split = TOÀN BỘ cảnh là 1 khung chia đôi tĩnh — nửa trái còn ố trắng, nửa phải trong veo, miếng chà nằm đúng ranh giới, KHÔNG chà (không chuyển động). Muốn chà thì chà ở cảnh khác. Một cảnh chỉ được hứa 1 hình duy nhất, và hình đó phải là toàn bộ cảnh.

## Lỗi 15: Hai mặt khác nhau trong 1 video (mới, 18/11/2026, video Ngày 1)
- Dấu hiệu: 0–10s cô áo thun xám (mặt tròn, già hơn), 10–35s đổi thành cô khác (áo ba lỗ trắng, mặt trẻ hơn). Không ai là v19. Model video giữ mặt kém hơn model ảnh rất nhiều.
- Sửa: 1 ảnh tham chiếu duy nhất (ảnh v19 đồ bơi khoe ưu điểm, Saek duyệt 18/11/2026, file refs/v19-do-boi-khoe-uu-diem.jpg.b64) làm chuẩn mặt + body cho MỌI clip; US phải đính kèm ảnh này vào MỖI lần tạo clip (không chỉ ghi bằng chữ) và xác nhận đã đính kèm; clip nào mặt trôi thì neo lại từ ảnh gốc, không nối từ clip đã trôi; 1 câu thoại chỉ 1 hình; ghi rõ diễn biến biểu cảm (hơi bực → ngạc nhiên → hài lòng), không để 1 biểu cảm tiêu cực kéo dài cả cảnh.

## Phiên bản
- v1.0 — 15/11/2026: 4 lỗi tay, mắt, mặt, chuyển động.
- v2.0 — 15/11/2026 19:14: thêm 6 lỗi da nhựa, mắt chết, miệng, trọng lượng, ánh sáng, tay nâng cao + công thức chuẩn + checklist test 10 giây.
- v2.1 — 17/11/2026 06:49: thêm Lỗi 11 (logo/chữ trên sản phẩm vẽ sai — đưa ảnh thật làm mẫu, sai thì sửa ở hậu kỳ, không bắt Muse làm lại mãi).
- v2.2 — 18/11/2026: thêm Lỗi 12 (body v19 mất vòng 1 — áo phải FITTED, khung hình giữ thân) + khối IDENTITY v2.2 + checklist tiết kiệm token (tối đa 2 lần tạo/cảnh, ngân sách tuần US).
- v2.3 — 18/11/2026: thêm Lỗi 13 (tiết tấu chậm như quay chậm), Lỗi 14 (khung split trước/sau không hiện), Lỗi 15 (hai mặt trong 1 video) — đúc kết từ video YUJIAO Ngày 1.
