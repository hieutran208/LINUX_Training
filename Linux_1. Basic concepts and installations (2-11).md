**CÁC KHÁI NIỆM CƠ BẢN VÀ CÁCH CÀI ĐẶT**

**A. Khái niệm Linux và các Distro Linux**

*Linux* là một hệ điều hành mã nguồn mở, nghĩa là người dùng có thể tuỳ chỉnh hệ điều hành cho phù hợp với nhu cầu sử dụng. Linux nổi tiếng với tính ổn định, bảo mật và khả năng tùy biến cao. So với Windows hay MacOS, HĐH Linux có phần khó thao tác với người dùng thông thường do sử dụng giao diện dòng lệnh. Vì vậy, Linux chủ yếu được sử dụng trong các môi trường như: máy chủ, máy trạm hay các hệ thống phát triển phần mềm.

*Distro Linux* là các phiên bản của HĐH Linux. Mỗi distro có cách cài đặt, quản lý gói và giao diện riêng để hướng tới một nhóm đối tượng có nhu cầu khác nhau. Các distro linux phổ biến hiện nay được chia thành 4 nhóm chính:

- Nhóm 1: Arch, Gentoo và Slackware: nhắm vào người dùng am hiểu Linux. Do đó, phần lớn các phương thức xây dựng, cũng như cấu hình của hệ thống được thực hiện qua dòng lệnh.
- Nhóm 2: Debian, Fedora: nhắm vào người am hiểu về hệ thống nhưng chưa thực sự hiểu về Linux. Vì vậy, distro sẽ cung cấp cho họ nhiều công cụ hơn. Nhóm này phù hợp với người dùng mới bắt đầu sử dụng Linux. 
- Nhóm 3: Centos, RHEL, SUSE EL: nhắm vào thị trường máy chủ, doanh nghiệp, cơ quan… Vì chúng có sự ổn định cao, thời gian ra phiên bản mới lâu, khoảng 3 – 5 năm tùy distrolinux. Ngoài ra, còn có dịch vụ hỗ trợ thương mại cho công ty, hướng dẫn sử dụng sản phẩm.
- Nhóm 4: Ubuntu, Open SUSE, Linux Mint: người mới bắt đầu dùng Linux và người dùng cuối. Đặc tính của chúng là phát triển trong thời gian ngắn, ứng dụng các công nghệ mới liên tục, nhiều công cụ đồ họa để thiết kế và cấu hình hệ thống theo nhu cầu sử dụng. Nhóm này cũng rất thân thiện với người dùng mới làm quen Linux.

**B. Cài đặt công cụ ảo hóa (VMWare) và cài Urbuntu trên máy ảo**

*1. Cách cài đặt máy ảo VMWare trên Window Desktop*
- Truy cập trang web của VMware và tải xuống phiên bản mới nhất của VMware Workstation Player.
- Chạy tệp cài đặt và làm theo các bước trên màn hình để hoàn tất cài đặt

*2. Cách cài đặt máy ảo VMWare trên Urbuntu*
- Cập nhật gói: sudo apt update
- Cài đặt các gói phụ thuộc để VMWare hoạt động đúng: sudo apt install build-essential linux-headers-$(uname -r)
- Truy cập trang tải xuống https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion và tải tệp cài đặt VMWare theo chỉ dẫn, ta sẽ có tệp .bundle
- Cd vào thư mục download và cấp quyền thực thi cho tệp cài đặt: chmod +x VMware-Player.bundle
- Cài đặt VMware Workstation Player: sudo ./Downloads/VMware-Player.bundle
- Sau bước cài đặt, ta đã có thể mở VMWare Workstation Player bằng cách tìm kiếm trong menu ứng dụng
  
