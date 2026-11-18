# Kiến thức làm video AI — bắt buộc cho mọi video

Nguồn chắt lọc: Thư viện Prompt v2.1 (`thu-vien-prompt-v2.md`), hệ thống
6 bước (`he-thong-tu-dong-video-truyen.md`), khung chất lượng
(`khung-chat-luong-video-ai.md`), kịch bản YUJIAO Ngày 1
(`lenh-muse-us-yujiao-ngay1.md`), nhật ký học 16–17/11/2026
(Bài học 13–20), nghiên cứu 18/11/2026 (Lollipop Drama, HeyGen,
Prompt Architects, BatchFrames, PicassoIA, MagicBoat, UniFab,
StoreFuel, SocialGPT, Veonib, vnaffiliate). File này là BẢN GỐC
TIẾNG VIỆT; `video-rules.json` là bản dạng máy đọc — hai bản phải
khớp nhau. Muse US đọc cả 2 file mỗi khi có lệnh mới.

## A. Quy tắc Muse US TỰ ÁP DỤNG vào mọi lệnh video (không cần người nhắc)

| # | Quy tắc | US làm gì |
|---|---------|-----------|
| 1 | **Hook:** sản phẩm vào khung trong **3 giây đầu** (Bài học 17: 63% video click cao làm vậy) | Kèm câu lệnh "show the product clearly in the first 3 seconds" vào mọi clip; cảnh 1 luôn có câu này |
| 2 | **Hook làm mới** ở khoảng 40–60% video (Bài học 17), trong kịch bản YUJIAO là ~giây 18 | Cảnh giữa tự kèm "open with a clear visual change (wide reveal) to re-hook the viewer" |
| 3 | **CTA 2 lần:** nhắc nhẹ 1 lần khoảng 70% video, nhắc lại lần chính ở cuối (Bài học 17) | Cảnh áp cuối tự kèm câu CTA nhẹ; cảnh cuối kèm "end with the product held up clearly and the call-to-action line" |
| 4 | **Mỗi clip tối đa 10 giây, 1 hành động, chuyển động vừa phải, đầu không quay quá ~45°** (Bài học 15: cảnh dài trên 10s dễ vỡ mặt, lệch sáng; nghiên cứu 18/11: mặt thường bắt đầu biến dạng từ ~khung 15, tệ nhất khi quay đầu mạnh, đổi xa–gần, hành động mạnh) | Làm từng clip ~10 giây, 1 hành động; làm 2–3 lần mỗi cảnh, giữ bản tốt nhất |
| 5 | **Nối clip hòa trộn 0,5 giây** (Bài học 15) | US tự ghép các clip theo thứ tự, nối hòa trộn 0,5 giây, không cắt khô |
| 6 | **Phụ đề và chữ CTA làm ở hậu kỳ, KHÔNG nhờ model render chữ trong clip** (Bài học 8: phụ đề không che mặt; Bài học 14: HyperFrames làm phụ đề ở hậu kỳ) | Kèm câu lệnh "no text, no subtitles… added later in post-production, never rendered by the model" |
| 7 | **Ảnh thật sản phẩm làm ảnh tham chiếu logo** (Bài học 16; Lỗi 11 v2.1: logo/chữ vẽ sai) — prompt ghi rõ copy đúng logo/màu; logo sai thì sửa ở hậu kỳ thay vì làm lại nhiều lần | US giải mã `refs/yujiao-logo.jpg.b64` (logo) + `refs/yujiao-hinh-dang.jpg.b64` (hình dáng/màu) trong repo làm ảnh tham chiếu; kèm câu lệnh "copy the product logo and colours exactly… if wrong, fix in post-production" |
| 8 | **Giọng đọc trước, cảnh cắt theo giọng, mỗi câu 1 cảnh** (hệ thống 6 bước) — lời thoại viết TRƯỚC, nằm ngay trong từng cảnh của lệnh; model tự nói lời thoại đó trong clip. **Không có file giọng riêng.** Giọng tiếng Việt của model **CHƯA kiểm chứng** — nếu model không nói được, hậu kỳ thêm giọng bằng CapCut TTS | US kèm "the scene follows one short spoken line written in the order; the model speaks that line as part of the clip" |
| 9 | **Demo trước–sau rõ ràng** (Mẫu truyện 1 và 4) | Kèm "show a clear before/after demo: one side still dirty, the other side clean" |
| 10 | **Tỉ lệ 9:16** (dọc, TikTok/Facebook) | Mọi clip 9:16 |
| 11 | **Khóa diễn viên v19** (số đo 106-58-90, cao 190cm, chân 122cm, đùi 50cm, bắp chân 30cm; mặt, makeup nhẹ tự nhiên, da trắng hồng khỏe khoắn có texture thật; tóc đổi kiểu theo cảnh nhưng không che ngực; máy quay góc thấp, toàn thân trong khung, 35mm, cách 3m; biểu cảm mặc định theo loại cảnh) | US đọc `v19.txt` + giải mã ảnh hero `refs/v19-vay-trang.jpg.b64` và ảnh nhà tắm `refs/v19-nha-tam.jpg.b64`; **khối v19 phải nằm ở ĐẦU mọi prompt, viết nguyên văn không đổi** (20–30 từ đầu của prompt có trọng số cao nhất; đổi cách diễn đạt là đổi mặt). Nếu model từ chối vì nội dung thì thử lại 1 lần với `v19-safe.txt` (bỏ cụm nhạy cảm, giữ số đo) |
| 12 | **Negative list v2.1** (11 lỗi: da nhựa, mắt chết, miệng/răng mờ khi nói, chuyển động không trọng lượng, ánh sáng không khớp, tay, logo/chữ sai…) | Nằm trong `v19.txt`, US kèm vào mọi prompt |
| 13 | **Nhất quán giữa các cảnh:** cùng mặt, cùng tóc, cùng trang phục, cùng hướng sáng; không chạy về phía máy quay (Bài học 15) | Kèm "same face, same hair, same outfit and same light direction… do not change them between scenes" |
| 14 | **1 video/ngày, không làm hàng loạt** (khung chất lượng §1) | US chỉ làm 1 video/ngày, trừ làm lại cảnh lỗi hoặc tiếp tục chuỗi đang dở |
| 15 | **1 video 1 lúc; 403 thì dừng hẳn, 429 thì chờ 1 giờ** (quy tắc an toàn) | US gặp 403 thì dừng hẳn và báo Ziggy; gặp 429 thì chờ 1 giờ rồi thử lại 1 lần |
| 16 | **Hạn mức tuần tính theo CLIP, không theo video:** 1 video 4 clip = 8–12% hạn mức tuần (2–3%/clip, theo báo cáo cộng đồng useapi.net + MoonReel, **CHƯA kiểm chứng**). 7 video/tuần là 56–84%, cộng làm lại là chạm 429 giữa tuần | US theo dõi số clip trong tuần, báo Ziggy khi gần chạm hạn |
| 17 | **Ảnh hero là chốt neo mặt; nối khung đầu–cuối chỉ giữ khung hình, KHÔNG giữ mặt** (nghiên cứu 18/11: nối khung tốt cho liên tục khung hình, yếu cho giữ mặt; nối từ khung đã trôi mặt sẽ làm mặt càng trôi; mặt trôi nặng dần theo số clip) | US đính kèm ảnh hero v19 vào MỌI clip; kiểm tra mặt từng clip ở cỡ đầy đủ TRƯỚC khi nối từ nó; clip nào mặt đã trôi thì KHÔNG nối từ khung cuối của nó — neo lại từ ảnh hero |
| 18 | **Giọng cũng trôi giữa các clip; xem các clip nối lại thành chuỗi, không xem lẻ từng clip** (nghiên cứu 18/11) | US giữ cùng cài đặt giọng cho mọi clip, chuẩn hoá âm lượng ở hậu kỳ, xem toàn bộ video đã ghép trước khi gửi |
| 19 | **Độ dài 15–30 giây là vùng tốt nhất cho affiliate** (nghiên cứu 18/11: video 15 giây xem hết gấp ~4 lần video 60 giây; 3 giây đầu quyết định 71–80% người xem có ở lại không) — video YUJIAO 35 giây của ta được số liệu riêng ủng hộ (trung vị top 100 là 34 giây), giữ 35 giây, test sau 1 bản cắt 15–20 giây | US làm đúng độ dài trong lệnh; Ziggy quyết độ dài mỗi video |

