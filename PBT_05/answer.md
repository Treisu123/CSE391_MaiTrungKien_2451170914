Phần A:KIỂM TRA ĐỌC HIỂU.
Câu A1:Viewport & Mobile-First.
1. <meta name="viewport" content="width=device-width, initial-scale=1.0">
- name="viewport":Dùng để cấu hình vùngg hiển thị(viewport) của trình duyệt trên thiết bị di động.
- width=device-width: Đăt chiều rộng vùng hiển thị(viewport) bằng đúng chiều rộng màn hình thiết bị.
- initial-scale=1.0: Mức bắt đầu của trang.

2. Thiếu dòng này: iPhone giả định trang rộng 980px (như desktop) → thu nhỏ lại → chữ bé xíu → UX tệ.

3. Sự khác nhau giữa Mobile-First và Desktop-First.
- Mobile-First: Viết code css cho màn hình nhỏ trước, sau đó mở rông cho các màn hình lớn hơn và mỗi mốc thì dùng min-width.
- Desktop-First: Viết code css cho các máy có màn hình lớn trước, sau đó thu hẹp lại và với mỗi mốc thì sử dụng max-width.

-Mobile-First:
.product-grid {
    display: grid;
    grid-template-columns: 1fr;     /* 1 cột trên mobile */
    gap: 16px;
}

@media (min-width: 768px) {
    .product-grid {
        grid-template-columns: repeat(2, 1fr);   /* 2 cột tablet nhỏ */
    }
}
- Desktop-First:
.product-grid { grid-template-columns: repeat(4, 1fr); }
@media (max-width: 768px) { /* 3 cột */ }

- Mobile-First tốt hơn vì:
+ Mobile tải ít CSS hơn (mobile chỉ tải mobile styles, không download desktop styles).
+ Buộc bạn ưu tiên nội dung quan trọng trước (content thinking).
+ Google và performance tools đánh giá cao hơn.

Câu A2:Breakpoints.
- Mobile:
+ Kích thước pixel: < 576px.
+ Thiết bị đại diện: iPhone SE, các điện thoại nhỏ.
+ Lưới sản phẩm: 1 cột.

- Mobile L: 
+ Kích thước pixel: ≥ 576px. 
+ Thiết bị đại diện: iPhone Plus, điện thoại ngang.
+ Lưới sản phẩm: 1-2 cột.

- Tablet:
+ Kích thước pixel: ≥ 768px
+ Thiết bị đại diện: iPad dọc, tablet.
+ Lưới sản phẩm: 2 cột.

- Desktop:
+ Kích thước pixel: ≥ 992px.
+ Thiết bị đại diện: Laptop nhỏ.
+ Lưới sản phẩm: 3 cột.

- Desktop L:
+ Kích thước pixel: ≥ 1200px
+ Thiết bị đại diện: Desktop, laptop lớn
+ Lưới sản phẩm: 4 cột.

- Desktop XL:
+ Kích thước pixel: ≥ 1400px.
+ Thiết bị đại diện: Màn hình 4K, ultrawide
+ Lưới sản phẩm: 4-6 cột.

Câu A3:Media Queries
| Chiều rộng màn hình | `.container` width |
|---|---|
| 375px (iPhone SE) | 375px |
| 600px | 540px |
| 800px | 720px |
| 1000px | 960px |
| 1400px | 1140px    |

Câu A4:SCSS Basics.
1. Variables — "Sửa 1 chỗ, tất cả tự đổi".
$color-primary:     #7c3aed;
$color-primary-dark: darken($color-primary, 10%);   
$color-danger:      #dc2626;
$color-success:     #16a34a;
$color-text:        #1e293b;
$color-bg:          #f8fafc;

$font-family-base:  'Inter', sans-serif;
$font-size-base:    16px;
$font-size-sm:      14px;
$font-size-lg:      18px;

$space-1: 4px;
$space-2: 8px;
$space-4: 16px;
$space-6: 24px;

$radius-sm:   6px;
$radius-md:   12px;
$radius-full: 9999px;

$transition-base: 0.3s ease;

.btn-primary
{
    background: $primary-color;
    color: $color-text;
    border-radius: $radious-sm;
}

2. Nesting — CSS theo cấu trúc HTML
.navbar
{
    backround: #1a202c;
    padding: $space-4;
    display: flex;
    align-items: center;
    justify-content: space-between;

    &__logo {
        color: white;
        font-size: $font-size-lg;
        font-weight: 700;
        text-decoration: none;
    }

    &__links {
        display: flex;
        gap: $space-6;
        list-style: none;
    }
}

