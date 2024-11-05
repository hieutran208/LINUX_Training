**THAO TÁC VỚI TIẾN TRÌNH VÀ TRÌNH QUẢN LÝ CỬA SỔ**

**A. Các câu lệnh thường dùng để theo dõi và quản lý tiến trình**

*Tiến trình: Tiến trình là các chương trình chạy trên hệ thống. PID là số hiệu tiến trình, dùng để nhận biết các tiến trình*

*1. Các câu lệnh ps thường dùng để kiểm tra thông tin tiến trình*

- Hiển thị tất cả các tiến trình trên hệ thống: ps aux (có thể thay bằng 'ps -ef' để kết quả ngắn gọn hơn nhưng sẽ không đầy đủ bằng)
- Hiển thị tiến trình theo tên người dùng: ps –U [tên người dùng]
- Hiển thị tiến trình theo PID: ps -ef -p [các pid cần hiển thị]
- Hiển thị các cột cần thiết của tiến trình đang chạy: ps -e -o [tên các cột cần hiển thị]
- Hiển thị các cột cần thiết và sắp xếp theo cách sử dụng: ps –e -o [tên các cột cần hiển thị] --sort=<tiền tố>[cột cần sắp xếp]

(*Đây cũng là câu lệnh có thể sử dụng để hiển thị tiến trình chiếm nhiều CPU và RAM nhất)

(Tiền tố: “+” sắp xếp theo thứ tự tăng dần, “-” sắp xếp theo thứ tự giảm dần) 

- Tra cứu một tiến trình bất kì dựa trên tên của nó: ps aux | grep <từ khoá>

(*Câu lệnh này có thể dùng để tra cứu PID của tiến trình hoặc để kiểm tra một phần mềm có hoạt động hay không)

*2. Lệnh top/htop để hiển thị trạng thái tiến trình*

a. Lệnh top 
- Giống như ps, top cũng có chức năng hiển thị thông tin tiến trình nhưng nâng cao hơn khi danh sách tiến trình được update liên tục. Ngoài ra có bổ sung thêm nhiều thông số quan trọng như: phân phối CPU, cấp phát bộ nhớ,…giúp dễ dàng theo dõi trạng thái hoạt động của hệ thống, phòng tránh xung đột và bế tắc xảy ra, tối ưu hoá hoạt động của CPU
- Cú pháp: top (Muốn tắt top để về terminal, ta nhấn Ctrl + Z)

b. Lệnh htop
- Câu lệnh htop cũng hiển thị đầy đủ các thông tin như top nhưng có một số tính năng nâng cao hơn như: dùng màu sắc để hiển thị thông tin hệ thống (CPU, RAM, swap), phím tắt để quản lý tiến trình,....
- Muốn sử dụng htop ta phải cài về bằng lệnh: sudo apt install htop
- Cú pháp: htop (Muốn tắt htop để về terminal, ta nhấn Ctrl + Z)

*3. Sử dụng lệnh kill để dừng tiến trình*
- Thông thường, để kết thúc một tiến trình ta dùng cú pháp: *kill <PID tiến trình>*. Đây là cú pháp mặc định, gọi là sigterm
- 
**B. Ý nghĩa các thông số khi theo dõi tiến trình**

