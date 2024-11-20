**FILE SYSTEM VÀ QUẢN LÝ PHẦN MỀM**

**A. Quản lý phần mềm**

*1. Khái niệm package, dependacy và repository*

a. Package: 
- Package là một gói phần mềm chứa các tệp và tài nguyên cần thiết để cài đặt và sử dụng phần mềm
- Biên dịch: là quá trình chuyển đổi mã nguồn (ngôn ngữ lập trình) của một chương trình thành mã máy (hướng dẫn để CPU có thể hiểu và thực thi)

b. Dependencies
- Dependencies là các thư viện hoặc công cụ cần thiết để chương trình có thể hoạt động bình thường.
- Khi cài đặt bằng APT, các công cụ quản lý gói sẽ tự kiểm tra và cài các dependency cần thiết nếu chúng chưa được cài đặt sẵn
- VÍ DỤ: Khi cài đặt Python về máy, nó sẽ cần thêm công cụ pip để hỗ trợ Python cài đặt thêm các thư viện khác

c. Binary package
- Binary package là loại gói phần mềm đã được biên dịch thành mã máy để có thể cài đặt trực tiếp mà không cần phải biên dịch lại từ mã nguồn
- VÍ DỤ: Gói cài đặt của GG Chrome cho Urbuntu là file .deb được download từ trang chính thức. Sau khi tải file .deb này về ta có thể cài GG Chrome trực tiếp bằng lệnh sudo dpkg -i mà không cần phải biên dịch lại từ mã nguồn 

d. Repository và cách kiểm tra
- Repository (repo) là kho lưu trữ trực tuyến các package để có thể cài đặt hoặc cập nhật phần mềm trên hệ thống của mình.
- Để kiểm tra repo của máy urbuntu đang dùng, ta dùng lệnh: *cat /etc/apt/sources.list.d/ubuntu.sources*. Kết quả sẽ ra các URL chứa thông tin về các repository phần mềm của Ubuntu

*2. Các cách cài đặt phần mềm phổ biến*

a. Cài đặt APT từ repository

Lấy ví dụ về các bước cài ứng dụng lên urbuntu bằng APT
- Cập nhật danh sách gói: sudo apt update  
- Cài đặt gói: sudo apt install <tên ứng dụng>

b. Cài đặt từ gói nhị phân

Lấy ví dụ về các bước cài ứng dụng lên urbuntu từ gói nhị phân (.deb)
- tải gói nhị phân từ trang chính thức 
- Cài đặt gói .deb: sudo dpkg -i <file .deb> 
- Cài đặt gói phụ thuộc còn thiếu: sudo apt install -f 

*3. Các trình quản lý package của Debian (dpkg, apt-get)* 
- dpkg:
  - Là công cụ quản lý gói ở mức độ thấp, chỉ làm việc với các gói .deb và không tự động xử lý các phụ thuộc.
  - Sử dụng khi đã có sẵn một tệp .deb và muốn cài đặt hoặc gỡ bỏ phần mềm không cần internet.
- apt-get:
  - Là công cụ quản lý gói cao cấp, làm việc với repository và tự động xử lý các gói phụ thuộc.
  - Được sử dụng rộng rãi để cài đặt và quản lý phần mềm thông qua kho phần mềm chính thức của hệ thống

a. Cài đặt phần mềm
- Với dpkg: Cài đặt từ file .deb đã tải về: sudo dpkg -i <file .deb>
- Với apt-get: Tải và cài trực tiếp từ repository: sudo apt-get install <tên ứng dụng>

b. Gỡ bỏ phần mềm
- Với dpkg: *sudo dpkg -r package_name*  (gỡ bỏ gói phần mềm khỏi hệ thống, nhưng chưa xóa các tệp cấu hình và phụ thuộc. Để xóa hoàn toàn nên sử dụng phần gỡ bỏ hoàn toàn trong apt-get)
- Với apt-get:
  - Gỡ bỏ nhưng vẫn giữ file cấu hình: sudo apt-get remove package_name
  - Gỡ bỏ hoàn toàn:
    - Gỡ bỏ phần mềm và tệp cấu hình: sudo apt-get purge package_name
    - Gỡ bỏ các gói phụ thuộc không cần thiết: sudo apt-get autoremove

