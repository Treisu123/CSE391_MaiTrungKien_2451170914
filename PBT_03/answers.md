Phần A:KIỂM TRA ĐỌC HIỂU
Câu A1: 3 Cách nhúng CSS
- Inline:
VD:
```html
<h1 style="color: #2563eb; font-size: 32px;">Tiêu đề</h1>
```
Ưu điểm: 
+ Không cần tạo và upload một file riêng như trong kiểu external style.
+ Có thể dễ dàng và nhanh chóng chèn các quy tắc CSS vào trang HTML. Đó là lý do tại sao phương pháp này hữu ích để kiểm tra hoặc xem trước các thay đổi và thực hiện sửa lỗi nhanh trên trang web.
Nhược điểm: 
+ Việc thêm các quy tắc CSS vào từng phần tử HTML rất tốn thời gian và làm cho cấu trúc HTML trở nên lộn xộn.
+ Việc tạo style cho nhiều phần tử có thể ảnh hưởng đến kích thước trang và thời gian tải xuống.
Nên sử dụng khi:
- Email HTML
- Trang web cũ hơn
- Nội dung CMS (ví dụ WordPress, Drupal)
- Nội dung động (tức là HTML được tạo hoặc thay đổi bởi JavaScript) 

-Internal:
VD:
```html
<head>
    <style>
        h1 { color: #2563eb; font-size: 32px; }
    </style>
</head>
```
Ưu điểm:
+ Dùng được class, ID, selector đầy đủ áp dụng style cho nhiều element cùng lúc.
+ Chỉ cần 1 file HTML duy nhất, không cần upload hay quản lý thêm file CSS riêng.
Nhược điểm: Việc thêm code vào file HTML có thể làm tăng kích thước trang và thời gian tải.
Nên sử dụng khi:
- Trang web đơn lẻ, chỉ dùng cho một trang web.
- Email phức tạp cần selector.
- Property cho một trang web duy nhất.
-External:
VD:
```html
<!--Đường liên kết đến style.css-->
<head>
    <link rel="stylesheet" href="style.css">
</head>

/*style.css*/
h1 { color: #2563eb; font-size: 32px; }
```
Ưu điểm:
+ code CSS nằm trong một file riêng, các file HTML của bạn sẽ có cấu trúc gọn gàng hơn và kích thước nhỏ hơn.
+ Bạn có thể dùng cùng một file .css cho nhiều trang.
Nhược điểm:
+ Các trang có thể không hiển thị đúng cho đến khi file CSS ngoài được tải xong.
+ Việc upload hoặc liên kết nhiều file CSS có thể làm tăng thời gian tải trang web.
Nên sử dụng khi:
+ Khi sử dụng một style cho nhiều trang web.
+ Khi muốn có thể tái sử dụng.
+ Khi muốn tối ưu code

- Khi đồng thời áp dụng cả 3 cách css đồng thời thì cách nào viết thì inline sẽ thắng. Vì code sẽ được đọc tuần tự từ trên xuống dưới và cái nào được đọc đến cuối dùng sẽ được thực thi lên màn hình(ghi đè lên các cách còn lại).

Câu A2:CSS Selectors — Dự đoán kết quả.
1. h1 -> Chọn: Các thẻ h1 có trong file.
2. .price -> Chọn: Những thẻ có class là price.
3. #app header -> Chọn: Thẻ header nằm bên trong thẻ có id là app.
4. nav a:first-child -> Chọn: Thẻ con a nằm trong nav đồng thời là thẻ a đầu tiên.
5. .product.featured h2 -> Chọn: Thẻ h2 nằm trong thẻ có class là featured, đồng thời thẻ có class là featured nằm trong thẻ có class là product.
6. article > p -> Chọn: Thẻ p là con trực tiếp của thẻ article.
7. a[href="/"] -> Chọn: Thẻ a có giá trị href="/".
8. .top-bar.dark h1 -> Chọn thẻ h1 nằm trong thẻ có class là dark, đồng thời thẻ có class là dark nằm trong thẻ có class là top-bar.

Câu A3:Box Model — Tính toán kích thước
- TH1:
+ Chiều rộng hiển thị: 450px
+ Không gian chiếm trang: 470px

- TH2:
+ Chiều rộng hiển thị: 400px
+ Kích thước content thực tế: 350px
+ Không gian chiếm trang: 420px

- TH3:
+ Khoảng cách giữa box-a và box-b: 40px. Vì marin dọc giữa 2 block element gộp lại sẽ lấy cái lớn hơn.

Nâng cao: Nếu .box-a có margin-bottom: -10px và .box-b có margin-top: 40px, khoảng cách = 30px.

Câu A4:Specificity (Độ ưu tiên).
1. Specificity score
A(0, 0, 1)
B(0, 0, 1)
C(0, 1, 0)
D(0, 0, 2)
2. Element sẽ hiện màu đỏ. Vì C có điểm độ ưu tiên lớn hơn tất cả các role còn lại.
3. Nếu thêm <p class="price" id="main-price" style="color: orange;">, element có màu Cam.
4. Nếu Rule A thêm !important, element có màu đen. Vì !important có độ ưu tiên cao nhất, vượt qua cả specificity.

Phần B:
Câu B1: Style trang Profile
1. Element selector
body{}
header{}

2. Class selector
.table{}
.Footer{}

3. Id selector
#Menu{}
#Skill{}

4.Descendant Selector + Child Combinator
#Menu ul > li a {}
#Skill .Table th, #Skill .Table td {}
#Skill .Table thead th {}
#Skill .Table tbody tr:nth-child(even) {}
#Skill .Table tbody tr:hover {}

5.Pseudo-class Selector
#Menu ul > li a:hover {}   
#Menu ul > li a.active {}       
#Skill .Table tbody tr:nth-child(even) {}
#Skill .Table tbody tr:hover {}
Phần C:
Câu C1: