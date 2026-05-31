# Phần A: Kiểm tra đọc hiểu
## Câu A1

| Position   | Vẫn chiếm chỗ trong flow? | Tham chiếu vị trí                        | Cuộn theo trang?                        | Use case                                  |
| ---------- | ------------------------- | ---------------------------------------- | --------------------------------------- | ----------------------------------------- |
| `static`   | Có                        | Không dùng top/left/bottom/right         | Có                                      | Mặc định, không cần can thiệp             |
| `relative` | Có                        | Vị trí gốc của chính nó                  | Có                                      | Dịch chuyển nhẹ, làm mốc cho absolute con |
| `absolute` | Không                     | Thẻ cha gần nhất có position khác static | Có (cuộn cùng cha)                      | Badge trên icon, dropdown, tooltip        |
| `fixed`    | Không                     | Cửa sổ trình duyệt                       | Không — luôn dính tại chỗ               | Chat button, modal overlay                |
| `sticky`   | Có → Không (khi dính)     | Cửa sổ trình duyệt (sau khi đạt ngưỡng)  | Có → Không (dính khi scroll đến ngưỡng) | Sticky header, sidebar                    |

- Tham chiếu `body`: Khi tất cả các phần tử tổ tiên bọc ngoài nó đều không được định vị (đều giữ `position: static` mặc định), phần tử absolute sẽ tìm ngược lên cho đến khi lấy khung tài liệu ngoài cùng (`body` / `html`) làm điểm tựa.

- Tham chiếu `parent`: Khi phần tử cha trực tiếp được thiết lập `position` khác `static` (thường dùng nhất là `position: relative;`).

- Nearest Positioned Ancestor: Là phần tử bọc ngoài gần nhất (cha, ông, cố...) có thuộc tính `position` mang giá trị khác với `static` (như `relative`, `absolute`, `fixefixe`, `sticky`). Nó được dùng làm mốc tọa độ (0,0) để định vị phần tử con.

## Câu A2
1. Trường hợp 1
```css
.container {
  display: flex;
}
.item {
  flex: 1;
}
/* 4 items */
```

```
┌─────────────────────────────────────────────────────┐
│  CONTAINER (100% width)                             │
│ ┌──────────┬──────────┬──────────┬──────────┐       │
│ │  Item 1  │  Item 2  │  Item 3  │  Item 4  │       │
│ │  (25%)   │  (25%)   │  (25%)   │  (25%)   │       │
│ └──────────┴──────────┴──────────┴──────────┘       │
└─────────────────────────────────────────────────────┘
```

Giải thích:
- `display: flex` → các item xếp thành 1 hàng ngang (mặc định `flex-direction: row`)
- `flex: 1` = `flex-grow: 1; flex-shrink: 1; flex-basis: 0%`
- Cả 4 item cùng `flex: 1` → chia đều container theo chiều ngang

2. Trường hợp 2
```css
.container {
  display: flex;
  flex-wrap: wrap;
}
.item {
  width: 45%;
  margin: 2.5%;
}
/* 6 items */
```

```
┌─────────────────────────────────────────────────────┐
│  CONTAINER                                          │
│  ┌───────────────┐  ┌───────────────┐               │
│  │    Item 1     │  │    Item 2     │               │
│  │  (45% + 5%m)  │  │  (45% + 5%m)  │               │
│  └───────────────┘  └───────────────┘               │
│  ┌───────────────┐  ┌───────────────┐               │
│  │    Item 3     │  │    Item 4     │               │
│  └───────────────┘  └───────────────┘               │
│  ┌───────────────┐  ┌───────────────┐               │
│  │    Item 5     │  │    Item 6     │               │
│  └───────────────┘  └───────────────┘               │
└─────────────────────────────────────────────────────┘
```

Giải thích:
- Mỗi item chiếm: `width 45% + margin-left 2.5% + margin-right 2.5%` = 50% tổng chiều ngang
- `flex-wrap: wrap` → khi không đủ chỗ, item xuống hàng
- 100% ÷ 50% = 2 item mỗi hàng
- 6 items ÷ 2 = 3 hàng

3. Trường hợp 3
```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
/* 3 items */
```