c. Liệt kê tất cả các phần mềm đã cài đặt
- Với dpkg: dpkg -l
- Với apt-get (hoặc apt): apt list --installed

d. Kiểm tra một phần mềm có được cài đặt hay chưa
- Với dpkg: dpkg -l | grep package_name
- Với apt-get (hoặc apt): apt list --installed | grep package_name
  
e. Lệnh apt update và apt upgrade
- apt update:
  - Cập nhật danh sách các gói phần mềm trong repository để xem có phần mềm mới hoặc bản cập nhật mới của các phần mềm sẵn có hay không
  - Sử dụng trước khi cài đặt phần mềm mới
- apt upgrade:
  - Cài đặt các bản nâng cấp của tất cả các gói phần mềm hiện có nếu chúng có bản cập nhật mới.
  - Dùng apt upgrade sau khi chạy apt update để đảm bảo rằng các phần mềm trên hệ thống được cập nhật lên phiên bản mới nhất

*4. Startup script và cách chạy script khi khởi động hệ thống.*

a. Script và startup script
- Script là một chương trình được viết bằng một ngôn ngữ lập trình để tự động hóa các tác vụ thay vì thực hiện thủ công: sao lưu dữ liệu, cấu hình hệ thống, quản lý tệp tin, hoặc khởi động các dịch vụ,....
- Startup script là các script được cấu hình để chạy tự động mỗi khi hệ thống khởi động. Những script này có thể thực hiện các công việc như cấu hình hệ thống, khởi động các dịch vụ, khởi tạo môi trường, hoặc thực thi các ứng dụng cần thiết.

b. Cách để chạy một script mỗi khi khởi động hệ thống
- Sử dụng crontab (file lên lịch các tác vụ tự động): Dùng khi chỉ cần chạy một tác vụ theo lịch, không cần các thao tác quản lý phức tạp.
  - Vào file crontab để chỉnh sửa: crontab -e
  - Thêm vào câu lệnh sau: @reboot /path/to/your_script.sh => Crontab sẽ tự động chạy script này mỗi khi server khởi động.
- Sử dụng systemd: Khi cần quản lý các dịch vụ, theo dõi trạng thái, giám sát logs hoặc khi tác vụ cần quản lý tài nguyên.
  - Tạo một file dịch vụ (.service) trong thư mục /etc/systemd/system/
  - Thêm nội dung vào file dịch vụ
  - Kích hoạt và chạy dịch vụ:
    - sudo systemctl enable my_startup_script.service
    - sudo systemctl start my_startup_script.service

**B. File và file system**

*1. File system và các loại file system*

a. File System: 
- File system là cấu trúc mà các thiết bị lưu trữ HĐH sử dụng để lưu trữ và quản lý dữ liệu trong nó

b. Các loại file system thường dùng trong Linux:
- Ext4 (bản cũ hơn là ext3 và ext2): là hệ thống tệp phổ biến Linux vì phù hợp với hầu hết các nhu cầu. Ext4 được sử dụng cho cả máy tính cá nhân và máy chủ Linux
- XFS: là hệ thống lưu trữ dành cho các tệp lớn, cần khả năng truy xuất dữ liệu nhanh. Xfs được dùng cho máy chủ lưu trữ lượng dữ liệu lớn hoặc các CSDL

*2. Cách kiểm tra và sửa lỗi một file system*

a. Cú pháp: fsck <option> <đường dẫn đến nơi cần kiểm tra>
- Options:
  - -y: Tự động sửa chữa các lỗi nếu có
  - -A: Kiểm tra tất cả phân vùng trong tệp được liệt kê

b. Các bước thường dùng
- B1: Trước khi sử dụng fsck để sửa chữa hệ thống tập tin, cần phải xác định hệ thống tập tin cần kiểm tra. Thông thường, hệ thống tập tin này là ổ đĩa hoặc phân vùng trên máy tính như: /dev/sda1, /dev/nvme0n1p1,.... Nếu không chắc chắn phân vùng nào bị lỗi, sử dụng lệnh lsblk để kiểm tra.
- B2: Gỡ bỏ gắn kết phân vùng: Để kiểm tra/sửa chữa thì phân vùng đó phải không được sử dụng: sudo umount /dev/sda1/
- B3: Sử dụng câu lệnh: sudo -y fsck /dev/sda1. Sau câu lệnh này, hệ thống sẽ:
  - Kiểm tra phân vùng /dev/sda1.
  - Tự động sửa mọi lỗi mà không yêu cầu bạn phải xác nhận.