3. Mixins — "Hàm CSS tái sử dụng".
@mixin flex-center {
    display: flex;
    justify-content: center;
    align-items: center;
}

@mixin flex-between {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

@mixin button-style($bg, $color: white, $hover-bg: null) {
    background: $bg;
    color: $color;
    padding: $space-3 $space-6;
    border: none;
    border-radius: $radius-sm;
    cursor: pointer;
    font-weight: 600;
    transition: background $transition-base, transform $transition-base;

    &:hover {
        background: if($hover-bg, $hover-bg, darken($bg, 10%));
        transform: translateY(-2px);
    }

    &:active { transform: translateY(0); }
}

@mixin respond-to($breakpoint) {
    @if $breakpoint == mobile {
        @media (max-width: 576px) { @content; }
    } @else if $breakpoint == tablet {
        @media (min-width: 768px) { @content; }
    } @else if $breakpoint == desktop {
        @media (min-width: 1024px) { @content; }
    }
}

.btn-primary {
    @include button-style($color-primary);
}

.btn-danger {
    @include button-style($color-danger);
}

.modal {
    @include flex-center;
    position: fixed;
    inset: 0;
}

.product-grid {
    display: grid;
    grid-template-columns: 1fr;

    @include respond-to(tablet) {
        grid-template-columns: repeat(2, 1fr);
    }

    @include respond-to(desktop) {
        grid-template-columns: repeat(4, 1fr);
    }
}

4. Partials & Import — "Chia file gọn gàng".
styles/
├── base/
│   ├── _variables.scss      
│   ├── _reset.scss          
│   └── _typography.scss   
│
├── mixins/
│   ├── _flexbox.scss        
│   ├── _responsive.scss    
│   └── _buttons.scss       
│
├── components/
│   ├── _navbar.scss
│   ├── _card.scss
│   ├── _button.scss
│   ├── _form.scss
│   └── _modal.scss
│
└── main.scss                

- Vì scss là ngôn ngữ mở rộng chạy phía build nên cần phải biên dịch thành css trước khi trình duyệt có thể đọc.
-Các cách để có thể biên dịch từ scss->css:
1. VS Code + Live Sass Compiler extension
   → Click "Watch Sass" ở status bar
   → Tự compile mỗi khi save

2. Vite (React/Vue project):
   npm install -D sass
   → Vite tự detect và compile .scss files

3. Node.js script:
   npm install -D sass
   npx sass styles/main.scss styles/main.css --watch

4. Create React App:
   npm install sass
   → Đổi .css thành .scss → tự compile

Phần B:
Câu B3: Lệnh compile scss -> css.
- Dùng live scss compiler:
+ cài extension live scss compile.
+ Click vào watch scss.
+ Thư mục main.css tự động được sinh ra trong thư mục scss.

- Dùng terminal:
```bash
Cài Sass
npm install -g sass

Compile một lần
sass scss/main.scss scss/main.css

Tự động compile khi lưu file
sass --watch scss/main.scss:scss/main.css
```
- Kết quả
+ Input:  `scss/main.scss`
+ Output: `scss/main.css`

Phần C:
Câu C1:
- Navigation thay đổi:
+ Mobile: Hamburger góc trái và sau nó là logo. Bên phải có biểu hiện hình người bị cắt đi chữ đăng nhâp va hình chuông. Nav chính ẩn hoàn toàn. Chỉ hiện danh mục hiện tại và thanh cuộn.
+ Tablet: Hamburger góc trái và sau nó là logo. Bên phải có biểu hiện hình người bị cắt đi chữ đăng nhâp, hình chuông và phần mới nhất|international. Nav hiện một phần và nó dấu -> để xem toàn bộ thẻ điều hướng.
+ Desktop: Ẩn đi hamburger. Bên trái hiện logo và ngày. Bên phải hiện biểu tượng hình người với chữ đăng nhập và hình chuông, sau nó là mới nhất|theo khu vực|international. Hiển thị toàn bộ thanh điều hướng.
- Lưới content: 
+ Mobile: 1 Cột.
+ Tablet: 1-2 cột.
+ Desktop: 3-4 cột
- Element bị ẩn trên mobile: Toàn bộ nav ngang ẩn. "Mới nhất","Theo khu vực", "International", "Đăng nhập" ẩn. Ngày tháng ẩn.
- Font size: Cỡ chữ có sự thay đổi khi ở mobile so với 2 kiểu còn lại.