```
┌─────────────────────────────────────────────────────┐
│  CONTAINER                                          │
│                                                     │
│  ┌────────┐          ┌────────┐          ┌────────┐ │
│  │ Item 1 │          │ Item 2 │          │ Item 3 │ │
│  └────────┘          └────────┘          └────────┘ │
│    (trái)              (giữa)              (phải)   │
│                                                     │
└─────────────────────────────────────────────────────┘
     ↑                    ↑                    ↑
  sát trái          căn giữa ngang          sát phải
  (cả 3 đều căn giữa dọc nhờ align-items: center)
```

Giải thích:
- `justify-content: space-between` → item đầu sát trái, item cuối sát phải, item giữa chính giữa, khoảng cách đều nhau giữa các items
- `align-items: center` → tất cả items căn giữa theo chiều dọc

4. Trường hợp 4
```css
.container {
  display: grid;
  grid-template-columns: 200px 1fr 200px;
  gap: 20px;
}
/* 3 items */
```

```
┌─────────────────────────────────────────────────────┐
│  CONTAINER (ví dụ 1000px)                           │
│                                                     │
│ ┌──────────┐ ┌──────────────────────┐ ┌──────────┐  │
│ │          │ │                      │ │          │  │
│ │  Item 1  │ │       Item 2         │ │  Item 3  │  │
│ │  200px   │ │   1fr (linh động)    │ │  200px   │  │
│ │          │ │                      │ │          │  │
│ └──────────┘ └──────────────────────┘ └──────────┘  │
│              (gap 20px giữa mỗi cột)                │
└─────────────────────────────────────────────────────┘
```

Giải thích:
- Cột 1: cố định 200px
- Cột 2: `1fr` = chiếm toàn bộ phần còn lại sau khi trừ 200px + 200px + 2 khoảng gap
- Cột 3: cố định 200px
- Tính width cột giữa (giả sử container = 1000px):`1fr = 1000px - 200px - 200px - (20px × 2) = 560px`

5. Trường hợp 5
```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}
/* 7 items */
```

```
┌─────────────────────────────────────────────────────┐
│  CONTAINER                                          │
│                                                     │
│ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐     │
│ │   Item 1    │ │   Item 2    │ │   Item 3    │     │
│ └─────────────┘ └─────────────┘ └─────────────┘     │
│ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐     │
│ │   Item 4    │ │   Item 5    │ │   Item 6    │     │
│ └─────────────┘ └─────────────┘ └─────────────┘     │
│ ┌─────────────┐                                     │
│ │   Item 7    │   (trống)          (trống)          │
│ └─────────────┘                                     │
│   ← 1fr →          ← 1fr →           ← 1fr →        │
│                                                     │
└─────────────────────────────────────────────────────┘
```

Giải thích:
- `repeat(3, 1fr)` → 3 cột đều nhau
- 7 items ÷ 3 cột = 2 hàng đầy + 1 hàng thiếu
- Hàng 1: Item 1, 2, 3
- Hàng 2: Item 4, 5, 6
- Hàng 3: Item 7 — chỉ có 1 item, nằm ở cột đầu tiên
- Item 7 không tự kéo rộng ra để lấp đầy — nó giữ nguyên kích thước `1fr` của cột

