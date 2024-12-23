**SHELL VÀ CÁC THAO TÁC VỚI SHELL**

**A. Các loại shell có trong Linux**

*Shell là một môi trường trong đó chúng ta có thể chạy các lệnh, các chương trình và Shell script. Linux cung cấp nhiều loại shell khác nhau, mỗi loại có đặc điểm và chức năng riêng. Bash là shell phổ biến do khả năng tùy chỉnh và hỗ trợ mạnh mẽ. Dưới đây là một số shell phổ biến*

1. Bash (Bourne Again Shell)
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

**B. Xem lịch sủ, thực hiện lại các lệnh đã gõ**

*1. Xem lịch sử*

VÍ DỤ 1: history => Hiển thị các lệnh đã chạy trong terminal

VÍ DỤ 2: history | grep "apt" => Hiển thị các lệnh đã chạy chứa từ khoá cần tìm 

VÍ DỤ 3: history -c => Xoá lịch sử

*2. Thực hiện lại lệnh*
- Ctrl + R: tìm ngược trong lịch sử, khi tìm thấy lệnh mong muốn thì nhấn ENTER để thực hiện
- Ctrl + S: tìm xuôi trong lịch sử, khi tìm thấy lệnh mong muốn thì nhấn ENTER để thực hiện
- Ctrl + G: Thoát tìm kiếm trong lịch sủ

=> Sau khi sử dụng Ctrl + R hoặc Ctrl + S, gõ một phần câu lệnh để tìm lệnh chứa từ khoá đó
  
**C. Thay đổi thư mục làm việc, xem thư mục đang làm việc và tra cứu hướng dẫn/options của các lệnh**

*1. Thay Đổi Thư Mục Làm Việc với lệnh cd: cd [đường dẫn]*

VÍ DỤ: cd /home/trantrunghieu/Documents -> Di chuyển đến thư mục "Documents" trong đường dẫn /home/trantrunghieu.
- cd .. : Di chuyển lên một thư mục cha (thư mục cấp trên của thư mục hiện tại).
- cd ~ : Di chuyển đến thư mục home của người dùng hiện tại.
- cd - : Quay lại thư mục làm việc trước đó.

*2. Xem thư mục đang làm việc: pwd*
- VÍ DỤ: pwd -> Hiển thị đường dẫn thư mục hiện tại đang làm việc

*3. Tra cứu hướng dẫn/options của lệnh: man [tên lệnh]*
- VÍ DỤ: man ls -> Hiển thị hướng dẫn sử dụng và các options chi tiết dành cho lệnh "ls"

**D. Bổ sung dòng 13: CPU, RAM, DISK**

*1. CPU* 
- CPU là bộ xử lý trung tâm giúp thực thi các chương trình do người dùng hay phần mềm yêu cầu
- Đơn vị đo hiệu năng CPU thường dùng là GHz (1 GHz = 1 tỷ phép toán/s).
- Các thống số thể hiện hiệu năng CPU:
  - Số lõi: CPU hiện đại có nhiều lõi, mỗi lõi có thể xử lý một tác vụ riêng biệt. CPU 1 lõi chỉ có thể xử lý một tác vụ tại một thời điểm, trong khi CPU đa lõi có thể xử lý nhiều tác vụ đồng thời.
  - Số luồng: Một số CPU cho phép mỗi lõi xử lý đa luồng (CPU 4 lõi, 8 luồng có thể xử lý 8 tác vụ cùng lúc (mỗi lõi xử lý 2 luồng))
  - Tốc độ xung nhịp (GHz): thể hiện khả năng xử lý nhanh hay chậm của CPU. Tốc độ xung nhịp càng cao, CPU càng thực hiện lệnh nhanh hơn (CPU 3.0 GHz sẽ nhanh hơn CPU 2.0 GHz)

*2. RAM*
- RAM là một loại bộ nhớ tạm thời dùng để lưu trữ dữ liệu và chương trình mà CPU cần trong quá trình hoạt động. Dữ liệu trong RAM sẽ bị mất khi tắt máy tính.
- Đơn vị đo hiệu năng RAM thường dùng là GB (1 GB = 1024 MB)
- Các thống số thể hiện hiệu năng RAM:
  - Dung lượng: Dung lượng RAM lớn giúp các chương trình đang chạy không chiếm hết bộ nhớ, khiến máy không phải sử dụng ổ cứng làm bộ nhớ tạm (swap), điều này làm cho máy chạy nhanh hơn.
  - Tốc độ (đo bằng MHz): Tốc độ cao hơn giúp dữ liệu được truy xuất nhanh hơn. VD: RAM 3200 MHz nhanh hơn RAM 2133 MHz.
  - Loại RAM: Ví dụ như DDR4 là chuẩn cũ, còn DDR5 là chuẩn mới với tốc độ và hiệu suất cao hơn.

*3. Disk*
- Ổ cứng là bộ nhớ lâu dài; giúp lưu trữ các tệp tin và ứng dụng. Dữ liệu trong ổ cứng sẽ không bị mất khi tắt máy
- Đơn vị đo dung lượng lưu trữ của disk: GB hoặc TB, 1 TB = 1024 GB.
- Các thông số thể hiện hiệu năng:
  - Dung lượng: Lượng dữ liệu có thể lưu trữ trên ổ cứng. Ví dụ: 500 GB, 1 TB, 2 TB.
  - Tốc độ đọc/ghi (MB/s): SSD có tốc độ đọc/ghi cao hơn HDD. (Ví dụ: SSD có thể đọc 500 MB/s, trong khi HDD chỉ có thể đọc 100 MB/s)

*4.  Quá trình truy xuất dữ liệu và xử lý*
- Khi lưu trữ các tệp tin hoặc ứng dụng, tất cả dữ liệu sẽ được lưu trên ổ cứng. Đây là bộ nhớ không thay đổi, nghĩa là dữ liệu sẽ được lưu trữ ngay cả khi máy tính tắt.
- Khi mở một ứng dụng hoặc truy cập tệp tin, HĐH sẽ nạp dữ liệu từ ổ cứng vào RAM. RAM giống như bàn làm việc tạm thời giúp CPU tăng tốc độ truy xuất dữ liệu thay vì truy xuất từ ổ cứng
- Khi CPU cần thực hiện tác vụ, nó sẽ lấy dữ liệu từ RAM, thực hiện phép toán và trả lại kết quả vào RAM.
