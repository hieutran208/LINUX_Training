**SỬA CÁC LỖI SAI TRONG BUỔI REVIEW 2**

- *Các loại stream:*
  - stdin:
    - là dữ liệu được truyền vào câu lệnh khi câu lệnh đó cần dữ liệu đầu vào. Stdin thường lấy từ bàn phím, hoặc từ một tệp hay một chương trình khác
    - Có thể thay đổi nguồn stdin bằng cú pháp redirect input thay vì lấy từ bàn phím như mặc định
  - stdout:
    - là kết quả trả về sau khi thực hiện câu lệnh thành công. Stdout thường xuất ra terminal, hoặc xuất ra một tệp/chương trình khác
    - Có thể thay đổi đích của stdout bằng cú pháp redirect output thay vì xuất ra terminal như mặc định
  - stderr: lỗi trả về khi thực hiện câu lệnh không thành công. Stderr thường xuất ra terminal, hoặc xuất ra tệp/chương trình khác

- *Đọc lệnh top*:
  
  ![image](https://github.com/user-attachments/assets/d2311744-2f17-4262-87a7-b26bc961fb0d)
- Dòng đầu tiên lần lượt hiển thị các thông số về hệ thống:  
  - Thời gian hiện tại của hệ thống: là thời gian thực tế mà máy chủ đang sử dụng để tính toán và đo lường các sự kiện
  - Thời gian uptime: Thời gian hệ thống hoạt động kể từ lần khởi động cuối cùng
  - Số lượng người dùng đã log in
  - Loadavg trong 1 phút, 5 phút và 15 phút qua: Số tiến trình trung bình mà CPU cần phải xử lý trong mỗi khoảng thời gian
    - Loadavg < số nhân CPU: Hệ thống đang chạy với tải thấp và có khả năng chạy nhiều tiến trình hơn
    - Loadavg = số nhân CPU: Tất cả nhân CPU đều đang bận với các tiến trình đang chạy. Tuy nhiên, vì có đủ CPU cho các tiến trình nên hệ thống không bị quá tải và không có độ trễ
    - Loadavg > số nhân CPU: Các tiến trình không thể sử dụng CPU một cách độc lập mà sẽ phải chia sẻ tài nguyên CPU, dẫn đến giảm hiệu suất (VD: Nếu loadavg gấp đôi số nhân CPU thì mỗi process chỉ còn sử dụng được 50% CPU. Kết quả là, nếu một tiến trình muốn sử dụng 100% CPU nhưng chỉ nhận được 50% CPU, thời gian hoàn thành tác vụ sẽ gấp đôi)
- Dòng thứ 2 lần lượt hiển thị tổng số tác vụ và số tác vụ theo trạng thái: 
  - Tổng số tác vụ mà hệ thống đang theo dõi và quản lý
  - Số tác vụ đang chạy: Tiến trình đang sử dụng CPU để thực thi công việc
  - Số tác vụ đang trong trạng thái ngủ: Tiến trình đang không thực thi mà đợi một sự kiện khác để tiếp tục hoạt động (VD: Tiến trình đọc dữ liệu từ đĩa cần chờ dữ liệu để tiếp tục thực thi. Trong lúc dữ liệu chưa có sẵn, nó sẽ không hoạt động và không sử dụng CPU). Tiến trình này không sử dụng CPU nhưng vẫn chiếm dụng RAM mà hệ thống cấp phát
  - Số tác vụ ở trạng thái dừng: Tiến trình bị dừng hoạt động bởi một tín hiệu từ hệ thống hoặc người dùng (VD: SIGTERM), cần nhận tín hiệu từ hệ thống và người dùng để tiếp tục hoạt động. Tiến trình này không sử dụng CPU nhưng vẫn chiếm dụng RAM mà hệ thống cấp phát
  - Số tác vụ ở trạng thái zombie: Tiến trình đã hoàn thành công việc và không còn chiếm dụng CPU hay RAM, nhưng vẫn tồn tại trong bảng tiến trình
- Dòng thứ 3 hiển thị phân phối CPU lần lượt như sau: 
  - us: Phần trăm CPU dùng để thực thi các tác vụ do người dùng chạy (trình duyệt, game,...) 
  - sy: Phần trăm phân phối cho tiến trình hệ thống 
  - ni: Phần trăm phân phối cho tiến trình có mức độ ưu tiên thấp
  - id: Phần trăm CPU đang rảnh
  - wa: Phần trăm CPU để đợi khi các tiến trình I/O đang xử lí
  - hi: Phần trăm CPU để xử lí các gián đoạn phần cứng
  - si: Phần trăm CPU để xử lí các gián đoạn phần mềm
  - st: Phần trăm CPU do máy ảo sử dụng 
- Dòng thứ 4 lần lượt hiển thị các thông số về bộ nhớ vật lý (RAM) :
  - Tổng dung lượng RAM cài đặt trên hệ thống
  - Bộ nhớ trống
  - Bộ nhớ đã sử dụng
  - Dung lượng đang được dùng làm bộ đệm (buffer) và bộ nhớ cache
- Dòng thứ 5 lần lượt hiển thị các thông số về swap space (Swap là RAM ảo, được sử dụng khi bộ nhớ vật lý (RAM) bị đầy):
  - Tổng swap có sẵn (kB)
  - Tổng swap còn trống
  - Tổng swap đã sử dụng
  - Bộ nhớ khả dụng

- *Phân biệt kill và kill -9*
  - Kill: Khi sử dụng lệnh kill mà không chỉ định thêm tham số, lệnh này sẽ yêu cầu kernel gửi tín tiệu SIGTERM đến tiến trình. SIGTERM là tín hiệu yêu cầu dừng tiến trình và cho phép tiến trình thực hiện một số thao tác trước khi kết thúc (lưu trữ dữ liệu, giải phóng tài nguyên,....).
  - Kill -9: Khi sử dụng lệnh kill -9, lệnh này sẽ yêu cầu Kernel gửi tín hiệu SIGKILL đến tiến trình. Khi tiến trình nhận được tín hiệu SIGKILL, nó sẽ bị dừng ngay lập tức mà không có cơ hội để thực hiện các thao tác như lưu trữ dữ liệu hay giải phóng tài nguyên
 
  => SIGTERM là tín hiệu dừng tiến trình đúng đắn, cho phép tiến trình thực hiện các thao tác cần thiết trước khi kết thúc, như lưu trữ dữ liệu và giải phóng tài nguyên. SIGKILL chỉ nên được sử dụng khi SIGTERM không phản hồi hoặc khi tiến trình treo và không thể dừng bằng cách thông thường.
  - Lợi ích khi sử dụng kill so với kill -9:
    - Lưu trữ dữ liệu: Nếu một tiến trình đang ghi dữ liệu vào tệp, sử dụng kill giúp cho tệp này được đóng trước khi tiến trình kết thúc. Điều này giúp lưu trữ an toàn các dữ liệu đã được ghi, đảm bảo không có dữ liệu nào bị mất.
    - Giải phóng tài nguyên: Khi một tiến trình đang chạy, nó sẽ "mượn" một phần RAM từ hệ thống. Nếu tiến trình không giải phóng bộ nhớ này khi kết thúc, hệ thống sẽ không thể tái sử dụng bộ nhớ đó, dẫn đến rò rỉ bộ nhớ. Khi hết dung lượng RAM, hệ thống sẽ phải bắt đầu sử dụng ổ cứng làm bộ nhớ ảo, làm giảm hiệu suất.
  
- Kiểm tra cấu hình repo hiện tại: Dùng lệnh *cat /etc/apt/sources.list*

  ![image](https://github.com/user-attachments/assets/3665a1e2-d471-4e91-ae0f-ca47f0d0a8af)
- Dùng apt-upgrade trong tình huống
- Output lệnh gỡ gói:
- *Cài đặt startup script:* Lần trước chưa cài đặt được vì chưa cấp quyền thực thi cho script

- *Partition:*
  - Phân vùng: là một đơn vị logic được chia ra từ ổ đĩa vật lý. Mỗi phân vùng hoạt động, xử lý dữ liệu như một ổ cứng độc lập
  - Tác dụng của phân vùng:
    - Bảo vệ dữ liệu: Khi tạo các phân vùng riêng biệt cho hệ điều hành và các dữ liệu quan trọng. Nếu hệ điều hành gặp sự cố (bị lỗi, gặp virus hoặc cần cài đặt lại) các dữ liệu quan trọng nằm trong các phân vùng riêng biệt sẽ không bị ảnh hưởng. Nếu không tạo phân vùng thì khi HĐH gặp sự cố thì dữ liệu ở toàn bộ ổ đĩa đều sẽ bị ảnh hưởng
    - Cài đặt nhiều HĐH trên cùng 1 máy: Nếu muốn sử dụng nhiều hệ điều hành trên cùng một máy tính, tách biệt từng hệ điều hành vào các phân vùng riêng biệt giúp chuyển đổi giữa các hệ điều hành mà không gây xung đột hoặc ảnh hưởng đến dữ liệu của hệ điều hành khác.

- *Check cấu hình fstab:* Dùng lệnh *sudo mount -a*, nếu có bất kì lỗi cú pháp nào sẽ hiển thị ra màn hình, không có thông báo tức là file cấu hình đã đúng

- *RAID:*
- *Log có thể để ở thư mục khác hay không?*
  - Mặc định, các file log sẽ để trong thư mục /var/log. Tuy nhiên có thể thay đổi vị trí file log của một ứng dụng bằng cách thay đổi đường dẫn log của file cấu hình liên quan đến dịch vụ/ứng dụng, sau đó restart lại dịch vụ/ứng dụng này để áp dụng cấu hình vừa thay đổi
  - VÍ DỤ: Với Nginx, có thể thay đổi đường dẫn log trong các file cấu hình /etc/nginx/nginx.conf
- *Rotate log:*
  - Xoay log là tạo một file log mới và xử lý file log cũ (nén/xóa) theo quy trình được thiết lập sẵn khi chúng trở nên quá lớn hoặc quá cũ.
  - Sau khi xoay log, hệ thống tiếp tục ghi log vào file mới mà không cần can thiệp thủ công, vì file log mới và file log cũ trước khi xoay đều ở cùng một vị trí (VÍ DỤ: Một file log /var/log/myapp.log sau khi thành log cũ có thể trở thành /var/log/myapp.log.1 và một file log mới sẽ được tạo lại với tên /var/log/myapp.log)
  - Sử dụng log rotation giúp tiết kiệm dung lượng đĩa bằng cách loại bỏ các file log không cần thiết sau khi đạt các tiêu chí nhất định tùy vào cách cấu hình. Một số cách để loại bỏ file log cũ:
    - Giới hạn số lượng file log cũ: Khi số file log cũ đạt đến giới hạn tối đa đã thiết lập, file log cũ nhất sẽ được xóa
    - Xóa các file log cũ sau một khoảng thời gian nhất định: Các file log sẽ bị xóa hoặc lưu trữ (nếu được cấu hình) sau thời gian đã chỉ định
- *Cron và at*
  - Cron
    - Tính chất của cronjob: cronjob dùng để lên lịch thực thi tác vụ theo 1 chu kì xác định (hằng ngày, hàng tuần, hàng tháng hay một thời điểm nhất định trong ngày,....)
    - Phân biệt với at: cronjob lên lịch thực thi tác vụ theo chu kì, còn at lên lịch thực thi tác vụ tại một thời điểm xác định
  - Lệnh at: Lên lịch tự động thực thi tác vụ 1 lần tại 1 thời điểm xác định
    - Cài 1 lệnh chạy vào lúc 10h sáng nay: echo "command_to_execute" | at 10:00 AM
    - Cài 1 công việc chạy vào đúng 1 thời điểm trong tương lai: echo "bash path/to/script.sh" | at 09:00 2025-12-01 
    - Lên lịch thực thi sau 30 phút kể từ thời điểm hiện tại: echo "command_to_execute" | at now + 30 minutes
    - Kiểm tra các công việc đã lên lịch: atq
    - Hủy 1 công việc đã lên lịch: atrm <ID công việc>
