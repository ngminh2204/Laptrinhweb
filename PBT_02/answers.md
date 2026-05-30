# Phần A - Kiểm tra đọc hiểu 
## Câu A1
1. type="email" → Ô nhập text, tự động kiểm tra định dạng email hợp lệ (phải có ký tự @ và tên miền) → Dùng cho ô nhập email khi Đăng ký/Đăng nhập.
2. type="password" → Ô nhập ẩn ký tự (ẩn ký tự), không có validation tự động → Dùng cho ô nhập mật khẩu tài khoản.
3. type="number" → Ô nhập chỉ chấp nhận số, có nút tăng/giảm → Dùng để chọn số lượng.
4. type="tel" → Ô nhập text tối ưu bàn phím số trên điện thoại, không tự động kiểm tra định dạng trừ khi kết hợp với thuộc tính pattern (Regex) → Dùng để nhập số điện thoại.
5. type="date" → Ô nhập hiển thị sẵn lịch (Calendar picker) để chọn ngày, tự động chặn nếu ngày chọn không hợp lệ → Dùng để chọn ngày.
6. type="url" → Ô nhập text, tự động kiểm tra định dạng đường dẫn hợp lệ → Dùng trong trang quản trị khi Admin cần chèn link.
7. type="search" → Ô nhập text có tích hợp sẵn nút xóa nhanh (dấu x) ở góc phải khi bắt đầu gõ → Dùng làm thanh tìm kiếm sản phẩm, thương hiệu trên đầu trang web.
8. type="color" → Ô hiển thị một hộp màu, khi nhấn vào sẽ mở bảng chọn màu của hệ điều hành, tự động trả về mã màu HEX hợp lệ → Dùng trong bộ lọc (Filter) sản phẩm.
9. type="range" → Thanh trượt (Slider) để chọn giá trị trong một khoảng, tự động giới hạn giá trị tối thiểu và tối đa → Dùng cho bộ lọc khoảng giá (Price range filter).
10. type="file" → Nút bấm kích hoạt cửa sổ chọn file từ thiết bị, có thể giới hạn định dạng → Dùng khi khách hàng tải ảnh/video sản phẩm 

## Câu A2
- Trường hợp 1: Không submit được → Vì required bắt buộc nhập, nhưng đang để trống
<img width="288" height="277" alt="image" src="https://github.com/user-attachments/assets/fbeca341-d09c-431a-aa32-ff8af114c783" />

- Trường hợp 2: Không submit được → Vì email phải có dạng có @, "abc" sai format
<img width="380" height="288" alt="image" src="https://github.com/user-attachments/assets/70c5ffea-2e54-4887-8f7a-49bda24e53a2" />

- Trường hợp 3: Không submit được → Vì 15 > max (10) → vượt phạm vi
<img width="291" height="285" alt="image" src="https://github.com/user-attachments/assets/ec391d8c-8534-492a-b413-c29295a5d5e5" />

- Trường hợp 4: Không submit được → Pattern yêu cầu đúng 10 chữ số, nhưng "abc123" sai
<img width="318" height="294" alt="image" src="https://github.com/user-attachments/assets/863eecd4-503a-4415-b2af-37caf4cf4209" />

- Trường hợp 5: Không submit được → Vì độ dài < 8 ký tự
<img width="494" height="285" alt="image" src="https://github.com/user-attachments/assets/db359c93-6596-4c8c-9a37-86c3a190386d" />

## Câu A3
1. Tại sao `<label for="email">` quan trọng cho người dùng screen reader?
- Giúp screen reader biết ô input này là gì
- Khi click vào label thì focus vào input
2. Khi nào dùng `<fieldset>` + `<legend>`? Cho ví dụ cụ thể.
- Dùng khi có nhóm nhiều input liên quan
```html
<fieldset>
  <legend>Phương thức thanh toán</legend>
  <input type="radio" name="pay"> Tiền mặt
  <input type="radio" name="pay"> Chuyển khoản
</fieldset>
```
3. aria-label dùng khi nào? 
- Dùng khi không có `<label>` hiển thị
Tại sao KHÔNG nên dùng aria-label khi đã có `<label>`?
- Gây trùng thông tin
- Screen reader có thể đọc 2 lần
- Làm rối trải nghiệm

## Câu A4
1. Thuộc tính loading="lazy" giúp ảnh chỉ tải khi gần xuất hiện trên màn hình, từ đó tăng tốc độ tải trang và tiết kiệm băng thông. Tuy nhiên, không nên dùng cho các ảnh quan trọng ở đầu trang vì cần hiển thị ngay.
2. Trong thẻ `<video>`, nên cung cấp nhiều `<source>` để đảm bảo tương thích với nhiều trình duyệt khác nhau; các định dạng phổ biến gồm MP4, WebM và Ogg
3. Thuộc tính alt dùng để mô tả nội dung ảnh cho screen reader, khi ảnh không tải được và hỗ trợ SEO
- Ảnh sản phẩm iPhone 16: alt="Đây là chiếc iPhone 16 màu đen"
- Ảnh trang trí (decorative): alt="Trang trí phòng bếp"
- Ảnh biểu đồ doanh thu Q1/2026: alt="Biểu đồ doanh thu quý 1 năm 2026"

