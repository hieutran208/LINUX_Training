**THAO TÁC VỚI TIẾN TRÌNH VÀ TRÌNH QUẢN LÝ CỬA SỔ**

*Tiến trình: Tiến trình là các chương trình chạy trên hệ thống. PID là số hiệu tiến trình, dùng để nhận biết các tiến trình*

**A. Các câu lệnh thường dùng để hiển thị thông tin, trạng thái của tiến trình**

*1. Các câu lệnh ps thường dùng để kiểm tra thông tin tiến trình*

- Hiển thị tất cả các tiến trình trên hệ thống: ps aux (có thể thay bằng 'ps -ef' để kết quả ngắn gọn hơn nhưng sẽ không đầy đủ bằng)
- Hiển thị tiến trình theo tên người dùng: ps –U [tên người dùng]
- Hiển thị tiến trình theo nhóm người dùng: ps –G [nhóm người dùng]
- Hiển thị tiến trình theo PID: ps -ef -p [các pid cần hiển thị]
- Hiển thị các cột cần thiết của tiến trình đang chạy: ps -e -o [tên các cột cần hiển thị]
- Hiển thị các cột cần thiết và sắp xếp theo cách sử dụng: ps –e -o [tên các cột cần hiển thị] --sort=<tiền tố>[cột cần sắp xếp]

(*Đây cũng là câu lệnh có thể sử dụng để hiển thị tiến trình chiếm nhiều CPU và RAM nhất)

(Tiền tố: “+” sắp xếp theo thứ tự tăng dần, “-” sắp xếp theo thứ tự giảm dần) 

- Kiểm tra/tra cứu một tiến trình bất kì dựa trên tên của nó: ps aux | grep <từ khoá>

(*Câu lệnh này có thể dùng để tra cứu PID của tiến trình, kiểm tra một tiến trình có hoạt động hay không)

*2. Lệnh top để hiển thị trạng thái tiến trình*

- Giống như ps, top cũng có chức năng hiển thị thông tin tiến trình nhưng nâng cao hơn khi danh sách tiến trình được update liên tục. Ngoài ra có bổ sung thêm nhiều thông số quan trọng như: phân phối CPU, cấp phát bộ nhớ,…giúp dễ dàng theo dõi trạng thái hoạt động của hệ thống, phòng tránh xung đột và bế tắc xảy ra, tối ưu hoá hoạt động của CPU
- Cú pháp: top (Muốn tắt top để về terminal, ta nhấn Ctrl + Z)

*3. Lệnh htop để hiển thị trạng thái tiến trình*

- Câu lệnh htop cũng hiển thị đầy đủ các thông tin như top nhưng có một số tính năng nâng cao hơn như: dùng màu sắc để hiển thị thông tin hệ thống (CPU, bộ nhớ), phím tắt để quản lý tiến trình thay vì dùng lệnh, tìm kiếm tiến trình trên giao diện,....
- Muốn sử dụng htop ta phải cài về bằng lệnh: sudo apt install htop
- Cú pháp: htop (Muốn tắt htop để về terminal, ta nhấn Ctrl + Z)

**B. Ý nghĩa các thông số khi hiển thị thông tin, trạng thái tiến trình**

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

b. Các thông số tiến trình
![image](https://github.com/user-attachments/assets/900f7e26-a522-4ae6-901a-e7d27fe7dd81)

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

**C. Quản lý tiến trình**


