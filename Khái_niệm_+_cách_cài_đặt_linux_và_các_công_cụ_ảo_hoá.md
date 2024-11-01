**Khái niệm Linux và các Distro Linux**
- Linux là một hệ điều hành mã nguồn mở, nghĩa là người dùng có thể tuỳ chỉnh hệ điều hành cho phù hợp với nhu cầu sử dụng. Linux nổi tiếng với tính ổn định, bảo mật và khả năng tùy biến cao. So với Windows hay MacOS, HĐH Linux có phần khó thao tác với người dùng thông thường do sử dụng giao diện dòng lệnh. Vì vậy, Linux chủ yếu được sử dụng trong các môi trường như: máy chủ, máy trạm hay các hệ thống phát triển phần mềm.
- Distro Linux là các phiên bản của hệ điều hành Linux. Mỗi distro có thể có cách cài đặt, quản lý gói và giao diện riêng để hướng tới một nhóm đối tượng với nhu cầu sử dụng khác nhau. Có một số distro phổ biến như: Urbuntu (dễ sử dụng, phổ biến cho người mới bắt đầu và các máy tính để bàn); CentOS (dựa trên Red Hat Enterprise Linux, thường được sử dụng cho các máy chủ); Fedora ( tích hợp các công nghệ mới nhất và phù hợp cho người yêu thích thử nghiệm);....

**Cài đặt các công cụ ảo hóa trên Windows Desktop và thiết lập máy ảo Urbuntu (lấy ví dụ với VMWare)**

*Cách cài đặt máy ảo VMWare*
- Truy cập trang web của VMware và tải xuống phiên bản mới nhất của VMware Workstation Player.
- Chạy tệp cài đặt và làm theo các bước trên màn hình để hoàn tất cài đặt

*Cách thiết lập máy ảo Urbuntu bản Server trên VMWare*: Linux bản Server được thiết kế để chạy trên máy chủ, được tối ưu hóa để cho hiệu suất, bảo mật và khả năng phục vụ nhiều người dùng cùng lúc
- Tải xuống file ISO của Ubuntu Server từ trang chính thức.
- Khởi tạo máy ảo: Mở VMware Workstation Player và nhấn vào "Create a New Virtual Machine" để tạo máy ảo mới.
- Chọn File ISO: Trong bước này, chọn "Installer disc image file (iso)", sau đó nhấn vào "Browse" và chọn file ISO của Ubuntu Server vừa tải về.
- Chọn Hệ Điều Hành, nhập tên cho máy ảo và chọn vị trí lưu trữ máy ảo (thư mục nơi máy ảo sẽ được lưu).
- Cấu Hình Bộ Nhớ: Chọn lượng RAM mà máy ảo sẽ sử dụng (Tối thiểu là 512 MB, nhưng 1 GB hoặc nhiều hơn là lý tưởng)
- Cấu Hình Đĩa Cứng Ảo: Chọn "Create a new virtual disk", sau đó chọn "Allocate all disk space now" để phân bổ toàn bộ dung lượng đĩa hoặc "Split virtual disk into multiple files" nếu muốn chia dung lượng đĩa để tiết kiệm không gian bộ nhớ. Chọn kích thước đĩa cứng (nên có ít nhất 10 GB). Nhấn "Next" và sau đó nhấn "Finish" để tạo máy ảo.
- Khởi chạy Máy Ảo: Chọn máy ảo mới tạo để khởi động từ file ISO. Khi màn hình cài đặt của Ubuntu xuất hiện, thiết lập các tiêu chí: cấu hình mạng, thông tin người dùng,...để hoàn tất cài đặt. Sau đó khời động lại để Urbuntu bắt đầu được khởi chạy

*Cách cài đặt Urbuntu bản Desktop*: Linux bản Desktop được thiết kế để sử dụng trên máy tính cá nhân, phục vụ nhu cầu sử dụng hàng ngày của người dùng như lướt web, văn phòng, đồ họa, và giải trí.
- Tải xuống file ISO của Ubuntu Server từ trang chính thức.