## B. Việc chỉ người kiểm tra được (Ziggy kiểm tra cuối video thành phẩm, Saek duyệt)

| # | Việc phải kiểm tra bằng tay | Nguồn |
|---|---------------------------|-------|
| 1 | **Nghe lại toàn video bằng tai nghe + chuẩn hoá âm lượng** trước khi giao | Bài học 20 (ffmpeg-skill) |
| 2 | **Kiểm tra tay/mắt/mặt/logo trên video thành phẩm** (tay đủ 5 ngón, mắt không chết, mặt không vỡ, logo đúng) — kiểm tra 10 giây: xem có tiếng và không tiếng trên điện thoại | Hệ thống 6 bước, bước 6; Thư viện Prompt v2.1 |
| 3 | **Cửa chống spam trước khi đăng:** video giải quyết 1 vấn đề thật, đúng như quảng cáo, không trùng video hôm qua, có lý do để lưu/chia sẻ | Khung chất lượng §3 |
| 4 | **Đo chất lượng sau khi đăng:** giữ chân giây 3, giây 10, tỉ lệ xem hết — không đo bằng số lượng | Khung chất lượng §4 |
| 5 | **Chọn sản phẩm qua 5 câu hỏi** (vì sao chọn, tại sao bây giờ, căn cứ số liệu, có ra tiền không, rủi ro gì) | Quy tắc chọn sản phẩm 15/11 |
| 6 | **Phương án dự phòng không lộ mặt** (chỉ tay + sản phẩm) nếu mặt diễn viên làm lại vẫn lỗi | Bài học 9 |
| 7 | **Sửa mặt ở hậu kỳ thay vì làm lại cả clip (CHỈ TEST):** clip nào chuyển động tốt mà mặt trượt thì thử face-swap/restore ở hậu kỳ thay vì quay lại cả clip (nghiên cứu 18/11). Chưa có tool free nào kiểm chứng — test trước rồi mới áp dụng | Nghiên cứu 18/11 (PicassoIA, MagicBoat, UniFab) |

