# Kiến thức làm video AI — bắt buộc cho mọi video

Nguồn chắt lọc: Thư viện Prompt v2.1 (`thu-vien-prompt-v2.md`), hệ thống
6 bước (`he-thong-tu-dong-video-truyen.md`), khung chất lượng
(`khung-chat-luong-video-ai.md`), kịch bản YUJIAO Ngày 1
(`lenh-muse-us-yujiao-ngay1.md`), nhật ký học 16–17/11/2026
(Bài học 13–20). File này là BẢN GỐC TIẾNG VIỆT; bot dịch các quy tắc
thành câu lệnh tiếng Anh trong `bot.py` (hằng `SCENE_RULES_EN` và file
`video-rules.json`). Hai bản phải khớp nhau — test `test_bot.py` kiểm
tra từng quy tắc đều có mặt trong prompt cuối cùng bot gửi đi.

## A. Quy tắc bot TỰ ÁP DỤNG vào mọi lệnh video (không cần người nhắc)

| # | Quy tắc | Bot làm gì |
|---|---------|-----------|
| 1 | **Hook:** sản phẩm vào khung trong **3 giây đầu** (Bài học 17: 63% video click cao làm vậy) | Kèm câu lệnh "show the product clearly in the first 3 seconds" vào mọi clip; cảnh 1 luôn có câu này |
| 2 | **Hook làm mới** ở khoảng 40–60% video (Bài học 17), trong kịch bản YUJIAO là ~giây 18 | Cảnh giữa tự kèm "open with a clear visual change (wide reveal) to re-hook the viewer" |
| 3 | **CTA 2 lần:** nhắc nhẹ 1 lần khoảng 70% video, nhắc lại lần chính ở cuối (Bài học 17) | Cảnh áp cuối tự kèm câu CTA nhẹ; cảnh cuối kèm "end with the product held up clearly and the call-to-action line" |
| 4 | **Mỗi clip tối đa 8 giây**, không quay cảnh dài liên tục trên 10 giây (Bài học 15: cảnh dài trên 10s dễ vỡ mặt, lệch sáng) | Bot tách lệnh dài thành nhiều job, mỗi job 1 cảnh ≤ 8 giây |
| 5 | **Nối clip hòa trộn 0,5 giây** (Bài học 15) | Bot gửi từng clip kèm số cảnh 1, 2, 3…; **Ziggy ghép bằng FFmpeg** khi clip về qua Drive — không nhờ người nhà ghép tay |
| 6 | **Phụ đề và chữ CTA làm ở hậu kỳ, KHÔNG nhờ model render chữ trong clip** (Bài học 8: phụ đề không che mặt; Bài học 14: HyperFrames làm phụ đề ở hậu kỳ) | Kèm câu lệnh "no text, no subtitles… added later in post-production, never rendered by the model" |
| 7 | **Ảnh thật sản phẩm làm ảnh tham chiếu logo** (Bài học 16; Lỗi 11 v2.1: logo/chữ vẽ sai) — prompt ghi rõ copy đúng logo/màu; logo sai thì sửa ở hậu kỳ thay vì làm lại nhiều lần | Bot gắn **2 ảnh tham chiếu**: ảnh diễn viên (5 ảnh khóa, mặc định ảnh váy trắng) + ảnh thật sản phẩm; kèm câu lệnh "copy the product logo and colours exactly… if wrong, fix in post-production" |
| 8 | **Giọng đọc trước, cảnh cắt theo giọng, mỗi câu 1 cảnh** (hệ thống 6 bước) — **quyết định v3:** lời thoại viết TRƯỚC, nằm ngay trong từng cảnh của lệnh; model tự nói lời thoại đó trong clip. **Không có file giọng riêng, không trộn tiếng ở bước này.** Giọng tiếng Việt của model **CHƯA kiểm chứng** — nếu model không nói được, hậu kỳ thêm giọng bằng CapCut TTS bên VN | Bot kèm "the scene follows one short spoken line written in the order; the model speaks that line as part of the clip" |
| 9 | **Demo trước–sau rõ ràng** (Mẫu truyện 1 và 4) | Kèm "show a clear before/after demo: one side still dirty, the other side clean" |
| 10 | **Tỉ lệ 9:16** (dọc, TikTok/Facebook) | Bot gửi `aspect_ratio: 9:16` trong mọi job (tự lui về mặc định nếu server không nhận) |
| 11 | **Khóa diễn viên v19** (số đo 106-58-90, cao 190cm, chân 122cm, đùi 50cm, bắp chân 30cm; mặt, makeup nhẹ tự nhiên, da trắng hồng khỏe khoắn có texture thật; tóc đổi kiểu theo cảnh nhưng không che ngực; máy quay góc thấp, toàn thân trong khung, 35mm, cách 3m; biểu cảm mặc định theo loại cảnh) | Bot kèm toàn bộ `v19.txt` vào TRƯỚC mọi prompt; nếu model từ chối vì nội dung thì thử lại 1 lần với `v19-safe.txt` (bỏ cụm nhạy cảm, giữ số đo) |
| 12 | **Negative list v2.1** (11 lỗi: da nhựa, mắt chết, miệng/răng mờ khi nói, chuyển động không trọng lượng, ánh sáng không khớp, tay, logo/chữ sai…) | Nằm trong `v19.txt`, bot kèm vào mọi prompt |
| 13 | **Nhất quán giữa các cảnh:** cùng mặt, cùng tóc, cùng trang phục, cùng hướng sáng; không chạy về phía máy quay (Bài học 15) | Kèm "same face, same hair, same outfit and same light direction… do not change them between scenes" |
| 14 | **1 video/ngày, không làm hàng loạt** (khung chất lượng §1) | Bot đếm lệnh video trong ngày; lệnh thứ 2 bị từ chối, trừ khi là làm lại cảnh lỗi hoặc tiếp tục chuỗi đang dở (`VIDEO: làm lại Cảnh N: …` / `VIDEO: tiếp tục từ Cảnh N`) |
| 15 | **1 video 1 lúc; 403 thì dừng hẳn, 429 thì chờ 1 giờ** (quy tắc an toàn) | Bot giữ cờ `video_disabled` / `cooldown_until` **lưu xuống đĩa** (`state.json`); khởi động lại vẫn nhớ, không thử lại vô hạn |
| 16 | **Hạn mức tuần tính theo CLIP, không theo video:** 1 video 4 clip = 8–12% hạn mức tuần (2–3%/clip, theo báo cáo cộng đồng useapi.net + MoonReel, **CHƯA kiểm chứng**). 7 video/tuần là 56–84%, cộng làm lại là chạm 429 giữa tuần | Bot đếm số job trong tuần, báo khi ≥ 25 job (~70%); cân nhắc làm lại cảnh lỗi bằng Google Flow thay vì đốt tiếp hạn mức Muse |

