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
  - Thời gian của hệ thống: là thời gian thực tế mà máy chủ đang sử dụng để tính toán và đo lường các sự kiện
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
  - us: Phần trăm CPU dùng để thực thi các tác vụ do người dùng chạy (trình duyệt, game,...). Khi us ở mức từ 50%, một hoặc một số ứng dụng đang sử dụng rất nhiều tài nguyên CPU, có thể khiến hệ thống trở nên chậm và không phản hồi các tác vụ khác.
  - sy: Phần trăm CPU dùng để thực thi các tác vụ hệ thống. sy ở mức từ 30% chỉ ra đã có vấn đề với các tác vụ nền (quét virus, quản lý bộ nhớ, bảo trì hệ thống,...), điều này có thể gây ảnh hưởng đến hiệu suất các ứng dụng người dùng
  - ni: Phần trăm CPU để thực thi các tiến trình có mức độ ưu tiên thấp
  - id: Phần trăm thời gian CPU ở trạng thái nghỉ
  - wa: Phần trăm thời gian CPU ở trạng thái chờ đợi dữ liệu khi yêu cầu dữ liệu từ các thiết bị I/O (như ổ đĩa, mạng). Từ 20% là mức cần chú ý khi cho thấy hệ thống đang gặp phải tắc nghẽn I/O (ổ đĩa cứng chậm, SSD đầy, có quá nhiều thao tác đọc/ghi đồng thời hoặc vấn đề về đến mạng)
  - hi: Phần trăm CPU để xử lí các gián đoạn phần cứng
  - si: Phần trăm CPU để xử lí các gián đoạn phần mềm
  - st: Phần trăm CPU dành để chạy các tác vụ liên quan đến máy ảo (Virtual Box, VMWare,...). Nếu st từ 10% chỉ ra có những vấn đề trong môi trường ảo hóa, có thể làm giảm hiệu suất các ứng dụng trên máy thực
- Dòng thứ 4 lần lượt hiển thị các thông số về bộ nhớ vật lý (RAM) :
  - Tổng dung lượng RAM cài đặt trên hệ thống
  - Bộ nhớ trống
  - Bộ nhớ đã sử dụng
  - Dung lượng đang được dùng làm bộ đệm (buffer) và bộ nhớ cache
- Dòng thứ 5 lần lượt hiển thị các thông số về swap space:
  - Tổng swap có sẵn (kB)
  - Tổng swap còn trống
  - Tổng swap đã sử dụng
  - Tổng swap khả dụng
- Ý nghĩa các trường thông số tiến trình ở phần dưới
  - PID: Process ID
  - User: User thực hiện Process trên.
  - PR: Độ ưu tiên của Process.
  - NI: Giá trị nice value của tiến trình, giá trị âm tăng độ ưu tiên của Process, giá trị dương giảm độ ưu tiên của Process.
  - VIRT: Tổng bộ nhớ ảo mà tiến trình có quyền truy cập, bao gồm cả bộ nhớ RAM và bộ nhớ Swap
  - RES: Dung lượng RAM thực chạy Process. Đây là bộ nhớ mà tiến trình thực sự cần và đang sử dụng trực tiếp.
  - SHR: Bộ nhớ mà nhiều tiến trình có thể sử dụng chung
  - S : Trạng thái Process đang hoạt động.
  - %CPU: %CPU được sử dụng cho Process.
  - %RAM: %RAM được dùng cho Process.
  - TIME+: Tổng thời gian thực hiện 1 Process.
  - COMMAND: Tên của Process.
