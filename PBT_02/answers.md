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

Câu C1:
```html
<form>
    Tên: <input type="text">
    
    <input type="email" placeholder="Email của bạn">
    
    <input type="password" placeholder="Mật khẩu">
    <input type="password" placeholder="Nhập lại mật khẩu">
    
    Phone: <input type="text" value="0901234567">
    
    <select>
        <option>Hà Nội</option>
        <option>TP.HCM</option>
    </select>
    
    <label>
        Tôi đồng ý điều khoản
    </label>
    
    <input type="submit" value="Gửi">
</form>
```
-Lỗi 1: Dòng 75 - Input "Tên" không có <label for=""-> Vi phạm accessibility.
Sửa: <label for="name">Tên:</label> <input type="text" id="name" name="name" required>.

-Lỗi 2: Dòng 77 - Input "Email" không có label for=""-> Vi phạm accessibility.
Sửa: <label for="email">Email:</label> <input type="email" id="email" name="email" required>.

-Lỗi 3: Dòng 79 - Input "Mật khâu" không có label for=""-> Vi phạm accessibility.
Sửa: <label for="password">Mật khẩu:</label> <input type="password" id="password" name="password" required>.

-Lỗi 4: Dòng 80 - Input "Nhập lại mật khẩu" không có label for=""-> Vi phạm accessibility.
Sửa: <label for="confirmpassword">Nhập lại mật khẩu:</label> <input type="password" id="confirmpassword" name="confirmpassword" required>.

-Lỗi 5: Dòng 82 - Input "Phone" không có label for="", sử dụng value thay vì placeholder, type="text" thay vì type="tel"-> Vi phạm validation, accessibility, best practice.
Sửa: <label for="phone">Phone:</label> <input type="tel" id="phone" name="phone" pattern="[0-9]{10}" required>.

-Lỗi 6: Dòng 84 - Select "Thành phố" không có label for="", Không có thuộc tính id và name-> Vi phạm accessibility + validation.
Sửa: <label for="city">Thành phố:</label> <select id="city" name="city">.

-Lỗi 7: Dòng 85 và 86 - option thiếu thuộc tính value -> vi phạm validation
Sửa: <option value="hanoi">Hà Nội</option>.

-Lỗi 8: Dòng 90 - lable không găn với input nào-> vi phạm accessibility.
Sửa: <input type="checkbox" id="terms" name="terms"> <label for="terms">Tôi đồng ý điều khoản</label>

-Lỗi 9: Dòng 93 - Input "Gửi" chưa tối ưu so với button-> Vi phạm Best pracetices.
Sửa: <button type="submit">Gửi</button>.

-Lỗi 10: Dòng 74 - Input không có thuộc tính action/methob-> vi phạm best practice.
Sửa: <form action="/register" method="post">.

Câu C2: Thiết kế chiến lược Validation
```html
<form action="#" method="POST">
  <fieldset>
    <legend>Đăng ký ngân hàng số</legend>

    <label for="cccd">CCCD:</label>
    <input type="text" name="cccd" id="cccd" pattern="[0-9]{12}" maxlength="12" placeholder="Nhập CCCD với đúng 12 số." required>

    <label for="accountNumber">Số tài khoản</label>
    <input type="text" name="accountNumber" id="accountNumber" pattern="[0-9]{10,15}" maxlength="15" placeholder="Nhập số tài khoản với 10-15 số" required>

    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required placeholder="kien@gmail.com" autocomplete="email">

    <label for="pin">PIN:</label>
    <input type="password" id="pin" name="pin" pattern="[0-9]{6}" required>
  </fieldset>
</form>
```
Trả lời câu hỏi:
1.Viết pattern regex cho CMND/CCCD và Số tài khoản.
Pattern của CMND/CCCD: pattern="[0-9]{12}"
pattern của Số tài khoản: pattern="[0-9]{10,15}"
2.Giải thích: HTML5 validation đủ an toàn cho ứng dụng ngân hàng chưa? Tại sao?
-Html5 validation chưa thể mang đến sự an toàn cho cho ngân hàng. Vì html5 chỉ đáp ứng được trong 3 tiêu chí cần có là client validation mà hoàn toàn không đả động gì đến server validation và database validation. Trong khi đó, html validation chỉ kiểm tra dữ liệu đúng không và cho phép submit. Các tin tặc có thể thực hiện các cuộc tấn công mà không cần đả động gì đến nó.

3.Liệt kê 3 loại validation mà HTML5 KHÔNG THỂ làm được (phải dùng JavaScript):
-So sánh giữa 2 field.
-Real-time feedback.
-Async / gọi API.

4.Nêu 2 rủi ro bảo mật nếu chỉ validate trên Frontend mà không validate Backend
- SQL Injection.
- XSS (Cross-Site Scripting).