# Privacy Policy Page — QRify

## Mục tiêu

Tạo một trang Privacy Policy tĩnh, đa ngôn ngữ (EN / VI), host trên GitHub Pages.  
Không cần backend, không cần framework — chỉ HTML + CSS + JS thuần.

---

## Thông tin dự án

| Mục | Giá trị |
|---|---|
| App name | QRify - Scan & Generate |
| Bundle ID | com.yangwave.nvd.qrif |
| Contact email | duongtrieu270799@gmail.com |
| GitHub username | trieunvd |
| Target URL | `https://tqrify-scan-generate.github.io/privacy` (hoặc custom domain sau) |

---

## Cấu trúc file cần tạo

```
/
├── index.html        # Trang chính — EN mặc định, có nút chuyển sang VI
├── style.css         # Style tối giản, responsive, hỗ trợ dark mode
├── CNAME             # Để trống — điền sau nếu dùng custom domain
└── README.md         # Ghi chú deploy
```

> Không dùng thư mục con `/vi/` — toàn bộ nội dung nằm trong `index.html`, chuyển ngôn ngữ bằng JS để URL duy nhất, Play Store chỉ cần 1 link.

---

## Yêu cầu kỹ thuật

### index.html

- Ngôn ngữ mặc định: **English**
- Nút chuyển ngôn ngữ EN | VI ở góc trên phải
- Khi nhấn nút, JS toggle class `lang-vi` / `lang-en` trên `<body>`
- Mỗi đoạn nội dung có 2 thẻ song song:
  ```html
  <span class="en">English text</span>
  <span class="vi">Nội dung tiếng Việt</span>
  ```
- CSS ẩn `.vi` khi body không có class `lang-vi`, ẩn `.en` khi có class `lang-vi`
- Lưu lựa chọn ngôn ngữ vào `localStorage` để giữ khi reload
- `<html lang>` attribute cập nhật theo ngôn ngữ đang chọn

### style.css

- Font: system-ui (không cần Google Fonts, tránh request ngoài)
- Max-width: 720px, căn giữa, padding hợp lý cho mobile
- Màu: CSS variables để hỗ trợ `prefers-color-scheme: dark`
- Không dùng framework CSS (Bootstrap, Tailwind, v.v.)
- Các element cần style: `h1`, `h2`, `p`, `a`, nút chuyển ngôn ngữ, footer

### Không cần

- Analytics (Google Analytics, v.v.)
- Cookie banner
- External fonts
- JavaScript framework

---

## Nội dung Privacy Policy

### Phần tiếng Anh

**Title:** Privacy Policy — QRify - Scan & Generate  
**Last updated:** May 31, 2026

**Section 1 — Information We Collect**  
QRify does not collect or transmit any personal data to external servers.

- **Camera:** Used solely to scan QR codes and barcodes. No images are captured, saved, or sent anywhere.
- **Scan History:** Stored locally on your device only (SQLite database). Never uploaded to any server.
- **Advertising ID:** Google AdMob may collect your device Advertising ID to serve relevant ads. This is managed entirely by Google.

**Section 2 — How We Use Information**

- Camera data is processed in real-time for scanning only and discarded immediately after.
- Local history is used to display your past scans within the app.
- Advertising ID is used by Google AdMob per their own privacy policy.

**Section 3 — Third-Party Services**  
We use Google AdMob for in-app advertising. Google may collect and use data as described in their Privacy Policy: https://policies.google.com/privacy

**Section 4 — Data Storage**  
All app data is stored locally on your device. You can remove all data by uninstalling the app. We have no access to your data.

**Section 5 — Children's Privacy**  
QRify does not knowingly collect personal information from children under the age of 13.

**Section 6 — Changes to This Policy**  
We may update this Privacy Policy from time to time. Changes will be reflected on this page with an updated date.

**Section 7 — Contact**  
If you have questions about this policy, contact us at: duongtrieu270799@gmail.com

---

### Phần tiếng Việt

