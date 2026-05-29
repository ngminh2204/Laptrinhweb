# Câu A1
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
- Tài liệu: tuan_1_html5/07_forms_interactive.md -> Các Input Types HTML5

# Câu A2
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

- Tài liệu: tuan_1_html5/07_forms_interactive.md -> HTML5 Validation Attributes

# Câu A3
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

- Tài liệu: tuan_1_html5/07_forms_interactive.md -> Accessibility — Form cho mọi người

# Câu A4
1. Thuộc tính loading="lazy" giúp ảnh chỉ tải khi gần xuất hiện trên màn hình, từ đó tăng tốc độ tải trang và tiết kiệm băng thông. Tuy nhiên, không nên dùng cho các ảnh quan trọng ở đầu trang vì cần hiển thị ngay.
2. Trong thẻ `<video>`, nên cung cấp nhiều `<source>` để đảm bảo tương thích với nhiều trình duyệt khác nhau; các định dạng phổ biến gồm MP4, WebM và Ogg
3. Thuộc tính alt dùng để mô tả nội dung ảnh cho screen reader, khi ảnh không tải được và hỗ trợ SEO
- Ảnh sản phẩm iPhone 16: alt="Đây là chiếc iPhone 16 màu đen"
- Ảnh trang trí (decorative): alt="Trang trí phòng bếp"
- Ảnh biểu đồ doanh thu Q1/2026: alt="Biểu đồ doanh thu quý 1 năm 2026"

# Câu A5



