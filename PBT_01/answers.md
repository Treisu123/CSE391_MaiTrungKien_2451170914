Câu A1:HTTP & Browser.
1.
    1 Kiểm tra cache cục bộ:Trình duyệt hoặc hệ điều hành kiểm tra cache cục bộ để tìm 
    địa chỉ ip của shoppee Nếu có thí sử dụng nay ip này. Nếu không có trong cache,  
    trình duyệt gửi yêu cầu đến DNS Resolver.
    2 Tra cứu DNS:
     Resolver kiểm tra cache của nó - Nếu không có trong cache, Resolver gửi truy vấn đến 
    Root DNS Server, yêu cầu thông tin về TLD .vn. 
     Resolver kiểm tra cache của nó - Nếu không có trong cache, Resolver gửi truy vấn đến 
    Root DNS Server, yêu cầu thông tin về TLD .vn. 
     Resolver hỏi TLD DNS, và TLD DNS chỉ định Authoritative DNS Server cho shoppee.vn.
     Authoritative DNS trả về địa chỉ IP, ví dụ: 192.0.2.1. 
    3 Phân giải DNS: Resolver nhận IP (192.0.2.1) và lưu vào cache với TTL (giả sử 3600 giây)
    4 Kết nối: Trình duyệt dùng IP để gửi yêu cầu HTTP đến máy chủ web, tải nội dung shoppee.vn.
    5 Server xử lý request: Máy chủ Shopee nhận yêu cầu, xử lý backend, truy vấn dữ liệu cần thiết
    rồi trả về HTML/CSS/JS.
    6 Từ dữ liệu HTML đã nhận từ server Browser tạo ra DOM và Styles được load và parsed (phân tích) 
    để tạo ra CSSOM.
    7 Dựa trên DOM và CSSOM ở trên, browser dựng lên một rendering tree.
    8 Với mỗi thành phần render tree, các toạ độ tương ứng cũng được tính toán.
    9 Cuối cùng, nội dung trang web được hiển thị lên màn hình, quá trình này.
    -Nguồn:01_introduction_html_universe.md
2. Ảnh lưu trong screenshots/screanshot.

Câu A2:Semantic HTML
<div class="header">
    <div class="logo">ShopTLU</div>
    <div class="menu">
        <div><a href="/">Trang chủ</a></div>
        <div><a href="/products">Sản phẩm</a></div>
    </div>
</div>
<div class="main">
    <div class="product">
        <div class="title">iPhone 16 Pro</div>
        <div class="price">25.990.000đ</div>
        <div class="image"><img src="iphone.jpg"></div>
    </div>
</div>
<div class="footer">© 2026 ShopTLU</div>

-Khi sử dụng toàn thẻ div như vậy không đúng ngữ nghĩa làm cho gg khó chia
ra được mức độ ưu tiên của từng mục dẫn đến bị gg đánh giá seo thấp.

-Các lỗi sematic hiện có:
div.header thay vì sử dụng thẻ header.
div.menu thay vì sử dụng thẻ nav.
<div><a href="">.... thay vì sử dụng thẻ li để tạo Danh sách dẫn tới đường liên kết.
div.main thay vì sử dụng thẻ main.
div.product thay vì sử dụng thẻ article
div.title thay vì sử dụng thẻ h1,h2...
div.price thay vì p.price.
div.footer thay vì thẻ footer.

-Sau khi sửa lại code:
<header class="header">
    <div class="logo">ShopTLU</div>
    <nav class="menu">
        <ul>
            <li><a href="/">Trang chủ</a></div>
            <li><a href="/products">Sản phẩm</a></div>
        </ul>
    </nav>
</header>
<main class="main">
    <article class="product">
        <h1 class="title">iPhone 16 Pro</h1>
        <p class="price">25.990.000đ</p>
        <img src="iphone.jpg">
    </article>
</main>
<footer class="footer">© 2026 ShopTLU</footer>

Câu A3:Block vs Inline
<div>Hộp 1</div>
<span>Text A</span>
<span>Text B</span>
<div>Hộp 2</div>
<span>Text C</span>
<strong>Text D</strong>
<div>Hộp 3</div>

Hộp 1
Text A Text B
Hộp 2
Text C Text D (Text D in đậm)
Hộp 3

- Hộp 1 nằm trong thẻ div là một block -> chiếm hết 1 dòng.
- Text A Text B trong thẻ span là inline-> Chiếm nội dung-> Nằm cùng 1 dòng.
- Hộp 2 nằm trong thẻ div là một block -> Chiếm hết một dòng.
- Text C Text D trong thẻ span và strong là inline -> chiếm nội dung -> Nằm cùng một dòng.
- Hộp 3 nằm trong thẻ div là một block -> Chiếm hết 1 dòng.

Câu A4:
thẻ thead là phần tiêu đề cột của bảng.
thẻ tbody là nội dung chính của bảng.
thẻ tfoot là phần tổng kết của bảng.

-Tại sao không nên dùng table để tạo layout trang web:
 Bảng biểu không thân thiện với khả năng truy cập: Phần lớn công cụ tìm kiếm đọc trang web
dựa trên cấu trúc HTML. Khi dùng bảng để dàn trang, công cụ tìm kiếm sẽ khó hiểu và khó 
phân tích bố cục hơn.
 Bảng biểu khó xử lý: Khi lồng nhiều bảng vào nhau, mã nguồn trở nên khó quản lý. 
Sau một thời gian, nếu muốn chỉnh sửa hay cập nhật, lập trình viên sẽ gặp nhiều khó khăn 
hơn trong việc bảo trì và gỡ lỗi.
 Bảng biểu thiếu linh hoạt: Khi dùng bảng với chiều rộng cố định để tạo bố cục, giao diện
sẽ trở nên cứng nhắc, không thích ứng tốt với nhiều kích thước màn hình khác nhau, đồng thời 
có thể làm trang tải chậm hơn. Bố cục linh hoạt luôn hiển thị tốt hơn trên mọi thiết bị.
 Bảng biểu gây hại cho SEO: Nhiều lập trình viên đặt thanh điều hướng ở bên trái và nội dung ở bên phải.
Nếu dùng bảng để dàn trang, công cụ tìm kiếm có thể phải xử lý nội dung theo thứ tự không tối ưu, 
khiến cấu trúc trang kém rõ ràng và ảnh hưởng tiêu cực đến SEO.
 Bảng biểu không phải lúc nào cũng in tốt: Khi in một bố cục dùng bảng, máy in có thể tự điều chỉnh giao diện 
vì chiều rộng bảng quá lớn. Kết quả là nội dung có thể bị cắt bớt hoặc đẩy sang trang sau, gây rối và khó đọc.