- B4: Gắn lại liên kết phân vùng để có thể sử dụng lại: sudo mount /dev/sda1 /path/to/mountpoint

*3. Giám sát ổ đĩa với lệnh df và du*

a. Lệnh df
- Dùng để cung cấp thông tin về dung lượng của các phân vùng trên hệ thống
- Các tùy chọn thông dụng của df:
  - -h: Hiển thị dung lượng đĩa với đơn vị dễ đọc (KB, MB, GB).
  - -T: Hiển thị loại hệ thống tệp của các phân vùng.
  - -a: Hiển thị thông tin về tất cả các hệ thống tệp, bao gồm cả những hệ thống tệp có dung lượng bằng 0.
  - -i: Hiển thị thông tin về inode thay vì dung lượng.
  - -l: Hiển thị chỉ các phân vùng cục bộ.
  - --total: Hiển thị tổng dung lượng sử dụng của tất cả các phân vùng.
- Sau khi chạy lệnh df, kết quả sẽ có dạng như sau:
  ![image](https://github.com/user-attachments/assets/58fb978a-cd44-4017-aaf7-d678b91ecd6e)
  - Size: Tổng dung lượng của phân vùng
  - Used: Dung lượng đã sử dụng
  - Avail: Dung lượng còn trống
  - Use%: Phần trăm dung lượng đã sử dụng
  - Mount on: thư mục trong hệ thống Linux mà phân vùng được gắn 

b. Lệnh du
- Dùng để cung cấp thông tin về dung lượng của thư mục/tệp con
- Các tùy chọn thông dụng của du:
  - -h: Hiển thị dung lượng dễ đọc (KB, MB, GB).
  - -s: Tính tổng dung lượng của thư mục, không hiển thị các thư mục con.
  - -a: Hiển thị dung lượng của tất cả các tệp và thư mục con.
  - -c: Tính tổng dung lượng cho tất cả các thư mục và tệp đã kiểm tra.
  - --max-depth=N: Hiển thị dung lượng của các thư mục con đến độ sâu N.
  - -d N: Tương tự như --max-depth, chỉ ra số cấp thư mục muốn hiển thị.

c. So sánh df và du
- df: Hiển thị dung lượng tổng thể của các phân vùng đĩa, cho biết dung lượng đã sử dụng, còn trống, và tổng dung lượng của từng phân vùng.
- du: Hiển thị dung lượng sử dụng của thư mục và tệp, giúp kiểm tra chi tiết dung lượng của từng thư mục con hoặc tệp cụ thể.

*4. Tạo file system với lệnh mkfs*
- Lệnh mkfs được sử dụng để tạo file system trên các phân vùng hoặc thiết bị lưu trữ (như ổ đĩa).
- Việc tạo file system là cần thiết vì nó cung cấp cấu trúc để lưu trữ và quản lý tệp tin, cùng với metadata (thông tin về tên tệp, vị trí, quyền truy cập, v.v.).
- Cú pháp: sudo mkfs -t <loại_file_system> <thiết_bị>
  - -t <loại_file_system>: Chỉ định loại file system ( ext4, Btrfs,...)
  - thiết bị: đường dẫn đến phân vùng hoặc thiết bị lưu trữ (ví dụ: /dev/sdb1)
- Lưu ý: Việc tạo một hệ thống tệp trên một phân vùng sẽ phá hủy bất kỳ dữ liệu nào có thể đã nằm trên phân vùng đó.

*5. Mount và umount trong file system*
- Mount:
  - Tác dụng: Gán file system của một thiết bị lưu trữ vào một thư mục trên hệ thống linux, giúp người dùng có thể truy cập dữ liệu trên thiết bị đó.
  - Cú pháp: sudo mount <thiết bị> <thư mục mount point>
- Umount:
  - Tác dụng: Dùng trong trường hợp cần rút thiết bị ra mà không gây hại cho dữ liệu (trước khi có các thay đổi với ổ đĩa hay phân vùng; không còn muốn sử dụng phân vùng)
  - Cú pháp: sudo umount <thiết bị/thư mục mount point>
