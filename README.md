# muse-vn-us-bridge — Chỗ chung của Muse VN và Muse Mỹ

Repo này là **chỗ chung** để Ziggy (Muse ở Việt Nam) ra lệnh làm video
và chia sẻ kiến thức làm video cho bot chạy trên máy Mỹ — bot tự đọc
định kỳ, không cần ai nhắn tay từng lần.

## Có gì trong repo

| File | Để làm gì |
|---|---|
| `queue.json` | File lệnh video. Ziggy viết lệnh vào đây; bot Mỹ đọc mỗi 5 phút, thấy lệnh mới thì làm ngay. Hiện đang trống (bản nháp YUJIAO Ngày 1 chưa được duyệt). |
| `commands-queue-example.json` | Mẫu lệnh (kịch bản YUJIAO Ngày 1, 5 cảnh) + ví dụ làm lại cảnh (`retake`) và tiếp tục chuỗi dở (`continue`). |
| `v19.txt` | Mô tả diễn viên v19 (khóa) — bot kèm vào mọi lệnh video. |
| `v19-safe.txt` | Bản v19 an toàn (bỏ cụm nhạy cảm) — bot thử khi model từ chối vì nội dung. |
| `video-rules.json` | Quy tắc làm video dạng máy đọc — bot kèm vào mọi lệnh video. |
| `kien-thuc-video.md` | Kiến thức làm video bản tiếng Việt (gốc của `video-rules.json`). |
| `lenh-runbook.md` | Sổ tay viết lệnh cho Ziggy (cách viết lệnh, múi giờ, theo dõi). |
| `refs/` | 5 ảnh khóa của diễn viên v19 (dạng `.b64` — ảnh nhị phân không đẩy trực tiếp qua connector GitHub được, bot tự tải về và giải mã). |

## Cách vận hành (tóm tắt)

1. Ziggy viết lệnh vào `queue.json`, đẩy lên repo.
2. Bot trên máy Mỹ đọc `queue.json` mỗi 5 phút, làm video bằng muse4ai,
   gửi clip về nhóm Telegram chung (Saek + người nhà + bot).
3. Bot đọc lại `v19.txt` / `video-rules.json` / `kien-thuc-video.md`
   mỗi 15 phút — bài học mới tự tới bên Mỹ.
4. Clip + `status.json` nằm trong thư mục `videos` trên máy Mỹ (nối
   Google Drive chung) để Ziggy tải về kiểm tra và hậu kỳ.

Chi tiết đầy đủ trong `README.md` của gói bot
(`telegram-muse-us-bridge` trên máy Ziggy).

## Bảo mật

- Repo công khai, chỉ chứa mô tả cảnh chung chung + kiến thức làm video.
- Không có token, key, mật khẩu, cookie trong repo.
- Chỉ Saek là cộng tác viên có quyền ghi.
