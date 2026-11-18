# Lịch video — kênh Gia dụng / Nhà cửa

File này để cả 2 bên cùng đọc: Ziggy (VN) viết lệnh theo lịch này vào
`queue.json`; bot Mỹ đọc lệnh và làm video. 1 video/ngày, lệnh phải có
trước giờ muốn có video ít nhất 15 phút.

Ngày video tính theo giờ Mỹ (xem `lenh-runbook.md`). Ngày lịch dưới đây
tính theo ngày đăng thực tế: Ngày 1 đăng ngày nào thì các ngày sau dời
theo ngày đó.

## Đã duyệt (kế hoạch 7 ngày, Saek duyệt 15/11/2026)

| Ngày | Sản phẩm | Cảnh | Trạng thái |
|------|----------|------|------------|
| Ngày 1 | Miếng tẩy cặn canxi YUJIAO | 5 cảnh (1, 2a, 2b, 3, 4) — xem `commands-queue-example.json` | CHỜ SAEK DUYỆT BẢN NHÁP. Cửa sổ đăng 16–19/11/2026 |
| Ngày 2 | Nước giặt Tidy Home Daily Essentials | chưa viết kịch bản | Chờ Ngày 1 xong |
| Ngày 3 | Khăn giấy Pio TOPGIA thùng 5 bịch | chưa viết kịch bản | Chờ Ngày 2 xong |
| Ngày 4 | Mise Giấy treo tường | chưa viết kịch bản | Chờ Ngày 3 xong |
| Ngày 5 | Giấy treo gấu Caipiao 10 bịch (so sánh TOPGIA) | chưa viết kịch bản | Chờ Ngày 4 xong |
| Ngày 6 | Tổng hợp top 3 sản phẩm | chưa viết kịch bản | Chờ Ngày 5 xong |
| Ngày 7 | Báo cáo video nhiều click nhất, chọn sản phẩm thắng | chưa viết kịch bản | Chờ Ngày 6 xong |

## Quy tắc

- Chỉ 1 video trong `queue.json` mỗi ngày. Làm lại cảnh lỗi thì được
  (dạng `kind: "retake"`, không tính vào hạn 1 video/ngày).
- Không viết lệnh Ngày N+1 khi Ngày N chưa xong và chưa có kết quả.
- Kịch bản mỗi ngày viết sau khi có kết quả ngày trước (video nào giữ
  người xem lâu thì ngày sau làm theo kiểu đó).
- Hạn mức tuần: 1 video 4 cảnh tốn 8–12% (2–3%/clip, số cộng đồng chưa
  kiểm chứng). 7 ngày là 56–84% — làm lại nhiều có thể chạm giới hạn
  giữa tuần, khi đó dời ngày lại thay vì đốt tiếp hạn mức.
