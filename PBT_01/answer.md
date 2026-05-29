# PHẦN A - KIỂM TRA ĐỌC HIỂU
## Câu A1 - HTTP & Browser
### 1. Khi bạn gõ https://shopee.vn vào trình duyệt và nhấn Enter thứ tự các bước xảy ra là:
- DNS Lookup: Trình duyệt tìm kiếm địa chỉ IP của tên miền shopee.vn.
- Thiết lập kết nối: Trình duyệt thực hiện bắt tay TCP/IP (và TLS cho HTTPS) để kết nối với server.
- Gửi Request: Trình duyệt gửi HTTP Request đến Server của Shopee để yêu cầu nội dung trang web.
- Nhận Response: Server xử lý và gửi ngược lại HTTP Response (chứa mã 200 OK và các file HTML/CSS/JS).
- Rendering: Trình duyệt đọc code và hiển thị giao diện hoàn chỉnh lên màn hình.
### 2. Trong DevTools của Chrome, tab Network cho thấy:
<img width="1340" height="681" alt="image" src="https://github.com/user-attachments/assets/256674b4-e40b-4abc-ad90-0fab98dbca52" />

## Câu A2 - Semantic HTML
- Dùng `<div>` thay cho thẻ semantic
    + `<div class="header">` nên dùng `<header>`
    + `<div class="main">` nên dùng `<main>`
    +`<div class="footer">` nên dùng `<footer>`
- Không dùng <nav> cho menu: Google không nhận diện được điều hướng
- Tiêu đề sản phẩm không dùng heading `(<h1>, <h2>)`
- Ảnh không có alt: Google không hiểu nội dung hình
  ```html
  <header>
    <div class="logo">ShopTLU</div>
    <nav>
      <ul>
        <li><a href="/">Trang chủ</a></li>
        <li><a href="/products">Sản phẩm</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <article class="product">
      <h1>iPhone 16 Pro</h1>
      <p class="price">25.990.000đ</p>
      <img src="iphone.jpg" alt="iPhone 16 Pro" />
    </article>
  </main>

  <footer>© 2026 ShopTLU</footer>
  ```
(tuan_1_html5\04_visible_part_html.md + Bản đồ sementic elements)

## Câu A3 
```
Hộp 1
Text A Text B
Hộp 2
Text C **Text D**
Hộp 3
- Thẻ <div> là block element: luôn chiếm 1 dòng riêng 
- Thẻ <span>, <strong> là inline element: hiển thị cùng dòng
```
Nguồn tham khảo: (tuan_1_html5/02_basic_structure_html.md + phần: Các thẻ cơ bản trong <body>)

## Câu A4
Sự khác nhau giữa `<thead>`, `<tbody>`, `<tfoot>` là:
`<thead>`: tiêu đề cột,nằm ở đầu bảng
`<tbody>`: dữ liệu chính,nằm ở giữa bảng
`<tfoot>`: tổng kết,nằm ở phần cuối bản dù có xếp không đúng thứ tự 3 thẻ trên thì dữ liệu nó vẫn sẽ hiển thị theo thứ tự là `<thead>` -> `<tbody>` -> `<tfoot>`

(tham chiếu tuan_1_html5/05_tables_hyperlinks.md + phần: Table bảng dữ liệu)

Không nên dùng table cho việc làm layout là vì:
- Sai semantic
- Code phức tạp, khó bảo trì
- Hiển thị kém linh hoạt (responsive kém): Table khó thích nghi với mobile

(tuan_1_html5/05_tables_hyperlinks.md + phần: Table bảng dữ liệu)

# Phần B - Thực hành code 
## Câu B3

  Lỗi 1: Dòng 1 — `<!DOCTYPE>` thiếu khai báo html — Sửa thành `<!DOCTYPE html>`

  Lỗi 2: Dòng 2 — `<html>` thiếu thuộc tính lang — Sửa thành `<html lang="vi">`

  Lỗi 3: Dòng 3 – Thiếu thẻ đóng `</title>` – Thêm thẻ đóng `</title>` sau chữ "Trang web".

  Lỗi 4: Dòng 5 — `<meta charset="utf8">` sai giá trị charset — Sửa thành `<meta charset="UTF-8">`

  Lỗi 5: Dòng 8 — `<h1>` thẻ đóng thiếu dấu / — Sửa thành `</h1>`

  Lỗi 6: Dòng 11 — `<a>` thẻ đóng thiếu dấu / — Sửa thành `</a>`

  Lỗi 7: Dòng 19 — `<img src=iphone.jpg>` src không có dấu nháy "" — Sửa thành `<img src="iphone.jpg">`

  Lỗi 8: Dòng 21 — `<p>Giá: <b>25.990.000đ</p></b>` thẻ đóng bị lồng sai thứ tự — Sửa thành `<p>Giá: <b>25.990.000đ</b></p>`

  Lỗi 9: Dòng 26 — Sử dụng thẻ `<td>` cho tiêu đề bảng – Cách sửa: Đổi thành thẻ `<th>` 
  
  Lỗi 10: Dòng 40 — Dùng `<main>` lần 2 cho sidebar — Một trang chỉ được có 1 thẻ `<main>`, sidebar phải dùng `<aside>` — Sửa thành `<aside>` nằm trong `<main>`

  Lỗi 11: Dòng 45 — Thiếu thẻ đóng `</p>` – Thêm thẻ đóng `</p>`
  