*1. Các thông số tiến trình khi hiển thị thông tin với lệnh ps*
![image](https://github.com/user-attachments/assets/66a42ee3-7613-474a-a5e4-7b5c717ad806)

Ý nghĩa các trường trong bảng hiển thị thông tin tiến trình:
- USER: Tên chủ sở hữu tác vụ
- PID: Số hiệu (ID định danh) của tiến trình
- %CPU: % sử dụng CPU của tiến trình
- %MEM: % sử dụng bộ nhớ của tiến trình
- VSZ: Kích thước bộ nhớ ảo sử dụng bởi tiến trình
- RSS: Kích thước bộ nhớ thực sử dụng bởi tiến trình
- TYY: Tên thiết bị đầu cuối điều khiển, nếu không có sẽ thấy “?”
- STAT: Trạng thái của tiến trình (S: sleeping; Ss: là tiến trình lãnh đạo phiên, ở trạng thái sleeping; I: rảnh rỗi; R: đang chạy)
- START: Thời gian bắt đầu của tiến trình 
- TIME: Tổng thời gian sử dụng CPU của tiến trình
- COMMAND: Tên tiến trình (Câu lệnh thực hiện)

*2. Các thông số khi hiển thị thông tin với lệnh top*

a. Các thông số hệ thống
![image](https://github.com/user-attachments/assets/d2311744-2f17-4262-87a7-b26bc961fb0d)

Ý nghĩa các thông số hệ thống tại các dòng trong phần khoanh đỏ:

- Dòng đầu tiên lần lượt hiển thị các thông số về hệ thống:  
  - Thời gian hiện tại của hệ thống; 
  - Thời gian uptime: Thời gian chương trình bắt đầu chạy; 
  - Số lượng người dùng đã log in
  - Mức độ tải trung bình của CPU  trong 1 phút, 5 phút và 15 phút qua.

- Dòng thứ 2 lần lượt hiển thị tổng số tác vụ và số tác vụ theo trạng thái: 
  - Tổng số tác vụ trên máy chủ
  - Số tác vụ đang chạy
  - Số tác vụ đang trong trạng thái ngủ
  - Số tác vụ ở trạng thái dừng
  - Số tác vụ ở trạng thái zombie (đã dừng nhưng chưa được giải phóng)

- Dòng thứ 3 hiển thị phân phối CPU lần lượt như sau: 
  - us: Phần trăm phân phối cho tiến trình người dùng
  - sy: Phần trăm phân phối cho tiến trình hệ thống 
  - ni: Phần trăm phân phối cho tiến trình có mức độ ưu tiên thấp
  - id: Phần trăm CPU đang rảnh
  - wa: Phần trăm CPU để đợi khi các tiến trình I/O đang xử lí (wa)
  - hi: Phần trăm CPU để xử lí các gián đoạn phần cứng
  - si: Phần trăm CPU để xử lí các gián đoạn phần mềm
  - st: Phần trăm CPU do máy ảo sử dụng 

- Dòng thứ 4 lần lượt hiển thị các thông số về bộ nhớ vật lý (RAM) :
  - Tổng dung lượng RAM cài đặt trên hệ thống
  - Bộ nhớ trống
  - Bộ nhớ đã sử dụng
  - Dung lượng đang được dùng làm bộ đệm (buffer) và bộ nhớ cache

- Dòng thứ 5 lần lượt hiển thị các thông số về swap space (Swap là RAM ảo, được sử dụng khi bộ nhớ vật lý (RAM) bị đầy):
  - Tổng swap có sẵn (kB)
  - Tổng swap còn trống
  - Tổng swap đã sử dụng
  - Bộ nhớ khả dụng

b. Các thông số tiến trình
![image](https://github.com/user-attachments/assets/900f7e26-a522-4ae6-901a-e7d27fe7dd81)

Ý nghĩa các trường trong bảng hiển thị thông tin tiến trình:
- PID: Số hiệu (ID định danh) của tiến trình
- USER: Tên chủ sở hữu tác vụ
- PR: Mức độ ưu tiên (20 là mức mặc định; 0 là mức cao nhất; rt là mức đặc biệt dành cho các tiến trình real-time)
- NI: Mức độ nice (PR = 20 + NI)
- VIRT: Kích thước bộ nhớ ảo sử dụng bởi tiến trình
- RES: Kích thước bộ nhớ thực sử dụng bởi tiến trình
- SHR: Kích thước bộ nhớ có thể chia sẻ với các tiến trình khác
- S: Trạng thái của tiến trình (S: sleeping; Ss: là tiến trình lãnh đạo phiên, ở trạng thái sleeping; I: rảnh rỗi; R: đang chạy)
- %CPU: % sử dụng CPU của tiến trình
- %MEM: % sử dụng bộ nhớ của tiến trình
- TIME+: Thời gian tiến trình đã được chạy
- COMMAND: Tên tiến trình (Câu lệnh thực hiện)

=> Nếu mục đích sử dụng là để theo dõi trạng thái hoạt động của toàn hệ thống thì sử dụng lệnh top. Nếu mục đích sử dụng là trích xuất các thông tin cụ thể của tiến trình thì sử dụng lệnh ps 

*3. Các thông số khi hiển thị thông tin với lệnh htop*
![image](https://github.com/user-attachments/assets/1892c745-4518-4e8d-89bf-5e9bbef241de)

Về cơ bản, tên các cột hiển thị thông tin tiến trình sẽ giống với lệnh top. Tuy nhiên có chút khác biệt khi có một số phần thông tin hệ thống (CPU, RAM, SWAP) được hiển thị dưới dạng thanh ngang có màu sắc:
- CPU Usage: Hiển thị nhiều thanh ngang màu sắc giúp dễ dàng theo dõi mức độ sử dụng CPU (màu xanh là phần CPU đang làm việc với các tác vụ người dùng, màu đỏ là phần CPU đang làm việc với các tác vụ hệ thống, màu xám là phần CPU ở trạng thái rảnh rỗi). Nếu có nhiều nhân CPU thì mỗi nhân sẽ có 1 thanh riêng biệt
- Memory Usage: Cung cấp thông tin về bộ nhớ RAM và swap (Xanh: Bộ nhớ đang được sử dụng cho các tiến trình bình thường; Đỏ: Bộ nhớ đang sử dụng cho các tiến trình hệ thống; Vàng: Bộ nhớ dùng cho bộ nhớ đệm (buffer) và bộ nhớ cache.)

*4. Ý nghĩa chỉ số load average*
- Load Average (trung bình tải) là chỉ số đo mức độ tải của hệ thống trong một khoảng thời gian nhất định. Nó cho biết số lượng trung bình các tiến trình đang ở trạng thái có thể chạy trong một khoảng thời gian cụ thể. Khi sử dụng câu lệnh top/htop để theo dõi tiến trình, load average được hiển thị dưới dạng 3 số liên tiếp nhau, biểu thị tải trong lần lượt 1, 5 và 15 phút vừa qua
- Ý nghĩa thông số:
  - Load Average = 1 có nghĩa là hệ thống đang sử dụng đầy đủ tài nguyên của CPU
  - Load Average > 1 có nghĩa là có nhiều tiến trình đang chờ CPU, gây ra tình trạng quá tải.
  - Load Average < 1 cho thấy hệ thống có tài nguyên dự phòng và không bị quá tải.

**C. Byobu và cách sử dụng byobu**