- *Phân biệt kill và kill -9*
  - Kill: Khi sử dụng lệnh kill mà không chỉ định thêm tham số, lệnh này sẽ yêu cầu kernel gửi tín tiệu SIGTERM đến tiến trình. SIGTERM là tín hiệu yêu cầu dừng tiến trình và cho phép tiến trình thực hiện một số thao tác trước khi kết thúc (lưu trữ dữ liệu, giải phóng tài nguyên,....).
  - Kill -9: Khi sử dụng lệnh kill -9, lệnh này sẽ yêu cầu Kernel gửi tín hiệu SIGKILL đến tiến trình. Khi tiến trình nhận được tín hiệu SIGKILL, nó sẽ bị dừng ngay lập tức mà không có cơ hội để thực hiện các thao tác như lưu trữ dữ liệu hay giải phóng tài nguyên
 
  => SIGTERM là tín hiệu dừng tiến trình đúng đắn, cho phép tiến trình thực hiện các thao tác cần thiết trước khi kết thúc, như lưu trữ dữ liệu và giải phóng tài nguyên. SIGKILL chỉ nên được sử dụng khi SIGTERM không phản hồi hoặc khi tiến trình treo và không thể dừng bằng cách thông thường.
  - Lợi ích khi sử dụng kill so với kill -9:
    - Lưu trữ dữ liệu: Nếu một tiến trình đang ghi dữ liệu vào tệp, sử dụng kill giúp cho tệp này được đóng trước khi tiến trình kết thúc. Điều này giúp lưu trữ an toàn các dữ liệu đã được ghi, đảm bảo không có dữ liệu nào bị mất.
    - Giải phóng tài nguyên: Khi một tiến trình đang chạy, nó sẽ "mượn" một phần RAM từ hệ thống. Nếu tiến trình không giải phóng bộ nhớ này khi kết thúc, hệ thống sẽ không thể tái sử dụng bộ nhớ đó, dẫn đến rò rỉ bộ nhớ. Khi hết dung lượng RAM, hệ thống sẽ phải bắt đầu sử dụng ổ cứng làm bộ nhớ ảo, làm giảm hiệu suất.
- Đơn vị đo của RAM: Lần trước đọc sai đơn vị đo dung lượng RAM
- Kiểm tra cấu hình repo hiện tại: Dùng lệnh *cat /etc/apt/sources.list*
- *Dùng apt-upgrade trong tình huống:*
  - Cách hoạt động của apt-upgrade: Hệ thống sẽ kiểm tra danh sách các gói phần mềm đã cài đặt, so sánh với bản cập nhật mới nhất trong repository. Nếu có phiên bản mới, hệ thống sẽ tải về bản cập nhật và thay thế phiên bản hiện có mà không gỡ bỏ các gói phần mềm hiện có
  - Dùng trong TH: chỉ muốn nâng cấp gói phần mềm hiện có mà không muốn làm thay đổi cấu hình và dữ liệu của gói