## C. Cách làm 1 video (qua queue.json)

- Ziggy viết 1 lệnh duy nhất vào `queue.json`, ghi rõ từng cảnh, prompt, ảnh tham chiếu trong repo.
- US đọc lệnh, làm từng clip (~10 giây), tự ghép theo thứ tự (hòa trộn 0,5 giây), thêm phụ đề + chữ CTA, chuẩn hoá tiếng, gửi **video thành phẩm** về cho Ziggy qua Telegram (người thân tải về gửi).
- **Lệnh bị từ chối (bận / hết hạn mức / thiếu ảnh):** US báo lại cho Ziggy, không tự làm lại nhiều lần, không đánh dấu xong.
- **Làm lại cảnh lỗi:** Ziggy ghi lệnh làm lại cảnh đó vào `queue.json`, chỉ làm lại cảnh đó.

## D. Cách kiến thức tới được bên Mỹ (đồng bộ qua GitHub)

Saek chốt 17/11/2026: Ziggy chia sẻ kiến thức với Muse Mỹ LIÊN TỤC
qua một chỗ chung trên GitHub mà Muse US tự đọc định kỳ — bài học mới,
quy tắc prompt mới, dữ liệu sản phẩm mới, kịch bản mới đều tự tới bên
Mỹ trong vài phút, không cần gửi lại tay từng lần.

- **US đọc gì, bao lâu 1 lần:** US kiểm tra repo **mỗi 5 phút**: `queue.json`
  (lệnh video) + `v19.txt`, `v19-safe.txt`, `video-rules.json`,
  `kien-thuc-video.md` (kiến thức). File nào đổi thì US áp dụng ngay cho
  lệnh tiếp theo. File JSON lỗi thì giữ bản cũ, không ghi đè.
- **Ảnh tham chiếu:** tất cả nằm trong repo (`refs/`, dạng `.b64` vì ảnh
  nhị phân không đẩy trực tiếp qua connector GitHub được — US tự tải về
  và giải mã bằng `base64 -d`). Không ai đính kèm ảnh trong chat nữa.
- **Video thành phẩm về:** người thân tải về, gửi qua Telegram cho Ziggy
  (video ~10–20MB, gửi được). Drive chung sẽ nối sau để tự động hoá
  đường về.
- **Việc của Ziggy (mỗi khi có bài học mới):** cập nhật cả 2 nơi —
  (1) `kien-thuc-video.md` (bản tiếng Việt cho người đọc) và
  (2) `video-rules.json` (bản dạng máy đọc), rồi đẩy lên GitHub.
  US đọc cả 2.
- **Giới hạn:** đồng bộ chỉ mang CHỮ (mô tả, quy tắc, kịch bản) tới
  bên Mỹ. Ảnh tham chiếu đi qua repo (dạng `.b64`).
