**STREAMS, REDIRECTION VÀ PIPES**

**Các loại stream trong Linux**

*Streams là các luồng dữ liệu đóng vai trò chính trong việc truyền tải thông tin giữa người dùng. Trong Linux, Standard Input (stdin), Standard Output (stdout) và Standard Error (stderr) là ba luồng (streams) chính để giao tiếp giữa người dùng và hệ thống, được sử dụng rộng rãi trong việc quản lý đầu vào, đầu ra, và xử lý lỗi khi thực thi các lệnh.*

*1. Standard Input (stdin)*
   
Mã đại diện: 0

Mục đích sử dụng: Đây là luồng đầu vào mặc định, thường nhận dữ liệu từ bàn phím hoặc từ một nguồn đầu vào khác (ví dụ: từ một tệp hoặc đầu ra của lệnh khác).

Cách sử dụng:
- Nhập dữ liệu từ bàn phím: Khi bạn chạy lệnh cần đầu vào từ người dùng, stdin sẽ nhận dữ liệu trực tiếp từ bàn phím. Ví dụ: cat > file.txt
  
=> Sau khi chạy lệnh này, bạn có thể nhập nội dung từ bàn phím vào tệp file.txt. Để kết thúc, nhấn Ctrl + D.
- Chuyển hướng stdin từ tệp: Sử dụng < để lấy đầu vào từ một tệp thay vì từ bàn phím. Ví dụ: cat < file.txt (Lệnh này sẽ hiển thị nội dung của file.txt mà không cần nhập trực tiếp từ bàn phím.)

*2. Standard Output (stdout)*
   
Mã đại diện: 1

Mục đích sử dụng: Đây là luồng đầu ra mặc định, dùng để hiển thị thông tin từ các lệnh hoặc chương trình ra màn hình.

Cách sử dụng:
- Xuất dữ liệu ra màn hình: Khi một lệnh hoàn thành và không xảy ra lỗi, kết quả sẽ được hiển thị qua stdout. Ví dụ: echo "Hello, world!"

=> Kết quả "Hello, world!" sẽ được in ra màn hình.
- Chuyển hướng stdout vào tệp: Dùng > để ghi kết quả vào tệp thay vì hiển thị trên màn hình. Ví dụ: ls > output.txt (Lệnh này sẽ lưu danh sách tệp/thư mục hiện tại vào output.txt thay vì hiển thị ra màn hình.)

*3. Standard Error (stderr)*
   
Mã đại diện: 2

Mục đích sử dụng: Đây là luồng dành cho các thông báo lỗi từ các lệnh hoặc chương trình.

Cách sử dụng:
- Hiển thị lỗi ra màn hình: Khi có lỗi xảy ra, stderr sẽ gửi thông báo lỗi ra màn hình. Ví dụ: ls /nonexistent_directory

=> Nếu thư mục không tồn tại, một thông báo lỗi sẽ xuất hiện.
- Chuyển hướng stderr vào tệp: Dùng 2> để ghi thông báo lỗi vào tệp thay vì hiển thị trên màn hình. Ví dụ: ls /nonexistent_directory 2> error.log (Thông báo lỗi sẽ được lưu vào error.log thay vì hiển thị trên màn hình.)

**Redirect Input, Output và cách Piping Data giữa các Programs**

*Redirect Input*
- Mục đích sử dụng: Cú pháp '<' dùng để chuyển hướng đầu vào từ một tệp

VÍ DỤ: cat < unsorted_list.txt => đọc nội dung từ unsorted_list.txt 

*Redirect Output*
- Mục đích sử dụng: chuyển hướng đầu ra của một lệnh đến một tệp hoặc một thiết bị khác. Có một số cách sử dụng sau: 
1. Chuyển hướng stdout vào tệp:
- Sử dụng > để ghi đè nội dung tệp hoặc tạo tệp mới.

VÍ DỤ: ls > output.txt => Lấy đầu ra của lệnh phía trước (trong trường hợp này là ls) và ghi đè nó vào tệp output.txt.
- Sử dụng >> để thêm dữ liệu vào cuối tệp mà không ghi đè.

VÍ DỤ: ls >> output.txt => Lấy đầu ra của lệnh phía trước (trong trường hợp này là ls) và thêm vào tệp output.txt.

2. Chuyển hướng stderr vào tệp:

- Sử dụng 2> để ghi thông báo lỗi vào một tệp.

VÍ DỤ: ls /nonexistent_directory 2> error.log => Lấy các lỗi của cú pháp phía trước rồi ghi vào tệp error.log

*Piping Data giữa các Programs*

- Mục đích sử dụng: Giúp kết nối đầu ra của một chương trình với đầu vào của chương trình khác thông qua ký tự '|'.
  
*Các cách sử dụng:*

1.Tìm kiếm tệp
- VÍ DỤ: Sử dụng ls để liệt kê các tệp và sau đó dùng grep để tìm kiếm một tệp cụ thể: ls | grep "file.txt"

=> Lệnh trên sẽ liệt kê tất cả các tệp trong thư mục hiện tại và chỉ hiển thị tệp có tên file.txt.

2. Đếm Số Dòng
- VÍ DỤ: Kết hợp cat và wc -l để đếm số dòng trong một tệp: cat file.txt | wc -l

=> Ở đây, cat file.txt đọc nội dung của file.txt và wc -l đếm số dòng trong đầu ra đó.

3. Sắp Xếp và Xóa Duplicates
- VÍ DỤ: Đọc một tệp, sắp xếp nội dung, và loại bỏ các dòng trùng lặp: cat list.txt | sort | uniq

=> Lệnh này sẽ hiển thị danh sách các mục duy nhất trong list.txt.

4. Kiểm Tra Tiến Trình
- VÍ DỤ: Sử dụng ps để liệt kê các tiến trình và grep để tìm kiếm một tiến trình cụ thể: ps aux | grep "nginx"

=> Lệnh này sẽ tìm kiếm trong danh sách các tiến trình hiện tại để xem thông tin về tiến trình nginx.

5. Kết Hợp Nhiều Lệnh
- VÍ DỤ: Đọc tệp, tìm kiếm từ khóa, sắp xếp và loại bỏ trùng lặp: cat file.txt | grep "keyword" | sort | uniq
