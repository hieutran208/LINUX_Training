**CÁC LỆNH VÀ CÁC THAO TÁC QUẢN LÝ TIẾN TRÌNH**

*Tiến trình: Tiến trình là các chương trình chạy trên hệ thống. PID là số hiệu tiến trình, dùng để nhận biết các tiến trình*

**A. Hiển thị thông tin tiến trình với lệnh ps**

1. Lệnh ps và các option liên quan để kiểm tra tiến trình

- Hiển thị tất cả các tiến trình trên hệ thống: ps aux (có thể thay bằng 'ps -ef' để kết quả ngắn gọn hơn nhưng sẽ không đầy đủ bằng)
- Hiển thị tiến trình theo tên người dùng: ps –U [tên người dùng]
- Hiển thị tiến trình theo nhóm người dùng: ps –G [nhóm người dùng]
- Hiển thị tiến trình theo PID: ps -ef -p [các pid cần hiển thị]
