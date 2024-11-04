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
- Mục đích sử dụng:  Ksh kết hợp các tính năng của Bourne Shell và C Shell, có hiệu suất cao và phù hợp để chạy các ứng dụng đòi hỏi xử lý phức tạp.
- Lệnh để khởi chạy: ksh
5. Csh (C Shell)
- Mục đích sử dụng: Csh có cú pháp tương tự ngôn ngữ lập trình C, do đó dễ dàng cho các lập trình viên quen với C.
- Lệnh để khởi chạy: csh
6. Tcsh (TENEX C Shell)
- Mục đích sử dụng: Tcsh là phiên bản nâng cấp của Csh với các tính năng bổ sung như tab completion và lịch sử lệnh.
- Lệnh để khởi chạy: tcsh
7. Fish (Friendly Interactive Shell)
- Mục đích sử dụng: Fish được thiết kế để dễ dùng, có cú pháp thân thiện và hỗ trợ các tính năng như highlight cú pháp và tự động gợi ý lệnh.
- Lệnh để khởi chạy: fish
8. Dash (Debian Almquist Shell)
- Mục đích sử dụng: Dash là shell siêu nhẹ và nhanh, thường dùng cho các script hệ thống trong môi trường Debian/Ubuntu, nơi yêu cầu tiết kiệm tài nguyên.
- Lệnh để khởi chạy: dash
9. Mksh (MirBSD Korn Shell)
- Mục đích sử dụng: Mksh là một biến thể của Korn Shell, gọn nhẹ và có hiệu suất tốt, thích hợp cho các hệ thống yêu cầu shell nhẹ.
- Lệnh để khởi chạy: mksh

**Thay đổi thư mục làm việc, xem thư mục đang làm việc**

*1. Thay Đổi Thư Mục Làm Việc với lệnh cd: cd [đường dẫn]*

VÍ DỤ: cd /home/trantrunghieu/Documents -> Di chuyển đến thư mục "Documents" trong đường dẫn /home/trantrunghieu.
- cd ..: Di chuyển lên một thư mục cha (thư mục cấp trên của thư mục hiện tại).
- cd ~: Di chuyển đến thư mục home của người dùng hiện tại.
- cd -: Quay lại thư mục làm việc trước đó.