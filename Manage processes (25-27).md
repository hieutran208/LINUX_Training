**CÁC LỆNH VÀ CÁC THAO TÁC VỚI TIẾN TRÌNH**

*Tiến trình: Tiến trình là các chương trình chạy trên hệ thống. PID là số hiệu tiến trình, dùng để nhận biết các tiến trình*

**A. Các câu lệnh thường dùng để hiển thị thông tin, trạng thái của tiến trình**

1. Các câu lệnh ps thường dùng để kiểm tra thông tin tiến trình
- Hiển thị tất cả các tiến trình trên hệ thống: ps aux (có thể thay bằng 'ps -ef' để kết quả ngắn gọn hơn nhưng sẽ không đầy đủ bằng)
- Hiển thị tiến trình theo tên người dùng: ps –U [tên người dùng]
- Hiển thị tiến trình theo nhóm người dùng: ps –G [nhóm người dùng]
- Hiển thị tiến trình theo PID: ps -ef -p [các pid cần hiển thị]
- Hiển thị các cột cần thiết của tiến trình đang chạy: ps -e -o [tên các cột cần hiển thị]
- Hiển thị các cột cần thiết và sắp xếp theo cách sử dụng: ps –e -o [tên các cột cần hiển thị] --sort=<tiền tố>[cột cần sắp xếp]

(Tiền tố: “+” sắp xếp theo thứ tự tăng dần, “-” sắp xếp theo thứ tự giảm dần) 

2. Lệnh top để hiển thị trạng thái tiến trình
- Giống như ps, top cũng có chức năng hiển thị thông tin tiến trình nhưng nâng cao hơn khi danh sách tiến trình được update liên tục. Ngoài ra có bổ sung thêm nhiều thông số quan trọng như: phân phối CPU, cấp phát bộ nhớ,…giúp dễ dàng theo dõi trạng thái hoạt động của hệ thống, phòng tránh xung đột và bế tắc xảy ra, tối ưu hoá hoạt động của CPU
- Cú pháp: top (Muốn tắt top để về terminal, ta nhấn Ctrl + Z)

3. Lệnh htop để hiển thị trạng thái tiến trình
- Câu lệnh htop cũng hiển thị đầy đủ các thông tin như top nhưng có một số tính năng nâng cao hơn như: dùng màu sắc để hiển thị thông tin hệ thống (CPU, bộ nhớ), phím tắt để quản lý tiến trình thay vì dùng lệnh, tìm kiếm tiến trình trên giao diện,....
- Muốn sử dụng htop ta phải cài về bằng lệnh: sudo apt install htop
- Cú pháp: htop (Muốn tắt htop để về terminal, ta nhấn Ctrl + Z)

**Ý nghĩa các thông số khi hiển thị thông tin, trạng thái tiến trình**
1. Các thông số khi hiển thị thông tin với lệnh ps
![image](https://github.com/user-attachments/assets/f7011a3c-a344-4e69-81d8-2421b5d77459)
