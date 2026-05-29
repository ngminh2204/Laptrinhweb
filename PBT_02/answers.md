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

- Trường hợp 2: Không submit được → Vì email phải có dạng có @, "abc" sai format

- Trường hợp 3: Không submit được → Vì 15 > max (10) → vượt phạm vi

- Trường hợp 4: Không submit được → Pattern yêu cầu đúng 10 chữ số, nhưng "abc123" sai

- Trường hợp 5: Không submit được → Vì độ dài < 8 ký tự

- Tài liệu: tuan_1_html5/07_forms_interactive.md -> HTML5 Validation Attributes

# Câu A3


