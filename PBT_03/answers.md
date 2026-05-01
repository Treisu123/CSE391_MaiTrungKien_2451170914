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

Phần B:

Câu B2:

Phần 1:
- Hộp 1 (content-box): chiều rộng thực tế = 300px px (đo từ DevTools)

- Hộp 2 (border-box): chiều rộng thực tế = 250px (đo từ DevTools)

- Content-box chỉ bao quanh vùng nội dung nên khi đặt width thì phần padding và border được cộng thêm phần ngoài, còn border-box thì đặt bao quanh cả vùng nội dung, padding và border nên khi đặt width là đặt tính cả padding và border vào nó. 

Phần 2:

- Các ảnh sidebar1, content1, ads1 là các ảnh sử dụng border-box.

- Các ảnh sidebar2, content2, ads2 là các ảnh không sử dụng border-box.

Câu B3:
/*1*/
p{
    color: blue;             /* Specificity: 0,0,1 */
}

/*2*/
.text{
    color: aqua;              /* Specificity: 0,1,0 */
}

/*3*/                           
.highlight{
    color: gold;     /* Specificity: 0,1,0 */
} 

/*4*/                           
p.text{
    color: royalblue;     /* Specificity: 0,1,1 */
}  

/*5*/                           
.text.highlight{
    color: black;     /* Specificity: 0,2,0 */
}

/*6*/                           
#demo{
    color: brown;     /* Specificity: 1,0,0 */
}

/*7*/                           
#demo.text{
    color: violet;     /* Specificity: 1,1,0 */
}

/*8*/                           
#demo.highlight{
    color: aquamarine;     /* Specificity: 1,1,0 */
}

/*9*/                           
#demo.text.highlight{
    color: green;     /* Specificity: 1,2,0 */
}


/*10*/                           
p#demo.text.highlight{
    color: rosybrown;     /* Specificity: 1,2,1 */
}

2.Element sẽ hiển thị màu hồng nâu. Vì màu này có specificity score cao nhất.

3.Ảnh BT-B3

4.Trong hầu hết trường hợp sẽ thay đổi kết quả. Vì:
+ Không đổi kết quả: Sẽ ưu tiên đến specificity cao nhất trong cùng một origin với trường hợp các role khác điểm specificity.

+ Có đổi: Các rule có cùng mức độ specificity ở mức cao nhất lúc đó role nào được viết sau cùng sẽ thắng.

Phần C:
Câu C1:
1. Tính chiều rộng thực tế của sidebar và content (content-box!)
- Chiều rộng thực tế của sidebar: 342px
- Chiều rộng thực tế của content: 722px

2. Layout bị vỡ do: Tổng kích thước là 1064px lớn hơn 960px của container nên làm cho dòng thừa bị đẩy xuống làm vỡ layout.

3.Đưa ra 2 cách sửa khác nhau (1 cách dùng border-box, 1 cách không dùng)
- Cách 1: Dùng border-box.
```html
*{
    box-sizing:border-box;
}
.container {
    width: 960px;
    margin: 0 auto;
}
.sidebar {
    width: 300px;
    padding: 20px;
    border: 1px solid #ccc;
    float: left;
}
.content {
    width: 660px;
    padding: 30px;
    border: 1px solid #ccc;
    float: left;
}
```

- Cách 2: Không sử dung border-box(Trừ padding, border ra khỏi width):
```html
.container {
    width: 960px;
    margin: 0 auto;
}
.sidebar {
    width: 258px;
    padding: 20px;
    border: 1px solid #ccc;
    float: left;
}
.content {
    width: 598px;
    padding: 30px;
    border: 1px solid #ccc;
    float: left;
}
```

Câu C2: Cascade Puzzle.
1. "Sản phẩm A" có font-size = 20px và color = green.
```html
body { font-size: 16px; color: #333; }
.card .title { font-size: 20px }            /* specificity (0,2,0) */
.container { font-size: 14px; }             /* specificity (0,1,0) */
.card { color: blue; }                      /* specificity (0,1,0) */ 
.highlight { color: green !important; }      /* specificity (0,1,0) + !important*/ 
-> font-size có .card .title thắng do có specificity score (0,2,0) cao nhất và color có .highlight thắng do có !inportant.
```

2. "Mô tả sản phẩm" (p trong card featured) có color = blue.
```html
body { color: #333; }             /* specificity (0,0,1) */
.card { color: blue; }              /* specificity (0,1,0) */
.card p { color: inherit; }         /* specificity (0,1,1) */
```
.card p specificity (0,1,1) cao nhất -> thắng và giá trị là inherit -> leo lên cha .card { color: blue } -> color = blue

3. "Sản phẩm B" (h2) có font-size = 20px và color = blue.
```html
body { font-size: 16px; }           /* specificity (0,0,1) */
.container { font-size: 14px; }     /* specificity (0,1,0) */
.card .title { font-size: 20px; }   /* specificity (0,2,0) */
body { color: #333; }             /* specificity (0,0,1) */
.card { color: blue; }              /* specificity (0,1,0) */
.card .title { font-size: 20px; }   /* specificity (0,2,0) */
```
font-size: .card .title (0,2,0) cao nhất → thắng -> font-size = 20px và color: không rule nào set color trực tiếp -> kế thừa từ .card { color: blue } -> color = blue

4. "Mô tả sản phẩm B" (p.highlight) có color = green.
```html
.card p { color: inherit; }                 /* specificity (0,1,1)*/
.highlight { color: green !important; }     /* specificity (0,1,0) + !important*/
```
.card p specificity (0,1,1) cao hơn .highlight (0,1,0) — bình thường sẽ thắng nhưng .highlight có !important → thắng mọi specificity → color = green.