- *Output lệnh gỡ gói:*

  ![image](https://github.com/user-attachments/assets/1e4e4bd9-1d9c-42d9-b358-19c44a6b2047)
  - Reading package lists... -> Đọc danh sách gói phần mềm có sẵn trong repository
  - Building dependency tree... -> Kiểm tra các gói phụ thuộc (xem gói sắp gỡ có ảnh hưởng đến phụ thuộc của gói khác không)
  - Reading state information...-> kiểm tra trạng thái hiện tại của các gói trên hệ thống (để xác nhận xem gói cần gỡ bỏ có thực sự tồn tại)
  - The following packages will be REMOVED: -> Các gói phần mêmf sẽ được gỡ bỏ (2 gói)
  - 0 upgraded, 0 newly installed, 2 to remove and 3 not upgraded.
    - 0 upgraded: Không có gói nào sẽ được nâng cấp.
    - 0 newly installed: Không có gói nào mới được cài đặt.
    - 2 to remove: 2 gói sẽ bị gỡ bỏ (nginx và nginx-common).
    - 3 not upgraded: 3 gói đã có bản cập nhật mới nhưng không được nâng cấp trong lần này.
  - After this operation, 1,596 kB disk space will be freed. -> Sau khi gỡ, hệ thống giải phóng 1,596 kB dung lượng ổ đĩa
  - Sau đó là các bước: Đọc CSDL, gỡ gói, xử lý các trigger

- *Cài đặt startup script:* Lần trước chưa cài đặt được vì chưa cấp quyền thực thi cho script
- *Partition:*
  - Phân vùng: là một đơn vị logic được chia ra từ ổ đĩa vật lý. Mỗi phân vùng hoạt động, xử lý dữ liệu như một ổ cứng độc lập
  - Tác dụng của phân vùng:
    - Bảo vệ dữ liệu: Khi tạo các phân vùng riêng biệt cho hệ điều hành và các dữ liệu quan trọng. Nếu hệ điều hành gặp sự cố (bị lỗi, gặp virus hoặc cần cài đặt lại) các dữ liệu quan trọng nằm trong các phân vùng riêng biệt sẽ không bị ảnh hưởng. Nếu không tạo phân vùng thì khi HĐH gặp sự cố thì dữ liệu ở toàn bộ ổ đĩa đều sẽ bị ảnh hưởng
    - Cài đặt nhiều HĐH trên cùng 1 máy: Nếu muốn sử dụng nhiều hệ điều hành trên cùng một máy tính, tách biệt từng hệ điều hành vào các phân vùng riêng biệt giúp chuyển đổi giữa các hệ điều hành mà không gây xung đột hoặc ảnh hưởng đến dữ liệu của hệ điều hành khác.
- Filesystem
  - ext4: Là loại filesystem đáp ứng được hầu hết các nhu cầu thông thường, thích hợp cho máy tính cá nhân hay máy chủ vừa và nhỏ
  - xfs: Là loại filesystem thích hợp với máy chủ lớn, CSDL hay các ứng dụng yêu cầu hiệu suất cao
- *Check cấu hình fstab:* Dùng lệnh *sudo mount -a*, không có gì tức là file cấu hình đã đúng

- *RAID:*
  - RAID 0:

    ![image](https://github.com/user-attachments/assets/0823293b-c554-4fd9-bbbf-41e32306b709)
    - Ghi dữ liệu: Dữ liệu được chia thành các khối và ghi các khối xen kẽ, đồng thời lên mỗi ổ đĩa trong mảng. Hiệu suất đọc/ghi sẽ cao hơn ghi vào 1 đĩa đơn vì dữ liệu được chia thành các khối nhỏ được đọc/ghi đồng thời
    - Đọc dữ liệu: Khi đọc dữ liệu, các khối dữ liệu nằm trong các ổ đĩa được truy xuất đồng thời.
    - An toàn: Độ an toàn không cải thiện so với 1 đĩa đơn. Nếu 1 ổ trong mảng gặp sự cố, toàn bộ dữ liệu sẽ bị mất
  - RAID 1:
 
    ![image](https://github.com/user-attachments/assets/8875dc38-95cc-4d88-8686-f4240424734f)
    - Ghi dữ liệu: Dữ liệu được chia thành các khối, và sao chép đồng thời vào tất cả các đĩa trong mảng. Vì vậy hiệu suất ghi dữ liệu không cải thiện so với 1 đĩa đơn
    - Đọc dữ liệu: Các khối dữ liệu có thể được truy xuất từ bất kì ổ đĩa nào trong mảng mà không cần phụ thuộc vào 1 ổ đĩa duy nhất. Nếu có 1 yêu cầu duy nhất thì hiệu suất đọc không cải thiện so với 1 đĩa đơn, nhưng nếu có nhiều yêu cầu đọc cùng lúc thì hệ thống có thể phân phối các yêu cầu đọc đến các ổ đĩa trong mảng, từ đó tăng hiệu suất đọc tổng thể
    - An toàn: Tốt hơn so với đĩa đơn vì khi 1 đĩa trong mảng gặp sự cố thì bản sao dữ liệu vẫn còn nguyên trên đĩa còn lại
    - Dung lượng lưu trữ: Giả sử nếu có 2 ổ RAID 1 với dung lượng bằng nhau thì dung lượng lưu trữ chỉ bằng 1/2 tổng dung lượng 2 đĩa vì dữ liệu được ghi 2 lần
  - RAID 5:

    ![image](https://github.com/user-attachments/assets/b19fab36-67d9-42d2-92e9-760852074399)
    - Ghi dữ liệu: Chia dữ liệu thành các khối và ghi theo chu trình (Với mảng RAID 5 có N đĩa: mỗi chu trình sẽ ghi N-1 khối dữ liệu + 1 parity được tính toán từ N-1 khối trên, N khối này được ghi xen kẽ vào N ổ trong mảng theo vòng tròn). Các chu trình này lặp lại đến khi mỗi block dữ liệu được ghi đầy đủ vào một ổ đĩa duy nhất. Hiệu suất ghi sẽ chậm hơn ghi vào đĩa đơn do phải tính toán parity
    - Đọc dữ liệu: Các khối dữ liệu được truy xuất đồng thời từ các ổ đĩa trong mảng nên hiệu suất đọc sẽ nhanh hơn đĩa đơn
    - An toàn: RAID 5 có thể chịu được 1 ổ đĩa bị hỏng và có thể khôi phục dữ liệu từ thông tin parity của các ổ còn lại. Nhưng nếu 2 ổ bị hỏng thì toàn bộ dữ liệu sẽ bị mất. Độ an toàn dữ liệu sẽ cao hơn 1 đĩa đơn nhưng thấp hơn RAID 1
     
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