**Tiêu đề:** Chính Sách Quyền Riêng Tư — QRify - Scan & Generate  
**Cập nhật lần cuối:** 31 tháng 5, 2026

**Mục 1 — Thông Tin Chúng Tôi Thu Thập**  
QRify không thu thập hay truyền bất kỳ dữ liệu cá nhân nào lên máy chủ bên ngoài.

- **Camera:** Chỉ dùng để quét mã QR và barcode. Không chụp, không lưu, không gửi ảnh đi bất kỳ đâu.
- **Lịch sử quét:** Chỉ lưu cục bộ trên thiết bị của bạn (cơ sở dữ liệu SQLite). Không bao giờ được tải lên máy chủ.
- **Advertising ID:** Google AdMob có thể thu thập Advertising ID của thiết bị để hiển thị quảng cáo phù hợp. Việc này do Google quản lý hoàn toàn.

**Mục 2 — Cách Chúng Tôi Sử Dụng Thông Tin**

- Dữ liệu camera chỉ được xử lý thời gian thực để quét và bị xóa ngay sau đó.
- Lịch sử cục bộ được dùng để hiển thị các lần quét trước đây trong ứng dụng.
- Advertising ID được Google AdMob sử dụng theo chính sách riêng của họ.

**Mục 3 — Dịch Vụ Bên Thứ Ba**  
Chúng tôi dùng Google AdMob cho quảng cáo trong ứng dụng. Google có thể thu thập và sử dụng dữ liệu theo Chính Sách Quyền Riêng Tư của họ: https://policies.google.com/privacy

**Mục 4 — Lưu Trữ Dữ Liệu**  
Toàn bộ dữ liệu ứng dụng được lưu cục bộ trên thiết bị của bạn. Bạn có thể xóa toàn bộ dữ liệu bằng cách gỡ cài đặt ứng dụng. Chúng tôi không có quyền truy cập vào dữ liệu của bạn.

**Mục 5 — Quyền Riêng Tư Trẻ Em**  
QRify không cố ý thu thập thông tin cá nhân từ trẻ em dưới 13 tuổi.

**Mục 6 — Thay Đổi Chính Sách**  
Chúng tôi có thể cập nhật Chính Sách Quyền Riêng Tư này theo thời gian. Thay đổi sẽ được phản ánh trên trang này cùng ngày cập nhật mới.

**Mục 7 — Liên Hệ**  
Nếu bạn có thắc mắc về chính sách này, hãy liên hệ chúng tôi tại: duongtrieu270799@gmail.com

---

## Các bước Claude Code cần thực hiện

- [ ] Tạo `index.html` với đầy đủ nội dung EN + VI, nút chuyển ngôn ngữ, và logic localStorage
- [ ] Tạo `style.css` với design tối giản, responsive, hỗ trợ dark mode
- [ ] Tạo `CNAME` rỗng (placeholder cho custom domain sau này)
- [ ] Tạo `README.md` với hướng dẫn bật GitHub Pages

---

## Hướng dẫn bật GitHub Pages (thực hiện thủ công sau khi push code)

1. Vào repo trên GitHub → **Settings**
2. Sidebar trái → **Pages**
3. Source: **Deploy from a branch**
4. Branch: **main** / **(root)**
5. Nhấn **Save**
6. Đợi ~1 phút → URL xuất hiện: `https://trieunvd.github.io/<tên-repo>/`

> Nếu đặt tên repo là `privacy` thì URL là `https://trieunvd.github.io/privacy/`  
> Nếu đặt tên repo là `trieunvd.github.io` (repo đặc biệt) thì URL là `https://trieunvd.github.io/`

---

## Tùy chọn custom domain (làm sau)

Nếu muốn URL dạng `https://yangwave.com/privacy`:

1. Mua domain `yangwave.com` trên Cloudflare Registrar (~$12/năm)
2. Thêm DNS record CNAME: `www → trieunvd.github.io`
3. Điền `yangwave.com` vào file `CNAME`
4. Trong GitHub Pages settings → nhập custom domain → bật **Enforce HTTPS**