# Phần C: Suy luận
## Câu C1
1. Navigation bar ngang (logo + menu + buttons)
- Lựa chọn: Flexbox
- Giải thích: Thanh điều hướng ngang là tập hợp các phần tử sắp xếp theo một chiều duy nhất (trục ngang). Flexbox xử lý cực tốt việc căn giữa theo chiều dọc `(align-items: center)` và phân bổ khoảng cách linh hoạt giữa các cụm phần tử `(justify-content: space-between)`.
2. Lưới ảnh Instagram (3 cột đều nhau, số ảnh không biết trước)
- Lựa chọn: Grid
- Giải thích: Đây là bố cục dạng lưới 2 chiều (hàng và cột) cố định. Việc sử dụng CSS Grid với cấu hình `grid-template-columns: repeat(3, 1fr)` sẽ tự động tính toán tạo ra 3 cột bằng nhau, và khi số lượng ảnh tăng lên không giới hạn, các ảnh mới sẽ tự động nhảy xuống hàng tiếp theo một cách thẳng hàng, vuông vức mà không lo bị lệch dòng.
3. Layout blog: main content + sidebar
- Lựa chọn: Grid (hoặc Flexbox đều được, nhưng tối ưu nhất cho khung lớn là Grid)
- Giải thích: Đây là layout tổng thể của trang web (Macro Layout). Sử dụng CSS Grid giúp thiết lập hệ thống cột rõ ràng ngay từ đầu (ví dụ: `grid-template-columns: 1fr 300px`), quản lý khoảng cách bằng gap trực quan và giúp cấu trúc bố cục trang web mạch lạc, không bị phụ thuộc vào kích thước nội dung bên trong.
4. Footer với 4 cột thông tin (Về chúng tôi, Liên kết, Hỗ trợ, Liên hệ)
- Lựa chọn: Grid hoặc Flexbox (Kết hợp cả hai là tốt nhất)
- Giải thích:  Nên dùng Grid cho phần bao ngoài của Footer để chia đều khung thành 4 cột cố định một cách nhanh chóng (`grid-template-columns: repeat(4, 1fr)`).
Bên trong từng cột thông tin nhỏ, có thể dùng Flexbox theo chiều dọc (flex-direction: column) để quản lý danh sách các thẻ liên kết đi kèm.
5. Card sản phẩm (ảnh trên, text giữa, nút dưới — nút luôn dính đáy)
- Lựa chọn: Flexbox
- Giải thích: Cấu trúc bên trong của một card sản phẩm đi theo một chiều duy nhất từ trên xuống dưới (trục dọc). Khi thiết lập `display: flex;` `flex-direction: column`; cho card, ta chỉ cần thêm thuộc tính  `margin-top: auto;` cho nút bấm ở dưới cùng. Cơ chế của Flexbox sẽ tự động đẩy nút bấm bám chặt vào đáy card một cách hoàn hảo, bất kể phần text ở giữa dài hay ngắn.

## Câu C2
### Lỗi 1: Cards không đều chiều cao — nút "Mua" bị nhảy lên/xuống
1. Nguyên nhân
- Các card có lượng text khác nhau nên chiều cao mỗi card khác nhau. 
- Nút `.btn` không được đẩy xuống đáy card nên vị trí bị lệch.

2. Cách sửa
- Chúng ta cần biến `.card` thành một Flex container theo hướng dọc (column), sau đó gán `margin-top: auto` cho nút bấm để ép nó luôn bám đáy.

3. Code sửa
```css
.card-container { 
    display: flex; 
    flex-wrap: wrap; 
}
.card { 
    width: 30%; 
    margin: 1.5%; 
    display: flex;
    flex-direction: column;
}
.card img { width: 100%; }
.card h3 { font-size: 18px; }
.card .btn { 
    padding: 10px; 
    margin-top: auto; 
}
```

### Lỗi 2 — Item không nằm giữa màn hình
1. Nguyên nhân
- Thuộc tính `text-align: center`; viết trong phần tử con `.hero-content` chỉ có tác dụng căn giữa các thành phần dạng văn bản (inline element) nằm bên trong chính nó, chứ không thể tự căn giữa cả khối `.hero-content` so với cha.

- Thẻ cha `.hero` đã có `display: flex;` nhưng chưa hề cấu hình các thuộc tính căn chỉnh tọa độ của Flexbox, khiến phần tử con mặc định bị đẩy về góc trái trên.

2. Cách sửa
- Bỏ thuộc tính `text-align` không hiệu quả ở thẻ con đi. 
- Thay vào đó, thêm bộ đôi quyền lực `justify-content: center` (căn giữa ngang) và `align-items: center` (căn giữa dọc) trực tiếp vào thẻ cha `.hero`.

3. Code sửa
```css
.hero {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}
.hero-content {
    text-align: center; 
}
```

### Lỗi 3: Sidebar bị co lại khi content quá dài
1. Nguyên nhân
- Trong cơ chế của Flexbox, các phần tử con mặc định sở hữu thuộc tính `flex-shrink: 1`. 
- Giá trị này cho phép phần tử tự động co nhỏ kích thước lại (nhỏ hơn mức `width: 250px` được thiết lập) khi không gian hiển thị tổng thể của container bị thiếu hụt.
- Khi `.content` chứa nội dung quá dài, khiến `.sidebar` bị méo mó, co cụm lại.

2. Cách sửa
- Cần chặn không cho phép `.sidebar` co lại bằng cách đổi thuộc tính `flex-shrink` về giá trị 0.

3. Code sửa
```css
.layout {
  display: flex;
}
.sidebar {
    width: 250px;
    flex-shrink: 0;
}
.content { flex: 1; }
```