*3. Cách cài đặt và thiết lập máy ảo Urbuntu bản Server trên VMWare (tương tự với bản Desktop trên VMWare)*:
- Tải xuống file ISO của Ubuntu Server từ trang chính thức: https://ubuntu.com/download/server
- Thiết lập Urbuntu trên VMWare
  - Mở VMware Workstation/Player.
  - Chọn "Create a New Virtual Machine" (Tạo máy ảo mới).
  - Chọn "Typical (recommended)" và nhấn Next.
  - Chọn file ISO: Chọn "Installer disc image file (iso)" và duyệt tới file ISO đã tải.
  - Đặt tên cho máy ảo và chọn vị trí lưu trữ: Đặt tên như "Ubuntu_1" và chọn thư mục lưu.
  - Cấu hình phần cứng:
    - Processor: Chọn số lượng lõi CPU mà bạn muốn cấp cho máy ảo (ít nhất 1 lõi).
    - Memory: Chọn dung lượng RAM (ví dụ 2 GB).
    - Hard Disk: Để mặc định hoặc điều chỉnh dung lượng ổ cứng ảo (ít nhất 20 GB).
  - Hoàn thành và tạo máy ảo: Nhấn Finish để hoàn thành quá trình tạo máy ảo.
  - Bật Urbuntu và làm theo hướng dẫn để hoàn tất cài đặt

**C. Cách cài đặt và thiết lập Urbuntu bản Desktop về máy thực**

*Tải xuống file ISO của Ubuntu Desktop từ trang chính thức:* https://ubuntu.com/download/desktop

*Tải xuống Rufus* từ trang chính thức https://rufus.ie/vi/ để tạo USB boot cho Urbuntu

*Cấu hình Rufus:* Chọn USB trong mục “Device”, trong mục “Boot selection”, chọn file ISO của Ubuntu mà bạn vừa tải; trong mục “Partition scheme”, chọn “GPT” nếu máy tính của bạn sử dụng UEFI hoặc “MBR” nếu máy dùng BIOS cổ điển. Nhấn “Start” và chờ Rufus tạo USB boot.

*Khởi Động Máy Tính Từ USB Boot:* Cắm USB vào máy tính và khởi động lại máy. Khi máy tính khởi động, vào phần BIOS/UEFI (nhấn giữ phím F2 hoặc Del). Trong menu boot, chọn khởi động từ USB.

*Bắt Đầu Cài Đặt Ubuntu*
- Khi máy khởi động từ USB, bạn sẽ thấy màn hình chào của Ubuntu với các tùy chọn như “Try Ubuntu” và “Install Ubuntu”. Nếu bạn muốn trải nghiệm trước mà không cài đặt, chọn “Try Ubuntu”. Để bắt đầu cài đặt, chọn “Install Ubuntu”.
- Chọn Ngôn Ngữ và Bố Cục Bàn Phím: Chọn ngôn ngữ và bố cục bàn phím phù hợp.
- Kết Nối Mạng (Tuỳ Chọn): Kết nối với mạng Wi-Fi hoặc mạng dây nếu cần cập nhật trực tiếp trong quá trình cài đặt.
- Chọn Loại Cài Đặt: Normal Installation để cài đầy đủ các ứng dụng đi kèm hoặc Minimal Installation để cài tối thiểu, bao gồm trình duyệt và các tiện ích cơ bản.
- Cập Nhật và Phần Mềm Bổ Sung: Bạn có thể chọn tải về các cập nhật và cài đặt phần mềm bổ sung như trình điều khiển bên thứ ba.
- Chọn Phương Thức Cài Đặt:
Erase disk and install Ubuntu: Xóa toàn bộ ổ đĩa và cài Ubuntu (lưu ý sẽ xóa toàn bộ dữ liệu trên ổ cứng).
Install Ubuntu alongside Windows: Nếu muốn cài song song với Windows (nếu có).
Something else: Tùy chỉnh phân vùng thủ công nếu bạn có kinh nghiệm.
- Thiết Lập Thông Tin Người Dùng: Nhập tên, tên máy tính, tên người dùng, mật khẩu, và chọn phương thức đăng nhập tự động hay yêu cầu mật khẩu.
