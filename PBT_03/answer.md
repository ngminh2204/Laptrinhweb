# Phần A - Kiểm tra đọc hiểu
## Câu A1
1. Inline CSS (CSS nội dòng)
- Cách làm: Thêm trực tiếp thuộc tính style vào thẻ HTML muốn định dạng.  Ví dụ code: `<p style="color:red;">Hello world</p>`   
- Ưu điểm: Áp dụng nhanh một kiểu duy nhất cho một phần tử cụ thể.  
- Nhược điểm: Code khó bảo trì khi website lớn, phải viết lặp lại nhiều lần, không tái sử dụng được
- Khi nào nên dùng: Test nhanh giao diện, chỉnh sửa tạm thời

2. Internal CSS (CSS nội bộ)
- Cách làm: Sử dụng cặp thẻ `<style></style>` đặt trong file HTML, thường nằm bên trong thẻ <head>.  
Ví dụ code: 
```html
<head>
    <style>
        h1 { color: red; }
    </style>
</head>
```
- Ưu điểm: Quản lý tập trung các quy tắc CSS cho một trang cụ thể, không cần tạo file riêng. 
- Nhược điểm: Chỉ có tác dụng trên một trang HTML duy nhất, không thể tái sử dụng cho các trang khác trong cùng website.  
- Khi nào nên dùng: website nhỏ, trang đơn.

3. External CSS (CSS bên ngoài)
- Cách làm: Tạo một file .css riêng biệt, sau đó dùng thẻ <link> trong thẻ <head> của HTML để dẫn file vào qua thuộc tính href.  
Ví dụ code: 
```html 
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```
- Ưu điểm: Quản lý dễ dành, tái sử dụng cho nhiều trang, code gọn gàng, dễ bảo trì
- Nhược điểm: Trình duyệt mất thêm thời gian để tải file CSS từ bên ngoài về.
- Khi nào nên dùng: Đây là cách chuyên nghiệp và phổ biến nhất, nên dùng cho tất cả các dự án có nhiều trang web.

## Câu A2
1. h1: → Chọn: `<h1>ShopTLU</h1>` → ShopTLU  
2. .price: → Chọn: `<p class="price">25.990.000đ</p>`, `<p class="price">45.990.000đ</p>` → 25.990.000đ, 45.990.000đ  
3. `#app header`: → Chọn: Toàn bộ nội dung trong thẻ `<header>` → ShopTLU, Home, Products, About  
4. `nav a:first-child`: → Chọn: `<a href="/" class="active">Home</a>` → Home  
5. `.product.featured h2`: → Chọn: `<h2>MacBook Pro</h2>` → MacBook Pro  
6. `article > p`: → Chọn: Các thẻ `<p>` mô tả giá và nội dung của iPhone 16 và MacBook Pro → 25.990.000đ, Mô tả sản phẩm..., 45.990.000đ, Mô tả sản phẩm...  
7. `a[href="/"]`: → Chọn: `<a href="/" class="active">Home</a>` → Home  
8. `.top-bar.dark h1`: → Chọn: `<h1>ShopTLU</h1>` → ShopTLU

## Câu A3
1. Trường hợp 1: content-box (mặc định)
```html
.box-1 {
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```
- Chiều rộng hiển thị: được tính bằng Content + Padding (trái/phải) + Border.  
Tính toán: `(400px + (20px x 2) + (5px x 2) = 450px)`→ Chiều rộng hiển thị = 450px
- Không gian chiếm trên trang: là tổng chiều rộng hiển thị cộng thêm Margin. 
Tính toán: `(450px + (10px x 2) = 470px)`→ Không gian chiếm trên trang = 470px

2. Trường hợp 2: border-box
```html
.box-2 {
    box-sizing: border-box;
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```
- Chiều rộng hiển thị: chính là giá trị width đã thiết lập.  → Chiều rộng hiển thị = 400px
- Kích thước content thực tế: lấy width trừ đi Padding và Border.  
    Tính toán: `(400px - (20px x 2) - (5px x 2) = 350px)`→ Kích thước content thực tế = 350px
- Không gian chiếm trên trang: lấy chiều rộng hiển thị cộng thêm Margin. 
    Tính toán: `(400px + (10px x 2) = 420px)`→ Không gian chiếm trên trang = 420px

3. Trường hợp 3: Margin collapse (Gộp lề)
```html
.box-a { margin-bottom: 25px; }
.box-b { margin-top: 40px; }
```
Khoảng cách giữa box-a và box-b: là giá trị lớn nhất giữa hai lề.
-> Khoảng cách giữa 2 box: 40px

