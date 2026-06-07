# Plan: Cập nhật Privacy Policy cho iOS + Android, độ tuổi 13+

## Bối cảnh
Policy hiện tại ([index.html](../index.html)) đang để **18+** (Section 4) và viết khá chung chung. Cần điều chỉnh để:
1. Hướng tới độ tuổi **13+** (chuẩn COPPA: không nhắm tới trẻ dưới 13).
2. Phù hợp **cả iOS lẫn Android** — ngôn ngữ trung lập về nền tảng, khai báo đầy đủ quyền truy cập, và nêu rõ "không tracking" để hợp yêu cầu App Privacy của Apple và Data Safety của Google Play.

### Sự thật về app (đã xác nhận với chủ dự án)
- **Camera:** quét QR/barcode.
- **Ảnh/Thư viện:** (a) lưu mã QR đã tạo vào gallery, (b) quét QR từ ảnh có sẵn, (c) chia sẻ qua share sheet → app **đọc và ghi** thư viện ảnh.
- **Bên thứ ba:** KHÔNG có analytics / crash reporting / quảng cáo. App offline hoàn toàn, không thu thập dữ liệu.
- **Độ tuổi:** 13+, không nhắm tới trẻ dưới 13.

---

## Tổng quan thay đổi

| # | Khu vực | Việc cần làm |
|---|---|---|
| 1 | Section 1 — Information We Collect | Thêm mục **Photos & Media**; thêm câu khẳng định đa nền tảng + không tracking |
| 2 | Section 2 — How We Use Information | Thêm mục mô tả việc dùng quyền ảnh |
| 3 | Section 3 — Data Storage & Deletion | Thêm lưu ý: ảnh QR đã lưu vào gallery vẫn còn sau khi gỡ app |
| 4 | Section 4 — Children's Privacy | Đổi **18+ → 13+** theo khung COPPA |
| 5 | Last updated | Đổi sang **June 7, 2026 / 7 tháng 6, 2026** |

> Tất cả thay đổi giữ nguyên cấu trúc đánh số section hiện tại (chỉ thêm `<li>`/`<p>`), không phải renumber.

---

## Chi tiết từng thay đổi

### 1. Section 1 — Information We Collect ([index.html:33-61](../index.html#L33-L61))

