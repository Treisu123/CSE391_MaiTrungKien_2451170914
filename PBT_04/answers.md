Phần A:KIỂM TRA ĐỌC HIỂU.
Câu A1:5 Loại Positioning
- static: 
+ Vẫn chiếm vị trí trong flow: Có.
+ Tham chiếu vị trí: Không dùng.
+ Cuộn theo trang: Có.
+ Use case: Mặc định. Không cần viết.

- relative:
+ Vẫn chiếm vị trí trong flow: Có.
+ Tham chiếu vị trí: Vị trí gốc của nó.
+ Cuộn theo trang: Có.
+ Use case: Làm anchor cho absolute con, dịch nhẹ.

- absolute:
+ Vẫn chiếm vị trí trong flow: Không.
+ Tham chiếu vị trí: Bám vào cha relative gần nhất.
+ Cuộn theo trang: Có.
+ Use case: Badge, dropdown, tooltip, overlay.

- fixed:
+ Vẫn chiếm vị trí trong flow: Có.
+ Tham chiếu vị trí: Viewport.
+ Cuộn theo trang: Không.
+ Use case: Chat button, cookie banner, header cố định.

- sticky:
+ Vẫn chiếm vị trí trong flow: Có.
+ Tham chiếu vị trí: .
+ Cuộn theo trang: Có.
+ Use case: Sticky header, sticky table header, sidebar.

- Absolute tham chiếu body khi không có parent nào có positive khác static. Tham chiếu đến parent khi parent có positive khác static. Nearest positioned ancestor là phần tử cha gần nhất (tính từ trong ra ngoài) có positive khác static.

Câu A2:
- Bố cục:
+ TH1: 1 hàng, 3 cột bằng nhau.
+ TH2: 3 hàng, 2 cột.
+ TH3: 1 hàng, 3 cột cách đều.
+ TH4: 1 hàng, 3 cột với kt(200px 1fr 200px)
+ TH5: 3 hàng, 3 cột với item cuối nằm ở bên trái hàng cuối.

Phần C:
Câu C1:Flexbox vs Grid: Khi nào dùng gì?
1. Navbar ngang dùng Flexbox. Vì Chỉ điều chỉnh nằm trên một dòng và có thể linh hoạt điều chỉnh.
2. Lưới ảnh Instagram dùng Grid. Vì flex box có thể điều chỉnh linh hoạt nhưng với trường hợp phải biết trước được số ảnh, với việc chưa biết ảnh thì dùng grid.
3. Layout blog: main content + siderbar:Dùng grid. Vì số thành phần nội dung trong nó chưa biết rõ.
4. Footer với 4 cột thông tin:Dùng cả 2 vì với footer chỉ cần chia ra 4 cột và điều đó cả 2 phương pháp đều làm được.
5. Card sản phẩm:Dùng flexbox. Vì ở trong flexbox có margin-top:0 làm cho nút dưới luôn dính đáy phù hợp với yêu cầu dề bài.

Câu C2:Debug Flexbox.
- Lỗi 1: 
+ Card không đều chiều cao do các thẻ card có chiều dài nội dung khác nhau: Chiều dài nội dung dài thì chiều cao lớn hơn, chiều dài nội dung ngắn thì chiều cao nhỏ hơn.
+ Nút btn nằm ngay sau nội dung nên bị đẩy xuống phụ thuộc vào chiều cao của nội dung.
+ Code sau khi sửa:
```css
.card-container 
{ 
    display: flex; 
    flex-wrap: wrap; 
}
.card 
{ 
    width: 30%; 
    margin: 1.5%;
    display: flex;
    flex-direction: column; 
}
.card img 
{ 
    width: 100%; 
}
.card h3 
{ 
    font-size: 18px; 
}
.card p
{
    flex-grow: 1;
}
.card .btn 
{ 
    padding: 10px; 
}
```

- Lỗi 2:
+ container đã khai báo thuộc tính flexbox nhưng vẫn chưa khai báo thuộc tính căn chỉnh, nên item vẫn nằm ở vị trí mặc định là góc trên bên trái.
+ Sau khi sửa lỗi:
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

- Lỗi 3:
Trong flexbox có flex-shrink: 1 làm cho siderbar bị co lại khi nội dung chính quá dài.
+ Sau khi sửa lỗi:
```css
.layout  
{ 
    display: flex; 
}
.sidebar 
{ 
    width: 250px; 
    flex-shrink: 0;
}
.content 
{ 
    flex: 1; 
}
```

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