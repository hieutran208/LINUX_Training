**Khái niệm Linux và các Distro Linux**

*Linux* là một hệ điều hành mã nguồn mở, nghĩa là người dùng có thể tuỳ chỉnh hệ điều hành cho phù hợp với nhu cầu sử dụng. Linux nổi tiếng với tính ổn định, bảo mật và khả năng tùy biến cao. So với Windows hay MacOS, HĐH Linux có phần khó thao tác với người dùng thông thường do sử dụng giao diện dòng lệnh. Vì vậy, Linux chủ yếu được sử dụng trong các môi trường như: máy chủ, máy trạm hay các hệ thống phát triển phần mềm.

*Distro Linux* là các phiên bản của HĐH Linux. Mỗi distro có cách cài đặt, quản lý gói và giao diện riêng để hướng tới một nhóm đối tượng có nhu cầu khác nhau. Các distro linux phổ biến hiện nay được chia thành 4 nhóm chính:

- Nhóm 1: Arch, Gentoo và Slackware: nhắm vào người dùng am hiểu Linux. Do đó, phần lớn các phương thức xây dựng, cũng như cấu hình của hệ thống được thực hiện qua dòng lệnh.
- Nhóm 2: Debian, Fedora: nhắm vào người am hiểu về hệ thống nhưng chưa thực sự hiểu về Linux. Vì vậy, distro sẽ cung cấp cho họ nhiều công cụ hơn. Nhóm này phù hợp với người dùng mới bắt đầu sử dụng Linux. 
- Nhóm 3: Centos, RHEL, SUSE EL: nhắm vào thị trường máy chủ, doanh nghiệp, cơ quan… Vì chúng có sự ổn định cao, thời gian ra phiên bản mới lâu, khoảng 3 – 5 năm tùy distrolinux. Ngoài ra, còn có dịch vụ hỗ trợ thương mại cho công ty, hướng dẫn sử dụng sản phẩm.
- Nhóm 4: Ubuntu, Open SUSE, Linux Mint: người mới bắt đầu dùng Linux và người dùng cuối. Đặc tính của chúng là phát triển trong thời gian ngắn, ứng dụng các công nghệ mới liên tục, nhiều công cụ đồ họa để thiết kế và cấu hình hệ thống theo nhu cầu sử dụng. Nhóm này cũng rất thân thiện với người dùng mới làm quen Linux.

**Cài đặt công cụ ảo hóa (VMWare) và cài đặt Urbuntu**

*Cách cài đặt máy ảo VMWare trên Window Desktop*
- Truy cập trang web của VMware và tải xuống phiên bản mới nhất của VMware Workstation Player.
- Chạy tệp cài đặt và làm theo các bước trên màn hình để hoàn tất cài đặt

*Cách cài đặt máy ảo VMWare trên Urbuntu*
- Cập nhật gói: sudo apt update
- Tải tệp cài đặt VMWare: wget -O VMware-Player.bundle "https://www.vmware.com/go/getplayer-linux"
- Cấp quyền thực thi cho tệp cài đặt: chmod +x VMware-Player.bundle
- Cài đặt VMware Workstation Player: sudo ./VMware-Player.bundle

*Cách cài đặt và thiết lập máy ảo Urbuntu bản Server trên VMWare (tương tự với bản Desktop trên VMWare)*: Linux bản Server được thiết kế để chạy trên máy chủ, được tối ưu hóa để cho hiệu suất, bảo mật và khả năng phục vụ nhiều người dùng cùng lúc
- Tải xuống file ISO của Ubuntu Server từ trang chính thức: https://ubuntu.com/download/server
- Khởi tạo máy ảo: Mở VMware Workstation Player và nhấn vào "Create a New Virtual Machine" để tạo máy ảo mới.
- Chọn File ISO: chọn "Installer disc image file (iso)", sau đó nhấn vào "Browse" và chọn file ISO của Ubuntu Server vừa tải về.
- Chọn Hệ Điều Hành, nhập tên cho máy ảo và chọn vị trí lưu trữ máy ảo (thư mục nơi máy ảo sẽ được lưu).
- Cấu Hình Bộ Nhớ: Chọn lượng RAM mà máy ảo sẽ sử dụng (Tối thiểu là 512 MB, nhưng 1 GB hoặc nhiều hơn là lý tưởng)
- Cấu Hình Đĩa Cứng Ảo: Chọn "Create a new virtual disk", sau đó chọn "Allocate all disk space now" để phân bổ toàn bộ dung lượng đĩa hoặc "Split virtual disk into multiple files" nếu muốn chia dung lượng đĩa để tiết kiệm không gian bộ nhớ. Chọn kích thước đĩa cứng (nên có ít nhất 10 GB). Nhấn "Next" và sau đó nhấn "Finish" để tạo máy ảo.
- Khởi chạy Máy Ảo: Chọn máy ảo mới tạo để khởi động từ file ISO. Khi màn hình cài đặt của Ubuntu xuất hiện, thiết lập các tiêu chí: cấu hình mạng, thông tin người dùng,...rồi chờ Urbuntu hoàn tất cài đặt. Sau đó tiến hành restart để Urbuntu bắt đầu được khởi chạy

*Cách cài đặt và thiết lập Urbuntu bản Desktop về máy thực*: Linux bản Desktop được thiết kế để sử dụng trên máy tính cá nhân, phục vụ nhu cầu sử dụng hàng ngày của người dùng như lướt web, văn phòng, đồ họa, và giải trí.
- Tải xuống file ISO của Ubuntu Desktop từ trang chính thức: https://ubuntu.com/download/desktop
- 
