# Bảng tin trong app (announcements.json)

App WorkPilot AI đọc `announcements.json` ở nhánh `main` của repo này để hiện **bảng tin** trong app cho **mọi người dùng** (không cần server). Sửa file này → mọi máy thấy khi mở app lần sau.

## Cách đăng một thông báo
Thêm một phần tử vào mảng `announcements`:

```json
{
  "id": "maintenance-2026-08-01",
  "title": "Bảo trì đồng bộ 01/08",
  "body": "Máy chủ đồng bộ tạm nghỉ 22:00–23:00. Dữ liệu vẫn lưu cục bộ bình thường.",
  "level": "warning",
  "url": "https://github.com/mittohoa/workpilot-app/releases"
}
```

| Trường | Bắt buộc | Ý nghĩa |
|---|---|---|
| `id` | ✅ | Mã DUY NHẤT. App nhớ id đã đọc → không hiện lại. **Đừng tái dùng id cũ.** |
| `title` | ✅ | Tiêu đề |
| `body` | | Nội dung |
| `level` | | `info` (xám) · `warning` (đỏ) · `update` (xanh). Mặc định `info`. |
| `url` | | Có → hiện nút "Xem" mở link |

## Lưu ý
- App hiện **lần lượt từng mục chưa đọc** (mục đầu mảng trước). Người dùng bấm "Đã hiểu" để qua mục kế.
- Muốn gỡ thông báo cho người **chưa** đọc: xoá phần tử khỏi mảng. Người đã đọc thì vốn không thấy nữa.
- Đây KHÔNG phải push nền — chỉ hiện khi user mở app (fetch lúc khởi động).
- Thông báo "có bản mới" là **tự động** (app tự so version với GitHub Releases), không cần đăng ở đây.