## B. Quy tắc CHỈ NGƯỜI mới kiểm tra được (bot KHÔNG tự làm)

Bot không xem được clip, không nghe được tiếng, không biết video có đúng
quảng cáo hay không — nên những việc này KHÔNG được ghi như thể bot tự làm.
**Hậu kỳ do Ziggy VN làm** (ghép clip bằng FFmpeg, chuẩn hoá tiếng, phụ đề
bằng HyperFrames khi đã test xong, không thì CapCut bên VN) khi clip về qua
thư mục Drive chung. Người (bên VN / người thân ở Mỹ) phải kiểm tra trước
khi đăng, theo khung chất lượng:

| # | Việc phải kiểm tra bằng tay | Nguồn |
|---|---------------------------|-------|
| 1 | **Nghe lại toàn video bằng tai nghe + chuẩn hoá âm lượng** trước khi xuất | Bài học 20 (ffmpeg-skill) |
| 2 | **Kiểm tra tay/mắt/mặt/logo trên clip thật** (tay đủ 5 ngón, mắt không chết, mặt không vỡ, logo đúng) — kiểm tra 10 giây: xem có tiếng và không tiếng trên điện thoại | Hệ thống 6 bước, bước 6; Thư viện Prompt v2.1 |
| 3 | **Cửa chống spam trước khi đăng:** video giải quyết 1 vấn đề thật, đúng như quảng cáo, không trùng video hôm qua, có lý do để lưu/chia sẻ | Khung chất lượng §3 |
| 4 | **Đo chất lượng sau khi đăng:** giữ chân giây 3, giây 10, tỉ lệ xem hết — không đo bằng số lượng | Khung chất lượng §4 |
| 5 | **Chọn sản phẩm qua 5 câu hỏi** (vì sao chọn, tại sao bây giờ, căn cứ số liệu, có ra tiền không, rủi ro gì) | Quy tắc chọn sản phẩm 15/11 |
| 6 | **Phương án dự phòng không lộ mặt** (chỉ tay + sản phẩm) nếu mặt diễn viên làm lại vẫn lỗi | Bài học 9 |

## C. Cách bot tách cảnh (mục A, quy tắc 4–5)