## Câu C1
```html
<!-- Header + Navigation -->
<header> <!-- header: phần đầu trang -->
  <nav> <!-- nav: chứa menu điều hướng -->
    <ul> <!-- ul: danh sách menu -->
      <li><a href="#">Trang chủ</a></li> <!-- link điều hướng -->
      <li><a href="#">Sản phẩm</a></li>
    </ul>
  </nav>
</header>

<!-- Breadcrumb -->
<nav aria-label="breadcrumb"> <!-- nav: điều hướng breadcrumb -->
  <ol> <!-- ol vì breadcrumb có thứ tự -->
    <li><a href="#">Trang chủ</a></li>
    <li><a href="#">Điện thoại</a></li>
    <li>iPhone 16</li> <!-- item hiện tại -->
  </ol>
</nav>

<main> <!-- main: nội dung chính -->

  <section> <!-- section: nhóm nội dung ảnh -->
    <h2>Hình ảnh sản phẩm</h2> <!-- tiêu đề -->
    <div> <!-- div: chứa ảnh -->
      <img src="#" alt="ảnh 1">
      <img src="#" alt="ảnh 2">
      <img src="#" alt="ảnh 3">
      <img src="#" alt="ảnh 4">
      <img src="#" alt="ảnh 5">
    </div>
  </section>

  <!-- Thông tin sản phẩm -->
  <section> <!-- section: thông tin chính -->
    <h1>iPhone 16</h1> <!-- tên sản phẩm -->
    <p>Giá: 1000000</p> <!-- giá -->
    <p>Đánh giá: ★★★★☆</p> <!-- rating -->
    <p>Mô tả: Đây là ip 16</p> <!-- mô tả -->
  </section>

  <!-- Bảng thông số -->
  <section> <!-- section: thông số -->
    <h2>Thông số kỹ thuật</h2>
    <table> <!-- table: dữ liệu dạng bảng -->
      <tr>
        <th>Thông số</th> <!-- tiêu đề cột -->
        <th>Giá trị</th>
      </tr>
      <tr>
        <td>Màn hình</td>
        <td>...</td>
      </tr>
    </table>
  </section>

  <!-- Đánh giá -->
  <section> <!-- section: đánh giá -->
    <h2>Bình luận</h2>
    <article> <!-- article: 1 comment độc lập -->
      <p>Người dùng A: Sản phẩm tốt</p>
    </article>
  </section>

  <!-- Sidebar -->
  <aside> <!-- aside: nội dung phụ -->
    <h2>Sản phẩm tương tự</h2>
    <ul>
      <li><a href="#">Sản phẩm 1</a></li>
      <li><a href="#">Sản phẩm 2</a></li>
    </ul>
  </aside>

</main>

<!-- Footer -->
<footer> <!-- footer: cuối trang -->
  <p>© 2026 Shop</p>
</footer>
```

## Câu C2
- Dùng toàn `<div>` là cách làm nhanh nhưng không tốt về lâu dài. Semantic HTML không hề lãng phí thời gian vì hai lý do cốt lõi:
  - SEO: Các bot tìm kiếm dựa vào `<main>`, `<article>` để hiểu cấu trúc nội dung, giúp xếp hạng web tốt hơn. Nếu chỉ dùng `<div>`, công cụ tìm kiếm khó biết đâu là nội dung chính
  - Accessibility: Trình đọc màn hình (Screen Reader) dùng `<nav>` hay `<header>` để giúp người khiếm thị định vị. Ví dụ `<nav>` giúp biết đó là menu, `<article>` là bài viết. Nếu dùng toàn `<div>`, trải nghiệm sẽ kém.
- Tuy nhiên, thẻ `<div>` sinh ra là để làm nhiệm vụ bọc dữ liệu thuần túy (wrapper) phục vụ cho mục đích CSS Layout (như Flexbox/Grid) hoặc gom cụm để định dạng style.