## Câu A4
1. Specificity score (a, b, c) của từng rule
- p { color: black; } → Rule A
    Selector loại (p) = 1
    Score: (0, 0, 1)

- .price { color: blue; } → Rule B
    Class (.price) = 1
    Score: (0, 1, 0)

- #main-price { color: red; } → Rule C
    ID (#main-price) = 1
    Score: (1, 0, 0)

- p.price { color: green; } → Rule D
    p = element = 1
    .price = class = 1
    Score: (0, 1, 1)
  
2. Element sẽ có màu gì? Giải thích
- Element sẽ có màu đỏ do Specificity của `#main-price` là cao nhất nên thắng tất cả

3. Nếu thêm `<p class="price" id="main-price" style="color: orange;">`, element có màu gì?
- Element sẽ có màu cam do Specificity của `#style="color: orange` là (1,0,0,0) nên thắng tất cả

4. Nếu Rule A thêm `!important`, element có màu gì? Tại sao?
- Element sẽ có màu đen do `!important` có specificity vô cực — phá vỡ toàn bộ quy tắc thông thường

# Phần B: Thực hành 
## Bài B1
- 5 loại selector có trong file `style.css`

1. Element selector: `body`, `header`, `table`, `footer`
2. Class selector: `nav a.active`
3. ID selector: `#about`
4. Descendant selector: `nav a`, `table th`, `table td`
5. Pseudo-class selector:  `nav a:hover`, `tr:nth-child(even)`, `tr:hover`

## Bài B2
1. Phần 1 — content-box vs border-box
- Hộp 1 (content-box): chiều rộng thực tế = 350px (đo từ DevTools)
- Hộp 2 (border-box): chiều rộng thực tế = 300px (đo từ DevTools)

Giải thích sự khác biệt:
- Hộp 1 dùng content-box (mặc định): width: 300px chỉ tính phần content. Padding và border được cộng thêm ra ngoài → chiều rộng thực tế = 300 + 20×2 + 5×2 = 350px.
- Hộp 2 dùng border-box: width: 300px là tổng kích thước bao gồm cả padding và border. Chúng co vào trong → chiều rộng thực tế luôn đúng 300px.

2. Phần 2 — Layout 3 cột
Trường hợp KHÔNG dùng border-box (content-box):
- Cột trái: 250 + 15×2 = 280px
- Cột giữa: 500 + 20×2 = 540px
- Cột phải: 250 + 15×2 = 280px
- Tổng = 280 + 540 + 280 = 1100px → vượt quá container 1000px → layout vỡ

Trường hợp CÓ dùng border-box:
- Cột trái: đúng 250px
- Cột giữa: đúng 500px
- Cột phải: đúng 250px
- Tổng = 250 + 500 + 250 = 1000px → vừa khít container → layout đúng

## Bài B3
1. Liệt kê 10 rules + specificity score
- `* { color: gray; }` - Specificity: (0,0,0)
- `p { color: black; }` - Specificity: (0,0,1)
- `.text { color: blue; }` - Specificity: (0,1,0)
- `.highlight { color: yellow; }` - Specificity: (0,1,0)
- `p.text { color: orange; }` - Specificity: (0,1,1)
- `p.highlight { color: purple; }` - Specificity: (0,1,1)
- `.text.highlight { color: violet; }` - Specificity: (0,2,0)
- `p.text.highlight { color: pink; }` - Specificity: (0,2,1)
- `#demo { color: red; }` - Specificity: (1,0,0)
- `p#demo.text.highlight { color: blueviolet; }` - Specificity: (1,2,1)

2. Element cuối cùng hiển thị màu gì? Tại sao?
Màu: `blueviolet` — do Rule 10 có selector `p#demo.text.highlight` với specificity cao nhất.

Tính theo hệ 3 cột (ID, Class, Tag):
- `p` → tag → cột Tag +1 → (0, 0, 1)
- `#demo` → ID → cột ID +1 → (1, 0, 0)
- `.text` → class → cột Class +1 → (0, 1, 0)
- `.highlight` → class → cột Class +1 → (0, 1, 0)
- Tổng: (1, 2, 1)

3. Thay đổi thứ tự rules trong CSS — Kết quả có đổi không?
- Không đổi.
- Khi các rules có specificity khác nhau, thứ tự viết trong file CSS không ảnh hưởng. Rule có specificity cao hơn luôn thắng dù viết trước hay sau.
- Thứ tự chỉ quan trọng khi 2 rules có specificity bằng nhau — lúc đó rule viết sau thắng (cascade). Ví dụ nếu có 2 rule cùng specificity 121, rule nào đứng sau trong file CSS sẽ được áp dụng.

# Phần C: Debug & Suy luận
## Câu C1
