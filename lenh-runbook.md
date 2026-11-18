# Runbook viết lệnh video — cho Ziggy (Muse VN)

File này là sổ tay của NGƯỜI VIẾT LỆNH (Ziggy), không phải hướng dẫn
cho người nhà ở Mỹ. Đọc trước mỗi lần viết lệnh vào `queue.json`.

## 1. Viết lệnh kiểu ghi-tạm-rồi-đổi-tên (atomic write)

Khi sửa `queue.json` trên máy của Ziggy: ghi ra file tạm
`queue.json.tmp`, xong mới đổi tên thành `queue.json` rồi đẩy lên
GitHub. Không bao giờ ghi đè trực tiếp file đang được bot đọc — bot
đọc đúng lúc đang ghi dở sẽ thấy file lỗi và bỏ qua lần đọc đó
(lần sau đọc lại thì được, nhưng tránh vẫn hơn).

## 2. Một ngày tối đa 1 video mới

- Trong `queue.json` không bao giờ xếp hơn 1 lệnh video mới/ngày
  (tính theo giờ Mỹ — xem mục 6).
- Làm lại cảnh lỗi (`kind: "retake"`) và tiếp tục chuỗi dở
  (`kind: "continue"`) thì được, không tính vào hạn 1 video/ngày.
- Mỗi lệnh có `id` duy nhất, không dùng lại id cũ. Muốn làm lại lệnh
  cũ thì tạo id mới.

## 3. Định dạng lệnh (xem commands-queue-example.json)

```json
{"id": "yujiao-ngay1-2026-11-17", "kind": "video",
 "actor_ref": "v19-vay-trang.jpg",
 "product_ref": "yujiao-sponge.jpg",
 "prompt": "Cảnh 1: ... Cảnh 2: ... Cảnh 3: ..."}
```

- `kind`: `video` (mới), `retake` (làm lại 1 cảnh — thêm `original_id`
  + `scene` + `prompt` mô tả mới của cảnh đó), `continue` (làm tiếp —
  thêm `original_id` + `from_scene` + `prompt` đầy đủ).
- `prompt`: ghi rõ từng cảnh `Cảnh 1: ... Cảnh 2: ...`, mỗi cảnh 1
  hành động, tối đa 8 giây. **Lời thoại tiếng Việt nằm ngay trong
  từng cảnh** (model tự nói lời đó trong clip — quyết định v3, chưa
  kiểm chứng giọng tiếng Việt của model).
- `actor_ref`: tên file trong 5 ảnh khóa (`refs/`). Mặc định bot dùng
  `v19-vay-trang.jpg` nếu không ghi.
- `product_ref`: ảnh thật sản phẩm. Ảnh phải có trong repo `refs/`
  (dạng `.b64`) hoặc đã gửi qua Telegram trước.
- **Lệnh chỉ chứa mô tả cảnh.** Không ghi lệnh hệ thống, không ghi
  số đo v19 trong `queue.json` (v19 nằm trong `v19.txt` rồi).

## 4. Ảnh sản phẩm mới

Ảnh nhị phân không đẩy trực tiếp qua connector GitHub được — chuyển
sang base64 trước rồi đẩy file `.b64` lên `refs/`:

```bash
base64 -w0 anh-san-pham.jpg > refs/anh-san-pham.jpg.b64
```

Bot tự tải `.b64` về và giải mã. Ảnh diễn viên khóa cũng vậy (5 file
`.b64` đã có sẵn trong repo).

## 5. Ra lệnh sớm hơn giờ muốn có video ít nhất 15 phút

Bot đọc GitHub mỗi 5 phút + thời gian làm job (mỗi cảnh tới 12 phút).
Muốn có video lúc 9h sáng (giờ VN) thì viết lệnh trước 8h45.

## 6. Múi giờ

- "Ngày video" tính theo giờ địa phương của máy Mỹ (giờ trong
  `us_timezone` ở `config.json` — người nhà điền, ví dụ
  `America/Los_Angeles`).
- 9h sáng ở Việt Nam = khoảng 19h tối hôm trước ở Mỹ (tùy bang, lệch
  11–12 tiếng). Lệnh viết buổi sáng VN thì máy Mỹ làm vào tối hôm
  trước — video về trong đêm, sáng VN đã có để xem.

## 7. Theo dõi và sửa

- Bot ghi `status.json` vào thư mục `videos` (trong thư mục Drive
  chung). Ziggy đọc file này qua Google Drive: bot sống/chết, lệnh
  đang làm, lệnh xong, lỗi gần nhất, số clip hôm nay, job trong tuần.
- Lệnh nào hỏng cảnh nào: gửi `retake` cho đúng cảnh đó, không làm
  lại cả video.
- Video nào đã đăng thì ghi tên file vào `keep.json` trên máy Mỹ
  (để bot không xóa khi dọn video cũ quá 30 ngày).

## 8. Bảo mật repo

- Repo công khai, chỉ chứa mô tả cảnh chung chung + kiến thức làm
  video. Không có token, key, mật khẩu, cookie trong repo.
- Chỉ Saek là cộng tác viên có quyền ghi. Không mở quyền ghi công khai.