## Câu A5
Cách 1 — `<img>`
- Dùng khi ảnh chỉ để minh họa, không cần chú thích hiển thị trên trang.
- Ảnh là một phần của nội dung xung quanh, không đứng độc lập.
  Ví dụ thực tế:
- Avatar người dùng trong header hoặc comment → chỉ cần hiển thị ảnh, không cần caption.

Cách 2 — `<figure>` + `<figcaption>`
- Dùng khi ảnh cần có chú thích hiển thị bên dưới để bổ sung thông tin.
- Ảnh và caption là một khối nội dung độc lập, có thể tách ra khỏi văn bản mà vẫn hiểu được.
  Ví dụ thực tế:
- Trang chi tiết sản phẩm → ảnh sản phẩm kèm tên, giá, màu sắc bên dưới.

# Phần C - Phân tích & Suy luận
## Câu C1
1. Lỗi 1: Dòng 2 — Input "Tên" không có `<label for="...">`, vi phạm accessibility
- Sửa:
```html
<label for="name">Tên:</label> <input type="text" id="name" name="name" required />
```

2. Lỗi 2: Dòng 4 — Input email không có `<label>` và thiếu `name`, `id`, `required`
- Sửa:
```html
<label for="email">Email:</label>
<input type="email" id="email" name="email" placeholder="Email của bạn" required />
```

3. Lỗi 3: Dòng 6 — Input password không có `<label>` và thiếu `name`, `id`, `required`, `minlength`
- Sửa:
```html
<label for="password">Mật khẩu:</label>
<input type="password" id="password" name="password" placeholder="Mật khẩu" minlength="8" required />
```

4. Lỗi 4: Dòng 7 — Input confirm password không có `<label>` và thiếu `name`, `id`, `required`
- Sửa:
```html
<label for="confirm-password">Nhập lại mật khẩu:</label>
<input type="password" id="confirm-password" name="confirm-password" placeholder="Nhập lại mật khẩu" minlength="8" required />
```

5. Lỗi 5: Dòng 9 — Input phone dùng `type="text"` thay vì `type="tel"`, thiếu `label`, `name`, `id`, `pattern`
- Sửa:
```html
<label for="phone">Phone:</label>
<input type="tel" id="phone" name="phone" pattern="[0-9]{10}" value="0901234567" />
```

6. Lỗi 6: Dòng 11 — `<select>` thiếu `<label>`, `name`, `id` và thiếu option mặc định placeholder
- Sửa:
```html
<label for="city">Thành phố:</label>
<select id="city" name="city">
  <option value="">-- Chọn thành phố --</option>
  <option value="hanoi">Hà Nội</option>
  <option value="hcm">TP.HCM</option>
</select>
```

7. Lỗi 7: Dòng 16 — `<label>` không gắn với checkbox nào, thiếu `<input type="checkbox">`
- Sửa:
```html
<input type="checkbox" id="terms" name="terms" required />
<label for="terms">Tôi đồng ý điều khoản</label>
```

8. Lỗi 8: Dòng 20 — `<form>` thiếu `action` và `method`
- Sửa:
```html
<form action="#" method="POST"></form>
```

## Câu C2
1. Regex pattern
- CMND/CCCD đúng 12 chữ số: `pattern="[0-9]{12}"`
- Số tài khoản 10-15 chữ số: `pattern="[0-9]{10,15}"`

2. HTML5 validation có đủ an toàn không?
- Chưa đủ, hoàn toàn không đủ cho ứng dụng ngân hàng.

Vì:

Chỉ chạy ở frontend (trình duyệt)
Người dùng có thể tắt validation hoặc sửa request (DevTools, Postman)
Không bảo vệ được dữ liệu khi gửi lên server

3. 3 validation HTML5 KHÔNG làm được
- So sánh nhiều field → Ví dụ: kiểm tra confirm PIN có khớp PIN không, HTML5 không thể so sánh giá trị giữa 2 input
- Kiểm tra dữ liệu từ server → Ví dụ: email đã được đăng ký chưa, số CCCD đã có tài khoản chưa.
- Logic phức tạp → Ví dụ: kiểm tra số CCCD có hợp lệ theo thuật toán của Bộ Công an không, kiểm tra số tài khoản có thuộc ngân hàng nào không, HTML5 chỉ kiểm tra được định dạng bề ngoài.

4. 2 rủi ro nếu chỉ validate frontend
- Bypass validation → Hacker gửi dữ liệu sai trực tiếp lên server
- Tấn công bảo mật (SQL Injection, dữ liệu bẩn) → Không kiểm tra backend → hệ thống bị khai thác
