**QUẢN LÝ FILE**

**A. Cấu trúc thư mục trong linux**

*1. Định nghĩa "cấu trúc thư mục trong Linux", phân biệt với "file system trong Linux"*
- Cấu trúc thư mục trong Linux (hay Filesystem Hierarchy Standard (FHS)), là một mô hình tổ chức các thư mục quan trọng trong toàn hệ thống Linux, giúp HĐH dễ dàng quản lý các tệp tin và phần mềm.
- Phân biệt FHS và file system:
  - *Cấu trúc thư mục* là cách HĐH tổ chức các thư mục quan trọng trong toàn hệ thống
  - *Hệ thống tệp* là cách thiết bị lưu trữ trên HĐH lưu trữ và quản lí dữ liệu trong nó

*2. Cấu trúc thư mục trong Linux*
   
![image](https://github.com/user-attachments/assets/74e985d0-a028-421f-abcc-bf9998debbf3)

- /
  - Mục đích: là thư mục gốc, điểm khởi đầu của tất cả tập tin và thư mục trong hệ thống
  - Chỉ user root mới có quyền thực thi trên thư mục này
- /bin
  - Mục đích: Chứa các chương trình (lệnh) cơ bản (cat, ls, cp....), là các công cụ cần thiết cho hệ thống khi hoạt động.
  - Ví dụ: Các lệnh như ls, cp, mv (để liệt kê tệp, sao chép, di chuyển) đều nằm trong /bin.
- /boot
  - Mục đích: Chứa các tệp cần thiết để khởi động hệ thống. Đây là nơi chứa các tệp cấu hình cho bộ nạp khởi động (bootloader) và kernel của hệ điều hành.
  - Ví dụ: Tệp kernel (như vmlinuz) và bộ nạp khởi động GRUB nằm trong /boot
- /dev
  - Mục đích: Chứa các tệp đại diện cho các thiết bị phần cứng được kết nối với máy tính: (như ổ cứng, bàn phím, chuột, hay các thiết bị mạng)
  - Ví dụ: /dev/sda có thể là ổ cứng đầu tiên, /dev/tty là thiết bị đầu vào/ra như bàn phím và màn hình.
- /etc
  - Mục đích: lưu trữ các tệp cấu hình của HĐH và các ứng dụng để thiết lập và điều khiển cách thức hoạt động của hệ thống.
  - Ví dụ: /etc/passwd chứa thông tin về người dùng, /etc/hostname chứa tên máy chủ, và /etc/network/interfaces chứa cấu hình mạng.
- /home
  - Mục đích: Chứa các thư mục cá nhân (tài liệu, ảnh,...) của tất cả người dùng. Mỗi người dùng trên hệ thống sẽ có một thư mục con trong /home để lưu trữ các tệp cá nhân của mình.
  - Ví dụ: Thư mục của người dùng "alice" sẽ là /home/alice, nơi chứa các tệp và thư mục của người dùng này.
- /lib
  - Mục đích: Chứa các thư viện cần thiết để các chương trình và ứng dụng có thể chạy
  - /lib/libc.so là thư viện chuẩn cho các chương trình, giúp chúng thực thi các chức năng cơ bản như nhập xuất dữ liệu.
- /media
  - Mục đích: là thư mục chứa các thiết bị ngoại vi đã được "mount" (gắn kết) tạm thời vào hệ thống, như ổ USB, đĩa CD/DVD, hoặc các ổ cứng ngoài.
  - Ví dụ: Khi bạn cắm một chiếc USB, nó có thể được gắn vào thư mục /media/usb
- /mnt
  - Mục đích: Cũng là thư mục chứa các thiết bị ngoại vi được gắn kết tạm thời, tuy nhiên dùng thư mục này chủ yếu khi muốn thực hiện các thao tác với thiết bị hay quản trị dữ liệu
  - VÍ DỤ: Nếu muốn "mount" một phân vùng từ ổ cứng vào thư mục này, bạn có thể tạo một thư mục con trong /mnt như /mnt/data để chứa dữ liệu đó.
- /opt
  - Mục đích: Chứa các phần mềm hoặc ứng dụng không phải là các gói chính thức của hệ điều hành.
  - Ví dụ: Một số ứng dụng như Google Chrome hoặc các phần mềm đặc biệt có thể được cài trong /opt.
- /sbin
  - Mục đích: Chứa các chương trình của các công cụ dùng để quản lý hệ thống, cài đặt phần mềm, hoặc bảo trì hệ thống,
  - Ví dụ: Các lệnh như shutdown, reboot, ifconfig (cấu hình mạng) nằm trong /sbin
- /srv
  - Mục đích: Chứa các tệp dữ liệu mà máy chủ cung cấp cho các dịch vụ như web, FTP,...để sử dụng hoặc cung cấp cho người dùng
  - Ví dụ: Nếu bạn chạy một máy chủ web, thư mục /srv/www có thể chứa các trang web của bạn.
- /tmp
  - Mục đích: Chứa các tệp tạm thời (tệp cache, các tệp tải xuống tạm thời,...) mà các chương trình hoặc hệ thống sử dụng trong quá trình hoạt động. Các tệp này thường bị xóa sau mỗi lần khởi động hệ thống hoặc sau một khoảng thời gian nhất định.
  - Ví dụ: Khi bạn mở một chương trình, nó có thể tạo ra các tệp tạm thời trong /tmp như các tệp tạm thời của trình soạn thảo văn bản hoặc các tệp tải lên từ trình duyệt.
- /var 
  - Mục đích: Chứa dữ liệu mà hệ thống và các ứng dụng tạo ra, thay đổi, hoặc sử dụng trong thời gian thực: các tệp log, các tệp tin tạm thời, cơ sở dữ liệu,....
  - Các thư mục con:
    - /var/log: Chứa các tệp log (nhật ký hệ thống), bao gồm các thông báo về hoạt động của hệ thống và các dịch vụ
    - /var/lib: Chứa các dữ liệu động mà các ứng dụng cần để lưu trữ, ví dụ như cơ sở dữ liệu và trạng thái ứng dụng.
- /usr
  - Mục đích: Chứa các phần mềm và ứng dụng được cài đặt thêm để phục vụ nhu cầu của người dùng; người dùng có thể sử dụng sau khi đã cài đặt thêm vào hệ thống (các phần mềm như trình duyệt, bộ công cụ văn phòng, các phần mềm lập trình,....)
  - Các thư mục con phổ biến:
    - /usr/bin chứa các chương trình thực thi cho người dùng (vd: dòng lệnh)
    - /usr/lib chứa thư viện hệ thống hỗ trợ các ứng dụng trong /usr/bin
    - /usr/share chứa các dữ liệu dùng chung như hình ảnh hoặc tài liệu. Thư mục này chứa các chương trình ứng dụng được cài đặt cho người dùng.
- /proc
  - Mục đích: Là thư mục ảo, chứa các thông tin về hệ thống và các tiến trình đang chạy. Dữ liệu trong /proc không thực sự được lưu trữ trên đĩa, mà là thông tin được tạo ra bởi hệ điều hành về trạng thái của hệ thống.
  - Ví dụ: /proc/cpuinfo chứa thông tin về CPU, /proc/meminfo chứa thông tin bộ nhớ, và /proc/[pid] chứa thông tin về các tiến trình đang chạy.

**B. Các lệnh quản lí file/thư mục: ‘ls’, ‘cp’, ‘mv’, ‘rm’, ‘touch’, ‘ln’**

*1. Lệnh ls*
- Mục đích: Liệt kê danh sách các tệp/thư mục trong thư mục hiện tại hoặc một thư mục được chỉ định
- Cú pháp: ls [options] [đường dẫn]
- Options:
  - -l: Hiển thị chi tiết thông tin (quyền, kích thước, thời gian)
  - -a: Hiển thị cả các tệp ẩn
  - -R: Hiển thị nội dung của thư mục con
  - -h: Hiển thị cả kích thước

*2. Lệnh cp*
- Mục đích: Sao chép tệp/thư mục từ vị trí này qua vị trí khác
- Cú pháp: cp [options] [đường dẫn] [đích]
- Options:
  - -r: Sao chép thư mục và các nội dung bên trong 
  - -i: Yêu cầu xác nhận trước khi thay thế tệp đích (tránh ghi đè)
  - -v: Hiển thị thông tin các tệp đang sao chép

*3.Lệnh mv*
- Mục đích: Di chuyển tệp/thư mục từ vị trí này qua vị trí khác hoặc đổi tên tệp/thư mục
- Cú pháp:
  - Di chuyển tệp/thư mục: mv [options] [đường dẫn] [đích]
    - -i: Y/c xác nhận trước khi thay thế tệp/thư mục đích
    - -f: Ghi đè mà không cần xác nhận
    - -v: Hiển thị thông tin các tệp/thư mục đang sao chép
    - --backup: Tạo bản sao lưu của tệp đích trước khi ghi đè
  - Đổi tên tệp/thư mục: mv old_name new_name

*4. Lệnh rm*
- Mục đích: Xóa bỏ tệp/thư mục
- Cú pháp: rm [options] [đường dẫn]
- Options:
  - -r: Xóa bỏ cả thư mục và các nội dung bên trong
  - -i: Y/C xác nhận trước khi xóa
  - -f: Xóa mà không cần xác nhận

*5. Lệnh touch*
- Mục đích: tạo tệp mới khi tệp đó chưa tồn tại
- Cú pháp: touch [đường dẫn]

*6. Lệnh ln*
- Mục đích lệnh ln: Tạo các liên kết trong hệ thống file, giúp tạo ra một đường dẫn trỏ tới một file hoặc thư mục khác
  - Hard link: Chỉ có thể trỏ tới các file trong cùng một phân vùng (có thể khác thư mục), không thể trỏ tới thư mục khác hoặc các file trong phân vùng khác
  - Soft link: Có thể liên kết qua các phân vùng khác nhau và có thể trỏ đến một thư mục khác
- Cú pháp:
  - Tạo liên kết cứng: ln <đường dẫn file gốc> <tên liên kết> (ln -s để tạo softlink)
  - Xóa liên kết: unlink <tên liên kết>
  
**C. Quản lý quyền sở hữu và quyền truy cập file**

*1. Khái niệm quyền sở hữu và quyền truy cập*
- Quyền sở hữu: Mỗi folder hay file bất ký đều chịu sự quản lý của 4 đối tượng:
  - Đối tượng u: user tạo ra file/folder (hoặc một user được chỉ định làm chủ sở hữu)
  - Đối tượng g: group của file/folder (những user trong nhóm này sẽ có quyền truy cập như nhau)
  - Đối tượng o: các đối tượng khác không là chủ sở hữu và không thuộc nhóm sở hữu
  - Đối tượng a: tất cả các user tồn tại trên hệ thống (thường dùng với lệnh chmod)
- Quyền truy cập: Có 3 quyền truy cập cho file/thư mục
  - r: Đọc nội dung file
  - w: Thay đổi nội dung file
  - x:
    - Với file: thực thi file dưới dạng chương trình
    - Với thư mục: Truy cập các file và thư mục con
- Khi dùng lệnh ls -l, ta sẽ show được các quyền và chủ sở hữu này, nó được thể hiện bằng 10 kí tự

  ![image](https://github.com/user-attachments/assets/d0f6f12d-1645-4817-aebb-6cd7e6c43d3e)
    - kí tự đầu tiên: "-" biểu thị file; "d" biểu thị thư mục
    - 9 kí tự tiếp theo: chỉ định quyền r,w,x cho mỗi đối tượng u,g,o theo thứ tự từ trái qua phải ("-" nếu không có quyền) 

*2. Lệnh chown và chgrp*
- Lệnh chown: (-R thay đổi chủ sở hữu của thư mục và tất cả các tệp/thư mục con)
  - Thay đổi cả chủ và nhóm sở hữu: chown +[options] + [tên user : tên nhóm] + [tập tin/thư mục]
  - Chỉ thay chủ sở hữu: chown +[options] + [tên user] + [tập tin/thư mục]
  - Chỉ thay đổi nhóm: chown +[options] + [: tên nhóm] + [tập tin/thư mục]
- Lệnh chgrp: (-R thay đổi nhóm sở hữu của thư mục và tất cả các tệp/thư mục con)
  - chgrp +[options] + [tên nhóm sở hữu] + [tên tập tin/thư mục]
 
*3.Thay đổi và thiết lập quyền truy cập với chmod*

a. Chỉ định bằng phương pháp chữ
- Cú pháp: chmod + [nhóm người dùng] + [thao tác] + [quyền] + [tập tin/thư mục]
- Thêm option -R nếu áp dụng quyền cho một thư mục và tất cả các tệp trong nó

  ![image](https://github.com/user-attachments/assets/7022d3f6-a775-47c2-811a-2f259074e468)

b. Chỉ định bằng phương pháp số
- Trong phương thức này, quyền được biểu diễn bằng dãy 3 chữ số, mỗi chữ số chỉ định quyền cho một đối tượng và có được bằng cách tính tổng các quyền:
  - r (read) + 4
  - w (write) + 2
  - x (execute) + 1
  - (no permission) + 0
- Cú pháp: chmod + [giá trị định quyền] + [file/thư mục]
  - Chữ số đầu tiên là quyền của user
  - Chữ số thứ hai là quyền của group 
  - Chữ số thứ ba là quyền của other 
- Thêm option -R nếu áp dụng quyền cho một thư mục và tất cả các tệp trong nó

**D. Các tool tìm kiếm file: ‘find’, ‘locate’, ‘whereis’, ‘which’**

*1. Lệnh find*
- Là lệnh giúp tìm kiếm file dựa trên các tiêu chí (tên, kích thước, ngày tạo, quyền truy cập,...)
- Cú pháp chung: find [điểm tìm kiếm] [tuỳ_chọn_tìm_kiếm]
  - điểm tìm kiếm: điểm bắt đầu tìm kiếm (một/nhiều thư mục). Nếu không chỉ định sẽ bắt đầu tìm từ thư mục làm việc hiện tại.
  - tùy chọn: có một số tùy chọn phổ biến
    - -name: Tìm theo tên tệp.
    - -type: Tìm theo kiểu (f = file, d = directory).
    - -size: Tìm tệp theo kích thước.
    - -mtime: Tìm tệp dựa trên thời gian sửa đổi.
 - VÍ DỤ:
   - Tìm các file và thư mục trong ./Documents: find ./Documents
   - Tìm các file và thư mục có đuôi .txt: find ./Documents -name "*.txt" (-iname: không phân biệt chữ hoa chữ thường) 
   - Tìm các file và thư mục có kích thước lớn hơn 1 MB(-: nhỏ hơn): find ./Documents -size +1M
   - Tìm các thư mục trong ./Documents: find ./Documents -type d
   - Tìm các file và thư mục đã được sửa đổi trong 7 ngày qua (chưa được sửa đổi: +): find . -mtime -7
   - Tìm tệp theo quyền (Theo chữ: u=rw): find . -perm 0640
   - Tìm tệp thỏa mãn 1 trong các điều kiện: ![image](https://github.com/user-attachments/assets/9c39d851-21fb-42a4-9be7-8efdbaf6222b)

*2. Lệnh locate*
- Lệnh locate không quét toàn bộ hệ thống để tìm tệp như lệnh find mà tìm kiếm trong một CSDL đã được lưu trữ sẵn. Nhờ vậy tốc độ tìm kiếm sẽ nhanh hơn find.
- Lệnh locate phù hợp sử dụng để tìm kiếm nhanh trên các hệ thống lớn, các tiêu chí tìm kiếm không có gì khác ngoài tên
- CSDL của locate được tạo ra từ kết quả quét hệ thống tệp và chứa thông tin về tất cả các tệp và thư mục trong hệ thống. Trước khi chạy lệnh locate, ta cần cập nhật CSDL này bằng lệnh updatedb
- Cú pháp chung: locate [option] <tên tệp>
  - -i: Không phân biệt chữ hoa/thường
  - -c: Hiển thị số kết quả phù hợp
- VÍ DỤ: locate "*.txt"

*3. Lệnh whereis*
- Lệnh whereis được sử dụng để tìm vị trí của các tệp nhị phân, tệp mã nguồn, và tệp tài liệu của các chương trình hoặc lệnh
- Không tìm toàn bộ hệ thống tệp như các lệnh trên mà tìm kiếm trong một số thư mục cụ thể được xác định từ trước
- Cú pháp chung: whereis [option] <chương trình hoặc lệnh>
  - -b: Chỉ tìm tệp nhị phân
  - -m: Chỉ tìm tệp tài liệu
  - -s: Chỉ tìm tệp mã nguồn
- VÍ DỤ: whereis -s rm

*4. Lệnh which*
- Lệnh which dùng để tìm kiếm tệp thực thi (binary file) của một lệnh hoặc chương trình. Nó không tìm kiếm tệp tài liệu về tệp mã nguồn như whereis
- Giúp người dùng xác định xem một lệnh có sẵn trên hệ thống hay không. Nếu có, thì tệp thực thi của lệnh đó nằm ở đâu.
- VÍ DỤ:
  - Tìm tệp thực thi của lệnh: which echo
  - Xác định xem lệnh có trên hệ thống không: which nonexistent_command => Không in ra kết quả
