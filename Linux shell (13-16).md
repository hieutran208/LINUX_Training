**SHELL VÀ CÁC THAO TÁC VỚI SHELL**

**Các loại shell có trong Linux**

*Shell là một môi trường trong đó chúng ta có thể chạy các lệnh, các chương trình và Shell script. Linux cung cấp nhiều loại shell khác nhau, mỗi loại có đặc điểm và chức năng riêng. Bash và Zsh là hai shell phổ biến cho người dùng thông thường và các lập trình viên do khả năng tùy chỉnh và hỗ trợ mạnh mẽ. Dưới đây là một số shell phổ biến*

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

**Xem lịch sủ, thực hiện lại các lệnh đã gõ**

*1. Xem lịch sử*

VÍ DỤ 1: history => Hiển thị các lệnh đã chạy trong terminal

VÍ DỤ 2: history | grep "apt" => Hiển thị các lệnh đã chạy chứa từ khoá cần tìm 

VÍ DỤ 3: history -c => Xoá lịch sử

*2. Thực hiện lại lệnh*
- Ctrl + R: Ctrl + R để tìm ngược trong lịch sử, khi tìm thấy lệnh mong muốn thì nhấn ENTER để thực hiện
- Ctrl + S: Ctrl + S để tìm xuôi trong lịch sử, khi tìm thấy lệnh mong muốn thì nhấn ENTER để thực hiện
- Ctrl + G: Huỷ tìm kiếm trong lịch sủ
- Ngoài ra cũng có thể dùng phím điều hướng lên, xuống để tìm lại các lệnh
  
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
