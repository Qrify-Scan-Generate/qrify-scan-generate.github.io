# Plan: Cập nhật Privacy Policy cho Google AdMob

## Bối cảnh
App đã tích hợp Google AdMob để hiển thị quảng cáo (`app-ads.txt` đã thêm ở commit `430e3fb`). Policy hiện tại ([../privacy/index.html](../privacy/index.html)) vẫn khẳng định không dùng advertising/tracking và Children's Privacy nói "collects no personal data from any user" — không còn đúng vì AdMob SDK thu thập Advertising ID và dữ liệu thiết bị. Landing page ([../index.html](../index.html)) cũng đang quảng bá "no ads".

### Sự thật về app (đã xác nhận với chủ dự án)
- **Ad network:** chỉ Google AdMob trực tiếp, không dùng mediation network khác.
- **Phạm vi phát hành:** toàn cầu, bao gồm EU/UK/EEA → cần disclosure GDPR/consent.
- **Độ tuổi:** vẫn 13+, không nhắm tới trẻ dưới 13 — ads không được cá nhân hóa cho nhóm này.

---

## Tổng quan thay đổi

| # | Khu vực | Việc cần làm |
|---|---|---|
| 1 | Last updated | Đổi sang June 24, 2026 / 24 tháng 6, 2026 |
| 2 | Section 1 — Information We Collect | Sửa câu khẳng định "không advertising/tracking"; mở comment + viết lại mục Advertising ID/Device Data |
| 3 | Section 2 — How We Use Information | Mở comment + viết lại mục dùng Advertising ID cho ads |
| 4 | Section mới "3. Advertising" | Mở comment cũ, viết lại đầy đủ: link Google Privacy Policy + Ad Technology Providers, đoạn GDPR/UMP cho EEA/UK/Thụy Sĩ, câu nối tới Children's Privacy |
| 5 | Renumber section | Data Storage 3→4, Children's Privacy 4→5, Changes 5→6, Version History 6→7, Contact 7→8 (giữ nguyên `id` anchor) |
| 6 | Children's Privacy | Thêm vế ngoại trừ Advertising ID khi nói "collects no personal data" |
| 7 | Version History | Thêm 1 `<li>` ghi nhận lần cập nhật này |
| 8 | Landing page (`../index.html`) | Bỏ claim "no ads" / "không quảng cáo" trong tagline feature "Private by Design" |

---

## Việc ngoài file policy (chủ dự án tự làm trên store)
- **Google Play Console:** Data safety → khai "Advertising or marketing" data type, Advertising ID.
- **Apple App Store Connect:** App Privacy → khai Advertising Identifier; xem xét App Tracking Transparency nếu dùng personalized ads trên iOS.
- Đảm bảo app thật đã tích hợp Google UMP SDK để khớp với đoạn GDPR trong policy.

## Checklist thực hiện
- [x] (1) Đổi "Last updated"
- [x] (2) Sửa Section 1 + mở comment Advertising ID/Device Data
- [x] (3) Mở comment mục dùng Advertising ID ở Section 2
- [x] (4) Thêm section "3. Advertising" đầy đủ (Google links + GDPR/UMP)
- [x] (5) Renumber các section còn lại
- [x] (6) Sửa Children's Privacy
- [x] (7) Thêm entry Version History
- [x] (8) Sửa tagline landing page
- [ ] Kiểm tra toggle EN/VI hiển thị đúng toàn bộ nội dung mới
- [ ] Commit & push, kiểm tra trên GitHub Pages
