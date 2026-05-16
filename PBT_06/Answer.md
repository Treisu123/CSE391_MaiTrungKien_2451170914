Phần A:Đọc hiểu.
Câu A1: Grid System.
col-12 col-md-6 col-lg-4

MOBILE (< 768px):              TABLET (≥ 768px):                            DESKTOP (≥ 992px):
┌──────────────────────┐       ┌─────────────┬─────────────┐       ┌─────────┬─────────┬─────────┬─────────┐
│      col-12 (100%)   │       │  col-md-6   │  col-md-6   │       │col-lg-3 │col-lg-3 │col-lg-3 │col-lg-3 │
│      Box 1           │       │  Item 1     │  Box 2      │       │  Box 1  │  Box 2  │  Box 3  │  Box 4  │
├──────────────────────┤       ├─────────────┼─────────────┤       └─────────┴─────────┴─────────┴─────────┘
│      col-12 (100%)   │       │  col-md-6   │  col-md-6   │
│      Box 2           │       │  Box 3      │  Box 4      │
├──────────────────────┤       └─────────────┴─────────────┘
│      col-12 (100%)   │
│      Box 3           │ 
├──────────────────────┤       
│      col-12 (100%)   │
│      Box 4           │ 
└──────────────────────┘       
                             
┌─────────────────────────────────────────────────────────────┐                             
│  Kích thước │   < 768px   |  768px - 991px   |   ≥ 992px    |
├─────────────────────────────────────────────────────────────┤
|  Số cột     |  1 cột      |     2 cột        |  4 cột       |
├─────────────────────────────────────────────────────────────┤
|  Số cột     |  Xếp chồng  |     2 box/hàng   |  4 box/hàng  |
└─────────────────────────────────────────────────────────────┘

- col-md-6: Là mỗi khi màn hình(≥ 768px) thì mỗi box chiếm 6/12 cột.
- Không cần viết col-sm-12: vì bootstrap sử dụng quy tắc mobile-first tự động áp dụng quy tắc từ kích thước nhỏ nhất tới lớn nhất.

Câu A2: Utilities & Components.
1. d-none d-md-block
- Element hiển thị với những màn hình (≥ 768px).
- Element ẩn với những màn hình (< 768px).

2. Liệt kê 5 spacing utilities (margin/padding) và giải thích.
- mt-3: Tạo khoảng cách với phần tử phía trên với size là 3.
- mb-5: Tạo khoảng cách với phần tử phía dưới với size là 5.
- py-4: Thêm phần đệm vào phía trái/phải của phần tử với size là 4.
- px-5: Thêm phần đệm trên/dưới của phần tử với size là 5.
- ms-3: Tạo khoảng cách bên trái với size là 3.

3. Sự khác nhau giữa .container, .container-fluid, .container-md.
- .container: Max-width sẽ thay đổi theo kích thước breakpoint, layout luôn được căn ở giữa màn hình.
- .container-fluid: Width sẽ luôn là 100% với các loại breakpoint khác nhau.
- .container-md: Khi kích thước màn nhỏ hơn kích thước tablet nó hoạt động như một container-fluid, khi kích thước lớn hơn kích thước tablet nó sẽ hoạt động như một container.

Phần C: Phân tích.
Câu C1:Tùy biến Bootstrap.
1. Đổi màu $primary từ xanh mặc định sang #E63946
- Công cụ: 
+ Một công cụ viết code bất kỳ(vs code...).
+ sass.
+ Node.js + npm
- modify file:
// src/custom.scss

// ===== STEP 1: Required imports (bắt buộc) =====
@import "bootstrap/scss/functions";

// ===== STEP 2: Override variables TRƯỚC bootstrap =====

// --- Colors ---
$primary:   #e63946;

// ===== STEP 3: Required Bootstrap imports =====
@import "bootstrap/scss/variables";

// ===== STEP 4: Import Bootstrap components =====
@import "bootstrap/scss/bootstrap";


// ===== STEP 5: Your custom CSS sau Bootstrap =====
// (Thêm styles riêng ở đây)


- Quy trình:
+ npm install bootstrap@5.3.0 sass
+ npm run sass:build
+ npm run sass:watch

2. Tại sao KHÔNG nên override trực tiếp .btn-primary { background: red; } mà nên dùng SASS variables.
- Vì nếu bạn viêt override trực tiếp .btn-primary { background: red; } nó chỉ đổi màu chỗ mà bạn chỉnh sửa mà không đổi màu toàn bộ dẫn đến mất đồng bộ và vì thế để đồng bộ bạn phải sửa chay toàn bộ gây mất thời gian và khó khăn vì vậy nên dùng đến SASS variables.