- Người gửi 1 lệnh duy nhất, ghi rõ từng cảnh:
  `VIDEO: Cảnh 1: … Cảnh 2: … Cảnh 3: …`
  (hoặc danh sách đánh số `1. … 2. …`, hoặc các đoạn cách nhau `---`).
- Bot tách thành từng job riêng, mỗi job 1 cảnh tối đa 8 giây,
  đánh số cảnh 1, 2, 3… và gửi từng clip về kèm số cảnh.
- **Ziggy ghép lại theo thứ tự bằng FFmpeg**, nối hòa trộn 0,5 giây.
- **Nếu lệnh không tách được rõ ràng** (chỉ 1 cảnh, hoặc nói video dài
  35 giây nhưng không ghi từng cảnh): bot làm đúng 1 clip và báo rõ
  "chỉ làm được 1 cảnh, gửi lại từng cảnh riêng" — không tự bịa thêm
  cảnh, không tự kéo dài clip quá 8 giây.
- **Cảnh cần xem lại trong app (`needs_review`):** bot dừng chuỗi, báo
  "đã xong tới Cảnh N", rồi chờ lệnh `VIDEO: tiếp tục từ Cảnh N+1`
  (hoặc lệnh GitHub kind `continue`) để làm nốt — không làm lại từ đầu,
  không tính vào hạn 1 video/ngày.

## D. Cách kiến thức tới được máy Mỹ (đồng bộ qua GitHub)

Saek chốt 17/11/2026: Ziggy chia sẻ kiến thức với Muse Mỹ LIÊN TỤC
qua một chỗ chung trên GitHub mà bot Mỹ tự đọc định kỳ — bài học mới,
quy tắc prompt mới, dữ liệu sản phẩm mới, kịch bản mới đều tự tới bên
Mỹ trong vài phút, không cần gửi lại tay từng lần.

- **Bot đọc gì, bao lâu 1 lần:** bot cứ 15 phút đọc lại từ GitHub các
  file trong `knowledge_files` của `config.json`: `v19.txt` (mô tả
  diễn viên), `v19-safe.txt` (bản an toàn), `video-rules.json` (quy tắc
  dạng máy đọc được), `kien-thuc-video.md` (bản tiếng Việt gốc, để người
  đọc). File nào đổi thì bot lưu về máy và áp dụng ngay cho lệnh tiếp theo.
  File JSON lỗi thì bot giữ bản cũ, không ghi đè (bản cũ giữ lại `.bak`).
- **Lệnh video cũng qua GitHub:** Ziggy viết lệnh vào `queue.json`
  trên repo chung; bot cứ 5 phút đọc 1 lần, thấy lệnh mới thì làm
  ngay, gửi video về Telegram. Saek không cần nhắn lệnh trên Telegram
  nữa. Xem `commands-queue-example.json` để biết định dạng lệnh.
  **Lệnh bị từ chối (bận / hết 1 video / thiếu ảnh) KHÔNG bị đánh dấu
  xong** — lần đọc sau bot thử lại, không mất lệnh.
- **Ảnh khóa diễn viên:** 5 ảnh khóa nằm trong repo (`refs/`, dạng
  `.b64` vì ảnh nhị phân không đẩy trực tiếp qua connector GitHub
  được — bot tự tải về và giải mã). Ảnh khóa cũng đi kèm gói zip lúc
  cài. Ảnh sản phẩm gửi qua Telegram (bot lưu làm ảnh sản phẩm) hoặc
  chỉ định trong lệnh GitHub.
- **Video về đường Drive:** bot ghi `status.json` + file MP4 vào thư
  mục `videos` (người nhà trỏ thư mục này vào thư mục đồng bộ của
  Google Drive trên máy Mỹ, chia sẻ với email của Saek). Ziggy đọc
  `status.json` + tải clip qua Google Drive để kiểm tra và hậu kỳ.
  Chưa cài Drive thì Telegram vẫn là đường video duy nhất, Saek là
  người chuyển tiếp file — cài Drive là cửa trước video thật đầu tiên.
- **Việc của Ziggy (mỗi khi có bài học mới):** cập nhật cả 2 nơi —
  (1) `kien-thuc-video.md` (bản tiếng Việt cho người đọc) và
  (2) `video-rules.json` (bản tiếng Anh cho máy đọc), rồi đẩy lên
  GitHub. Bot chỉ đọc được quy tắc trong `video-rules.json`; chỉ sửa
  file `.md` thì bot KHÔNG tự áp dụng được.
- **Giới hạn:** đồng bộ chỉ mang CHỮ (mô tả, quy tắc, kịch bản) tới
  máy Mỹ. Ảnh tham chiếu đi qua repo (dạng `.b64`) hoặc Telegram.
