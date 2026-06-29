# 📊 Dự Án Web App Tính Công Cá Nhân (Futuristic Neon Glassmorphism 3D)

Ứng dụng web chạy trên nền tảng Serverless thuần túy (Client-side), hỗ trợ quản lý ngày công, tính toán giờ làm việc, tự động làm tròn tăng ca và khấu trừ bảo hiểm xã hội để xuất ra tổng lương thực nhận theo thời gian thực. Toàn bộ dữ liệu được đồng bộ hóa bảo mật tuyệt đối qua Google Drive API cá nhân.

---

## 🎯 Tất Cả Các Chức Năng Đã Triển Khai (Features)

### 1. Quản Lý Chấm Công & Tính Lương Thời Gian Thực
* **Chấm công linh hoạt:** Tích chọn Ca Sáng (4 giờ / 0.5 công) và Ca Chiều (4 giờ / 0.5 công).
* **Cụm 3 ô tăng ca độc lập:** Hỗ trợ nhập số phút tăng ca cho cả 3 ca: Tăng ca sáng, Tăng ca trưa, và Tăng ca tối.
* **Cấu hình lương cơ bản:** Cho phép nhập số tiền lương mong muốn (mặc định ban đầu `6.000.000 VNĐ`), tự động định dạng phân tách dấu chấm (`.`) thông minh.

### 2. Logic Tính Toán & Ép Thuật Toán Tự Động (Core Logic)
* **Thuật toán làm tròn xuống Trọng Lực (Overtime Round-Down):** Thời gian tăng ca của người dùng nhập vào các textbox sẽ tự động được làm tròn xuống theo block **mỗi 30 phút**. (Ví dụ: Nhập 135 phút tự quy về 120 phút tương ứng 2 giờ; nhập 45 phút tự quy về 30 phút).
* **Hệ số ngày nghỉ & Ngày Lễ (x2):** Tự động phát hiện ngày Chủ Nhật hoặc các ngày Đại Lễ Việt Nam (`01-01`, `30-04`, `01-05`, `02-09`) để **nhân đôi ($x2$)** toàn bộ tổng số giờ làm việc quy đổi trong ngày đó.
* **Hệ thống Khấu trừ Bảo hiểm (BHXH):** Textbox thông minh tích hợp bộ lọc (chỉ cho phép nhập số, chặn toàn bộ ký tự chữ cái). Hệ thống sẽ lấy số tiền tại dòng **"Tổng Lương"** trừ đi số tiền **"Khấu trừ BHXH"** để xuất ra kết quả cuối cùng tại dòng **"Tổng Lương Dự Kiến"** (Số tiền thực nhận cuối tháng).

### 3. Điều Hướng & Trải Nghiệm Người Dùng (UX)
* **Bộ lọc chuyển tháng (Month Navigation):** Hệ thống nút bấm chứa icon SVG mảnh cho phép lùi/tiến qua lại giữa các tháng để xem lại lịch sử số công cũ mà không bị xóa data khi qua tháng mới.
* **Nút Nhảy Nhanh (📍 Hiện tại):** Click một phát hệ thống tự động định vị lại tháng/năm hiện tại của thiết bị, vẽ lại lịch và kích hoạt chọn sẵn ô ngày hôm nay trên giao diện.
* **Trang Giới Thiệu Độc Lập (`about.html`):** Hiển thị thông tin bản quyền của chủ sở hữu (**Jung Minh Tiền**), tích hợp hệ thống thẻ liên kết Social Media chuyển màu và tự bung tab mới khi click (Facebook, Tiktok, Github).

### 4. Thiết Kế Futuristic Neon Glassmorphism 3D & Hiệu Ứng Vật Lý
* **Visual đỉnh cao:** Sử dụng cơ chế thấu kính mờ `backdrop-blur-[30px]` hấp thụ màu sắc kết hợp với các bong bóng thủy tinh dập nổi 3D (`shadow-[inset_...]`) chuyển động bồng bềnh ngầm phía sau màn hình.
* **Đồng bộ hiệu ứng chữ số Neon:** Cả 2 dòng tiền tệ lớn (Tổng lương và Tổng lương dự kiến) đều được thắp sáng bằng dải màu Gradient phát sáng hào quang rực rỡ.
* **Hiệu ứng Trọng lực Hút nam châm (Magnet Gravity Hover):** Khi rê chuột trên PC, hai nút bấm Đẩy/Kéo data sẽ tự động bị "hút" và dịch chuyển tịnh tiến lệch khối theo tọa độ của con trỏ chuột thời gian thực, tạo cảm giác phản hồi cơ học cực kỳ đã tay.

---

## 🛠️ Công Thức Toán Học Tính Toán Toàn Cục

* **Tổng giờ làm việc trong ngày ($H$):**
$$H = (\text{Ca Sáng} \times 4) + (\text{Ca Chiều} \times 4) + \frac{\text{Tăng ca sáng} + \text{Tăng ca trưa} + \text{Tăng ca tối}}{60}$$
*(Nếu gặp ngày Chủ Nhật hoặc Ngày Lễ: $H = H \times 2$)*

* **Số công trong ngày:** $\text{Công} = \frac{H}{8}$
* **Tổng Lương Tháng (Dựa trên 26 ngày công chuẩn):**
$$\text{Tổng Lương} = \frac{\text{Lương Cơ Bản}}{26} \times \text{Tổng Số Công Tích Lũy Trong Tháng}$$
* **Tổng Lương Dự Kiến Thực Nhận:**
$$\text{Thực Nhận} = \text{Tổng Lương} - \text{Khấu Trừ BHXH}$$

---

## 🚀 Hướng Dẫn Cài Đặt & Triển Khai (Setup & Deployment)

Vì dự án chạy theo kiến trúc **Serverless** thuần túy, m không cần phải cài đặt môi trường server hay node_modules gì phức tạp cả.

### 1. Chạy dưới máy Cục bộ (Local Development)
1. Tải folder project về máy PC.
2. Click đúp chuột vào file `index.html` là ứng dụng tự chạy trực tiếp trên các trình duyệt hiện đại (Brave, Chrome, Edge, Safari).

### 2. Cấu hình định danh Cloud Sync (Google Drive API)
Để hệ thống nút Đẩy/Kéo data hoạt động được với tài khoản Google của m:
1. Mở file `index.html`, tìm đến dòng biến `const CLIENT_ID = '...';` ở đầu thẻ `<script>`.
2. Thay thế chuỗi ID bằng mã Client ID tạo từ [Google Cloud Console](https://console.cloud.google.com/) thuộc tài khoản của m là xong.

### 3. Deploy lên Mạng thông qua GitHub Pages
Mở Terminal tại thư mục dự án và chạy combo 3 lệnh Git thần thánh để đưa app lên chạy online:
```bash
git add .
git commit -m "Update full documentation in README.md"
git push origin main