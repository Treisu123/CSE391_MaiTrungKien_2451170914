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
