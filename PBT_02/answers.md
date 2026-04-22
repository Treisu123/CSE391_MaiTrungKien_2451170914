Phần A:Kiểm tra đọc hiểu
Câu A1:Input Types
1. type="email" → Ô nhập text → tự kiểm tra có @ → Dùng cho form đăng ký.
2. type="text" → Ô nhập text một dòng, không giới hạn ký tự → Không có validation tự động → Nhập họ tên, địa chỉ giao hàng.
3. type="password" → Ô nhập text nhưng ký tự bị ẩn thành *** → Không có validation tự động → Đăng nhập, tạo tài khoản.
4. type="number" → Ô nhập số, có mũi tên tăng/giảm → Chỉ chấp nhận số, hỗ trợ min/max/step → Nhập số lượng sản phẩm trong giỏ hàng.
5. type="checkbox" → Ô vuông tick/untick → Không có validation tự động → Lọc sản phẩm theo nhiều danh mục, chọn size/màu
6. type="radio" → Nút tròn, chỉ chọn 1 trong nhóm → Không có validation tự động → Chọn phương thức thanh toán (COD / thẻ / ví).
7. type="date" → Hiện date picker của trình duyệt/OS → Kiểm tra ngày hợp lệ, hỗ trợ min/max → Chọn ngày giao hàng mong muốn.
8. type="search" → Giống type="text" nhưng có nút ✕ xóa nhanh → Không có validation tự động → Thanh tìm kiếm sản phẩm.
9. type="url" → Ô nhập text, bàn phím mobile hiện thêm ".com" / "/" → Tự kiểm tra phải có http:// hoặc https:// → Nhập link shop/fanpage khi đăng ký tài khoản seller.
10. type="hidden" → Không hiển thị gì trên giao diện → Không có validation → Lưu ngầm order_id, user_id, csrf_token khi submit form.

Câu A2:Validation Attributes.
- TH1: Không Submit được vì required yêu cầu nhập dữ liệu không được để trống. 
- TH2: Không Submit được vì type="email" tự validate format.
- TH3: Không Submit được vì min=1 max=10 mà value=15 vượt quá giới hạn cho phép.
- TH4: Không Submit được vì pattern="[0-9]{10}" yêu cầu nhập đúng 10 chữ số mà value="abc123" chỉ nhập 6 chữ số và có chứa chữ cái.
- TH5: Không Submit được vì minlength="8" yêu cầu nhập ít nhất 8 ký tự mà giá trị value="123" chỉ có 3 ký tự.

-Kết quả dự đoán đúng với kết quản chạy thực tế.

Câu A3:Accessibility
1. <label for="email"> quan trọng cho người dùng screen reader vì nếu không có <label> = người dùng screen reader không biết rằng ô đấy nhập gì.
2. <fieldset> + <legend> được sử dụng khi muốn nhóm input liên quan với nhau thành một khối. VD:
```html
<fieldset>
    <legend>Thông tin giao hàng</legend>
    <label for="addr">Địa chỉ:</label>
    <input type="text" id="addr" name="addr">
</fieldset
```
3. aria-label được dùng cho button icon.
- aria-label không nên dùng khi đã có label vì dùng aria-label sẽ ghi đè lên label làm cho screen reader không đọc đến label mà chỉ đọc aria-label.

Câu A4:Media

1. loading="lazy" trên thẻ <img> Ảnh chỉ tải khi user scroll đến → trang load nhanh hơn!. Không nên dùng với các ảnh nhìn thấy ngay khi vừa mở như logo, banner,....

2. Nên cung cấp nhiều source trong thẻ video vì Browser không hỗ trợ video.
- 3 format phổ biến:
+ MP4
+ WebM
+ OGV

3. Thuộc tính alt để cung cấp văn bản thay thế cho hình ảnh khi mà ảnh bị hỏng, Crawler dùng alt để hiểu nội dung ảnh và screen reader có thể đọc.
```html
<img src="iphone16-black.jpg" alt="iPhone 16 màu đen nhìn từ mặt trước, màn hình 6.1 inch">
<img src="deco.jpg" alt="">
<img src="grafikpendapatan.jpg" alt="Biểu đồ doanh thu Q1/2026: tháng 1 đạt 20 tỷ, tháng 2 đạt 15 tỷ, tháng 3 đạt 24 tỷ, tổng tăng 18% so với Q1/2025">
```

Câu A5:
- Cách 1: Được sử dụng khi chỉ cần ảnh đơn thuần hoặc alt đủ để mô tả.
- Cách 2: Được sử dụng khi cần chú thích nội dung bổ xung hoặc là một nội dung tách rời mà vẫn có ý nghĩa.

- VD:
```html
--Cách 1:
<img src="avatar.jpg" alt="Ảnh đại diện Nguyễn Văn A">

--Cách 2:
<figure>
  <img src="iphone16.jpg" alt="iPhone 16 Pro Max 256GB Titan">
  <figcaption>iPhone 16 Pro Max — 25.990.000đ</figcaption>
</figure>
```

Câu B1:Form Đăng ký Tài khoản
-HTML chỉ kiểm tra được chính field của nó. Việc so sánh password phụ thuộc vào người nhập đây là logic động nên không thể giải quyết bằng html mà phải dùng đến javascript.