**1a. Thêm câu khẳng định đa nền tảng + không tracking** — chèn sau đoạn `<p>` "does not collect..." ([index.html:38-41](../index.html#L38-L41)):

```html
<p>
  <span class="en">QRify is available on both iOS and Android, and this policy applies to all versions. The app runs entirely on your device. It does not use analytics, advertising, tracking, or any third-party data-collection services (including Apple's App Tracking Transparency framework).</span>
  <span class="vi">QRify có mặt trên cả iOS và Android, và chính sách này áp dụng cho mọi phiên bản. Ứng dụng chạy hoàn toàn trên thiết bị của bạn. Ứng dụng không sử dụng analytics, quảng cáo, theo dõi (tracking), hay bất kỳ dịch vụ thu thập dữ liệu của bên thứ ba nào (bao gồm cả khung App Tracking Transparency của Apple).</span>
</p>
```

**1b. Thêm mục Photos & Media** vào `<ul>`, sau mục "Scan History" ([index.html:48-52](../index.html#L48-L52)):

```html
<li>
  <strong><span class="en">Photos &amp; Media:</span><span class="vi">Ảnh &amp; Phương tiện:</span></strong>
  <span class="en">Accessed only when you choose to scan a QR/barcode from an existing image, or to save a QR code you generated to your device. Images are processed locally and are never uploaded or shared with us.</span>
  <span class="vi">Chỉ được truy cập khi bạn chọn quét mã QR/barcode từ một ảnh có sẵn, hoặc khi bạn lưu mã QR đã tạo vào thiết bị. Ảnh được xử lý cục bộ, không bao giờ được tải lên hay chia sẻ cho chúng tôi.</span>
</li>
```

> Ghi chú nền tảng (không cần đưa vào HTML, chỉ để dev đối chiếu khi khai báo store):
> - iOS: `NSCameraUsageDescription`, `NSPhotoLibraryUsageDescription` (đọc ảnh để quét), `NSPhotoLibraryAddUsageDescription` (lưu QR). Privacy Nutrition Label = **Data Not Collected**.
> - Android: `CAMERA`; đọc ảnh dùng Photo Picker (Android 13+ không cần quyền) hoặc `READ_MEDIA_IMAGES`; lưu QR qua MediaStore (Android 10+ thường không cần quyền ghi). Play Data safety = **No data collected / No data shared**.

### 2. Section 2 — How We Use Information ([index.html:63-84](../index.html#L63-L84))

Thêm `<li>` vào cuối `<ul>` (sau mục "Local history" ở [index.html:73-76](../index.html#L73-L76)):

```html
<li>
  <span class="en">Photo access is used only to read an image you pick for scanning, or to save a QR code you generated — both happen on your device only.</span>
  <span class="vi">Quyền truy cập ảnh chỉ dùng để đọc ảnh bạn chọn để quét, hoặc lưu mã QR bạn đã tạo — cả hai đều chỉ diễn ra trên thiết bị của bạn.</span>
</li>
```

> ⚠️ Phối hợp với plan trước [docs/privacy-action-handling-plan.md](privacy-action-handling-plan.md): plan đó cũng thêm `<li>` action-handling vào chính `<ul>` này. Nếu làm cả hai, thêm cả hai `<li>` vào cùng list.

### 3. Section 3 — Data Storage & Deletion ([index.html:100-129](../index.html#L100-L129))

Thêm lưu ý sau đoạn "Data deleted includes..." ([index.html:125-128](../index.html#L125-L128)) — vì giờ app ghi ảnh ra gallery, gỡ app KHÔNG xóa các ảnh đó:

```html
<p>
  <span class="en">Note: QR code images you chose to save are stored in your device's photo gallery and remain there after uninstalling QRify. You can delete them anytime from your gallery app.</span>
  <span class="vi">Lưu ý: Các ảnh mã QR mà bạn đã chọn lưu được lưu trong thư viện ảnh của thiết bị và vẫn còn ở đó sau khi gỡ QRify. Bạn có thể xóa chúng bất cứ lúc nào từ ứng dụng thư viện ảnh.</span>
</p>
```

### 4. Section 4 — Children's Privacy ([index.html:131-140](../index.html#L131-L140))

Thay toàn bộ đoạn `<p>` 18+ hiện tại ([index.html:136-139](../index.html#L136-L139)) bằng nội dung 13+:

| | Nội dung mới |
|---|---|
| EN | `QRify is intended for users aged 13 and over and is not directed to children under 13. We do not knowingly collect personal information from anyone under 13 — in fact, QRify collects no personal data from any user, and all information stays on your device. If you believe a child under 13 has used the app and you have concerns, please contact us.` |
| VI | `QRify dành cho người dùng từ 13 tuổi trở lên và không hướng tới trẻ em dưới 13 tuổi. Chúng tôi không cố ý thu thập thông tin cá nhân từ bất kỳ ai dưới 13 tuổi — thực tế, QRify không thu thập dữ liệu cá nhân từ bất kỳ người dùng nào, và mọi thông tin đều nằm trên thiết bị của bạn. Nếu bạn cho rằng có trẻ dưới 13 tuổi đã dùng ứng dụng và bạn có lo ngại, vui lòng liên hệ chúng tôi.` |

### 5. Cập nhật "Last updated" ([index.html:28-31](../index.html#L28-L31))

| | Hiện tại | Sau cập nhật |
|---|---|---|
| EN | `Last updated: May 31, 2026` | `Last updated: June 7, 2026` |
| VI | `Cập nhật lần cuối: 31 tháng 5, 2026` | `Cập nhật lần cuối: 7 tháng 6, 2026` |

---

## Việc ngoài file policy (chủ dự án tự làm trên store)
- **Apple App Store Connect:** App Privacy → khai *Data Not Collected*; Age Rating đặt 12+/13+; không bật ATT.
- **Google Play Console:** Data safety → *No data collected, No data shared*; Content rating (IARC) → 13+; nếu dùng quyền đọc ảnh rộng (`READ_MEDIA_IMAGES`) phải khai mục đích, ưu tiên Photo Picker để khỏi cần khai báo.

## Checklist thực hiện trong index.html
- [ ] (1a) Thêm `<p>` đa nền tảng + không tracking vào Section 1
- [ ] (1b) Thêm `<li>` "Photos & Media" vào Section 1
- [ ] (2) Thêm `<li>` dùng quyền ảnh vào Section 2
- [ ] (3) Thêm `<p>` lưu ý ảnh trong gallery sau gỡ app vào Section 3
- [ ] (4) Đổi Children's Privacy 18+ → 13+
- [ ] (5) Đổi "Last updated" sang June 7, 2026 / 7 tháng 6, 2026
- [ ] Kiểm tra toggle EN/VI hiển thị đúng toàn bộ nội dung mới
- [ ] Commit & push, kiểm tra trên GitHub Pages
