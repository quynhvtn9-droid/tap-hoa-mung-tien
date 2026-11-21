# Quét & Bán – gói cài lên iPhone (PWA)

Ứng dụng web cài lên màn hình chính iPhone: quét mã vạch lưu giá, bán hàng, tạo hóa đơn trên máy. Không cần Mac, Xcode hay tài khoản Apple Developer.

## Trong gói

| File | Vai trò |
|---|---|
| `index.html` | Toàn bộ ứng dụng |
| `vendor/zxing.min.js` | Bộ đọc mã vạch ZXing 0.21.3, chạy cả khi mất mạng |
| `sw.js`, `manifest.webmanifest`, `icons/` | Cài lên màn hình chính, chạy offline |
| `web.config` | Cấu hình sẵn cho IIS |

## Điều kiện bắt buộc

Trang phải chạy trên **HTTPS với chứng chỉ hợp lệ**. iPhone chỉ cho mở camera và cài PWA khi có HTTPS; chứng chỉ tự ký sẽ không chạy.

## Cách 1: đưa lên IIS

1. Chép cả thư mục `quet-ban` lên server.
2. Tạo site hoặc virtual directory trỏ tới thư mục đó.
3. Gắn binding HTTPS với chứng chỉ hợp lệ (chứng chỉ công ty, hoặc Let's Encrypt qua win-acme).
4. `web.config` đã khai báo MIME cho `.webmanifest`, tắt cache cho `sw.js` và `index.html`, cho phép camera.

## Cách 2: không có server

Dùng GitHub Pages hoặc Netlify Drop (kéo thả cả thư mục vào trang). Cả hai đều cấp HTTPS miễn phí.

## Cài lên iPhone

1. Mở địa chỉ trang bằng **Safari**.
2. Chạm nút **Chia sẻ**, chọn **Thêm vào MH chính**, chạm **Thêm**.
3. Mở app từ biểu tượng Quét & Bán. Lần đầu quét, chạm **Cho phép** khi được hỏi quyền camera.

## Dữ liệu

- Lưu ngay trên iPhone. Xóa biểu tượng app khỏi màn hình chính có thể làm mất dữ liệu.
- Sao lưu hằng tuần: **Cài đặt**, **Sao lưu ra file**. Khôi phục bằng file đó trên máy khác.
- Bản chạy trong Claude và bản cài này lưu dữ liệu riêng. Chuyển qua lại bằng Sao lưu và Khôi phục.

## Cập nhật phiên bản

Mỗi lần thay file, đổi `CACHE` trong `sw.js` (ví dụ `quet-ban-v2`) để iPhone tải bản mới. Đóng hẳn app rồi mở lại.
