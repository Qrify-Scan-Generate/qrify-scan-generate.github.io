# Plan: Cập nhật Privacy Policy — Action Handling trên kết quả quét

## Bối cảnh
App có thay đổi: khi người dùng bấm một hành động trên kết quả quét (mở link, gọi, gửi SMS/email, mở bản đồ, mở Cài đặt Wi-Fi), QRify chuyển nội dung đó sang app tương ứng trên thiết bị. Hành động bản đồ mở Google Maps. Việc này chỉ xảy ra khi người dùng chủ động bấm và không có dữ liệu nào gửi lên máy chủ.

Cần phản ánh điều này trong [index.html](../index.html) để chính sách đầy đủ và chính xác.

## Mục tiêu
1. Thêm nội dung mô tả việc bàn giao nội dung cho app bên ngoài khi người dùng bấm action.
2. Cập nhật ngày "Last updated" / "Cập nhật lần cuối".

## Thay đổi cụ thể

### 1. Thêm dòng mô tả action handling
**Vị trí đề xuất:** Section 2 — "How We Use Information" ([index.html:63-84](../index.html#L63-L84)), thêm `<li>` mới vào cuối `<ul>` (sau mục "Local history").

Lý do chọn Section 2: nội dung nói về *cách app dùng/xử lý dữ liệu khi người dùng tương tác*, hợp ngữ cảnh hơn Section 1 (liệt kê dữ liệu thu thập) hay Section 3 (lưu trữ & xóa).

**Nội dung thêm:**

```html
<li>
  <span class="en">When you tap an action on a scan result (e.g. open a link, call, send SMS/email, open a map, or open Wi-Fi settings), QRify hands that content to the relevant app on your device. Map actions open Google Maps. This happens only on your action and nothing is sent to our servers.</span>
  <span class="vi">Khi bạn bấm một hành động trên kết quả quét (mở liên kết, gọi, gửi SMS/email, mở bản đồ, hoặc mở Cài đặt Wi-Fi), QRify chuyển nội dung đó sang app tương ứng trên thiết bị. Hành động bản đồ sẽ mở Google Maps. Việc này chỉ xảy ra khi bạn chủ động bấm và không có dữ liệu nào được gửi lên máy chủ của chúng tôi.</span>
</li>
```

### 2. Cập nhật "Last updated"
**Vị trí:** [index.html:28-31](../index.html#L28-L31)

| | Hiện tại | Sau cập nhật |
|---|---|---|
| EN | `Last updated: May 31, 2026` | `Last updated: June 6, 2026` |
| VI | `Cập nhật lần cuối: 31 tháng 5, 2026` | `Cập nhật lần cuối: 6 tháng 6, 2026` |

## Cân nhắc (tùy chọn, không bắt buộc)
- Cache busting: file dùng `style.css?v=3` ([index.html:12](../index.html#L12)). Thay đổi lần này chỉ sửa nội dung HTML (không sửa CSS) nên không bắt buộc tăng version. Nếu GitHub Pages cache HTML gây hiển thị cũ, có thể cân nhắc nhưng thường HTML tự refresh.
- Nếu muốn nhất quán đánh số, action handling cũng có thể tách thành section riêng — nhưng thêm `<li>` vào Section 2 là cách gọn nhất, không phải đánh số lại các section sau.

## Checklist thực hiện
- [ ] Thêm `<li>` action handling vào cuối `<ul>` của Section 2
- [ ] Đổi ngày EN sang `June 6, 2026`
- [ ] Đổi ngày VI sang `6 tháng 6, 2026`
- [ ] Kiểm tra hiển thị cả 2 ngôn ngữ (toggle EN/VI) hoạt động đúng với nội dung mới
- [ ] Commit & push
