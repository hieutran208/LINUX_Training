**QUẢN LÝ FILE LOG VÀ TÁC VỤ TỰ ĐỘNG**

**A. Sử dụng file log trong hệ thống**

*1. Khái niệm và vị trí của file log trong hệ thống*
- File log của hệ thống là những file văn bản ghi lại các các sự kiện quan trọng của hệ thống và các chương trình trên máy tính (có người dùng đăng nhập, có dịch vụ gặp lỗi, hệ thống khởi động hoặc tắt,...). Những thông tin này giúp người quản trị hệ thống theo dõi và kịp thời khắc phục các sự cố xảy ra.
- Vị trí của file log trong hệ thống: các file log quan trọng của hệ thống và các ứng dụng thường được lưu trong thư mục /var/log/.
  - /var/log/syslog: Lưu trữ các sự kiện chung của hệ thống (thông tin khởi động, thông báo của hệ thống, các lỗi trong quá trình hoạt động,...)
  - /var/log/auth.log: Lưu trữ các sự kiện liên quan đến xác thực và quyền truy cập người dùng. Thông tin trong file này giúp theo dõi quá trình đăng nhập và đăng xuất của người dùng.
  - /var/log/kern.log: Lưu các thông báo từ kernel (thường liên quan đến các sự kiện phần cứng hoặc toàn hệ thống.)
  - /var/log/dmesg: Chứa các thông báo của hệ thống trong quá trình khởi động. 
  - /var/log/nginx: Chứa các sự kiện liên quan đến hoạt động của ứng dụng nginx

*2. Rotate log*
- Rotate log: khi file log đã đạt đến một kích thước nhất định, hệ thống sẽ tự động tạo file log mới và lưu trữ file log cũ dưới dạng có thể nén lại (để tiết kiệm dung lượng) 
- Tác dụng:
  - Tiết kiệm dung lượng ổ đĩa
  - Dễ quản lý: Chia nhỏ các file log giúp việc tìm kiếm và phân tích thông tin trở nên dễ dàng hơn.
  - Bảo mật: lưu trữ các file log cũ giúp tránh bị lộ dữ liệu hệ thống nếu xảy ra lỗi.
- Cách rotate log: Sử dụng công cụ logrotation. Với công cụ này, ta chủ yếu thực hiện cấu hình trong các file/thư mục:
  - /etc/logrotate.conf: File cấu hình chính của logrotate để thiết lập các tham số chung.
  - /etc/logrotate.d/: Thư mục chứa các file cấu hình riêng biệt cho từng ứng dụng hoặc dịch vụ (ví dụ: nginx, apache, syslog). 
  
