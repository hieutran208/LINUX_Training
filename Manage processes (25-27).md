**CÁC LỆNH VÀ CÁC THAO TÁC QUẢN LÝ TIẾN TRÌNH**

*Tiến trình: Tiến trình là các chương trình chạy trên hệ thống. PID là số hiệu tiến trình, dùng để nhận biết các tiến trình*

**A. Hiển thị thông tin tiến trình với lệnh ps**

1. Các câu lệnh ps thường dùng để kiểm tra thông tin tiến trình

- Hiển thị tất cả các tiến trình trên hệ thống: ps aux (có thể thay bằng 'ps -ef' để kết quả ngắn gọn hơn nhưng sẽ không đầy đủ bằng)
- Hiển thị tiến trình theo tên người dùng: ps –U [tên người dùng]
- Hiển thị tiến trình theo nhóm người dùng: ps –G [nhóm người dùng]
- Hiển thị tiến trình theo PID: ps -ef -p [các pid cần hiển thị]
- Hiển thị các cột cần thiết của tiến trình đang chạy: ps -e -o [tên các cột cần hiển thị]
- Hiển thị các cột cần thiết và sắp xếp theo cách sử dụng: ps –e -o [tên các cột cần hiển thị] --sort=<tiền tố>[cột cần sắp xếp]
                  (Tiền tố: “+” sắp xếp theo thứ tự tăng dần, “-” sắp xếp theo thứ tự giảm dần) 

