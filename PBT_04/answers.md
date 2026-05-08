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

