**Các loại shell có trong Linux**

*Linux cung cấp nhiều loại shell khác nhau, mỗi loại có đặc điểm và chức năng riêng. Bash và Zsh là hai shell phổ biến cho người dùng thông thường và các lập trình viên do khả năng tùy chỉnh và hỗ trợ mạnh mẽ. Dưới đây là một số shell phổ biến*

1.Bash (Bourne Again Shell)
- Mục đích sử dụng: Đây là shell mặc định trên nhiều bản phân phối Linux và được dùng phổ biến cho mọi tác vụ trên hệ thống. Bash hỗ trợ cả làm việc tương tác và viết script tự động hóa, nhờ tính năng mạnh mẽ và dễ tùy chỉnh.
- Lệnh để khởi chạy: bash
2. Sh (Bourne Shell)
- Mục đích sử dụng: Đây là shell gốc của UNIX, có cú pháp đơn giản và tiêu chuẩn, chủ yếu dùng cho việc viết script hệ thống vì tính tương thích cao.
- Lệnh để khởi chạy: sh
3. Zsh (Z Shell)
- Mục đích sử dụng: Zsh là shell thay thế hiện đại, phát triển từ Bash và bổ sung nhiều tính năng tiện lợi. Người dùng ưa thích Zsh nhờ khả năng tùy biến mạnh mẽ và hỗ trợ nhiều plugin.
- Lệnh để khởi chạy: zsh
4. Ksh (Korn Shell)
- Mục đích sử dụng:  Ksh có hiệu suất cao và phù hợp để chạy các ứng dụng đòi hỏi xử lý phức tạp.
- Lệnh để khởi chạy: ksh
5. Csh (C Shell)
- Mục đích sử dụng: Csh có cú pháp tương tự ngôn ngữ lập trình C, do đó dễ dàng cho các lập trình viên quen với C.
- Lệnh để khởi chạy: csh
6. Fish (Friendly Interactive Shell)
- Mục đích sử dụng: Fish được thiết kế để dễ dùng khi hỗ trợ các tính năng như highlight cú pháp và tự động gợi ý lệnh.
- Lệnh để khởi chạy: fish
7. Dash (Debian Almquist Shell)
- Mục đích sử dụng: Dash là shell siêu nhẹ và nhanh, thường dùng cho các script hệ thống trong môi trường Debian/Ubuntu, nơi yêu cầu tiết kiệm tài nguyên.
- Lệnh để khởi chạy: dash

**Thay đổi thư mục làm việc, xem thư mục đang làm việc và tra cứu hướng dẫn/options của các lệnh**

*1. Thay Đổi Thư Mục Làm Việc với lệnh cd: cd [đường dẫn]*

VÍ DỤ: cd /home/trantrunghieu/Documents -> Di chuyển đến thư mục "Documents" trong đường dẫn /home/trantrunghieu.
- cd .. : Di chuyển lên một thư mục cha (thư mục cấp trên của thư mục hiện tại).
- cd ~ : Di chuyển đến thư mục home của người dùng hiện tại.
- cd - : Quay lại thư mục làm việc trước đó.

*2. Xem thư mục đang làm việc: pwd*
- VÍ DỤ: pwd -> Hiển thị đường dẫn thư mục hiện tại đang làm việc

*3. Tra cứu hướng dẫn/options của lệnh: man [tên lệnh]*
- VÍ DỤ: man ls -> Hiển thị hướng dẫn sử dụng và các options chi tiết dành cho lệnh "ls"

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

VÍ DỤ: sort < unsorted_list.txt => đọc nội dung từ unsorted_list.txt và sắp xếp nó.

*Redirect Output*

- Mục đích sử dụng: Cú pháp '<' dùng để chuyển hướng đầu vào từ một tệp
