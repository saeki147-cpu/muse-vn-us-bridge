# muse-vn-us-bridge — Chỗ chung của Muse VN và Muse Mỹ

Repo này là **chỗ chung** để Ziggy (Muse ở Việt Nam) ra lệnh làm video
và chia sẻ kiến thức làm video cho Muse US (nhân viên video ở xa, dùng
muse.ai như Ziggy, chỉ khác là tạo video không bị chặn). Không bot,
không muse4ai, không cài gì lên máy Mỹ. Cả 2 Muse đều đọc/ghi repo
trực tiếp qua connector GitHub.

## Có gì trong repo

| File | Để làm gì |
|---|---|
| `queue.json` | File lệnh video. Ziggy viết lệnh vào đây; Muse US đọc rồi làm. Lệnh hiện tại: làm tiếp 3 clip YUJIAO Ngày 1 (cảnh 2b, 3, 4), US tự ghép thành video thành phẩm. |
| `commands-queue-example.json` | Mẫu lệnh (kịch bản YUJIAO Ngày 1, 5 cảnh) + ví dụ làm lại cảnh (`retake`) và tiếp tục chuỗi dở (`continue`). |
| `v19.txt` | Mô tả diễn viên v19 (khóa) — kèm vào mọi lệnh video. |
| `v19-safe.txt` | Bản v19 an toàn (bỏ cụm nhạy cảm) — thử khi model từ chối vì nội dung. |
| `video-rules.json` | Quy tắc làm video dạng máy đọc — kèm vào mọi lệnh video. |
| `kien-thuc-video.md` | Kiến thức làm video bản tiếng Việt (gốc của `video-rules.json`). |
| `lenh-runbook.md` | Sổ tay viết lệnh cho Ziggy (cách viết lệnh, múi giờ, theo dõi). |
| `refs/` | 8 ảnh tham chiếu (dạng `.b64` — ảnh nhị phân không đẩy trực tiếp qua connector GitHub được, tải về rồi giải mã bằng `base64 -d`): 5 ảnh khóa v19 + ảnh v19 trong nhà tắm + 2 ảnh thật sản phẩm YUJIAO (logo + hình dáng). |
| `he-thong-tu-dong-video-truyen.md` | Hệ thống làm video tự động 6 bước + 5 mẫu truyện (ngách Gia dụng). |
| `thu-vien-prompt-v2.md` | Thư viện Prompt v2.1: 11 lỗi làm video nhìn giả + cách sửa, prompt mẫu, negative list. |
| `khung-chat-luong-video-ai.md` | Khung chất lượng video AI: tối đa 1 video/ngày, cửa kiểm tra từng bước, cửa chống spam, cách đo chất lượng. |
| `ho-so-dien-vien-v19-khoa.md` | Hồ sơ đầy đủ diễn viên v19 (số đo, biểu cảm, tóc, ngực, eo, chân, trang phục, máy/ánh sáng, prompt mẫu, checklist). |
| `yujiao-ngay1-ban-chot-2026-11-18.md` | Gói bản chốt YUJIAO Ngày 1: kiểm chứng 5 câu hỏi chọn sản phẩm, prompt chi tiết, checklist rà soát. |

## Cách vận hành (tóm tắt)

1. Ziggy viết lệnh vào `queue.json`, đẩy lên repo. Mọi thứ US cần (hồ sơ v19, ảnh tham chiếu diễn viên + sản phẩm) đều nằm trong repo — US tự lấy, không cần ai đính kèm ảnh.
2. Người thân mở chat Muse US trên máy Mỹ 1 lần, bảo US đọc link lệnh
   `https://raw.githubusercontent.com/saeki147-cpu/muse-vn-us-bridge/main/queue.json`
   rồi làm theo. **LUẬT BẮT BUỘC: US kiểm tra link lệnh và các file kiến thức
   trong repo mỗi 5 phút, liên tục cho đến khi Saek bảo dừng** (giống như
   Ziggy phải tìm việc liên tục); có lệnh mới hoặc bài học mới thì áp dụng ngay.
3. US làm từng clip (mỗi clip ~10 giây), tự ghép + hậu kỳ (phụ đề, chữ CTA,
   chuẩn hoá tiếng) thành **video thành phẩm**, rồi up video lên thư mục
   Google Drive **"Video Muse"** trong tài khoản Gmail **yuik70pro@gmail.com**
   (nối Drive bằng Gmail này nếu chưa nối) — đây là nơi giao video chính,
   Ziggy tải về từ đó. Telegram chỉ là dự phòng (người thân tải về gửi).
4. Ziggy kiểm tra cuối video thành phẩm rồi giao Saek duyệt. Saek chỉ xem
   video thành phẩm, không duyệt từng clip.
5. Ziggy đẩy bài học mới lên repo, US thấy trong vòng 5 phút sau khi Ziggy
   đẩy (kiểm tra mỗi 5 phút).

## Bảo mật

- Repo công khai, chỉ chứa mô tả cảnh chung chung + kiến thức làm video.
- Không có token, key, mật khẩu, cookie trong repo.
- Chỉ Saek là cộng tác viên có quyền ghi.
- Saek KHÔNG mở tài khoản Muse US từ Việt Nam (mở từ VN sẽ bị chặn
  video). Chỉ người thân ở Mỹ mở.
