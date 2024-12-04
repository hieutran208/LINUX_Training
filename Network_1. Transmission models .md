**CÁC MÔ HÌNH TRUYỀN TIN TRONG MẠNG MÁY TÍNH**

**A. Mô hình OSI và TCP/IP**

*Mô hình OSI và TCP/IP là 2 mô hình giúp chuẩn hóa cách truyền tải dữ liệu giữa các thiết bị trong mạng. Mô hình OSI là mô hình lý thuyết, cung cấp nhiều tầng chứa các chức năng chi tiết trong việc giao tiếp giữa các thiết bị trong mạng máy tính. Mô hình TCP/IP là mô hình được ứng dụng rộng rãi trong thực tế*

*1. Mô hình OSI*

  ![image](https://github.com/user-attachments/assets/94f81852-11b8-43ff-8612-5045f37d28b4)

Mô hình OSI chia quá trình truyền tải dữ liệu qua mạng thành 7 tầng (layers), mỗi tầng có một chức năng riêng biệt.
- Tầng Vật lý (Physical):
- Tầng Liên kết Dữ liệu (Data Link)
- Tầng Mạng (Network)
- Tầng Ứng dụng (Application): Chính là các ứng dụng mà người dùng sử dụng trực tiếp trên máy tính hoặc điện thoại (trình duyệt web, ứng dụng email, và các phần mềm khác) để tương tác với mạng 
  - Vai trò của tầng ứng dụng:
    - Cung cấp giao diện giúp người dùng tương tác với các dịch vụ mạng
    - Cung cấp các giao thức cho phép phần mềm gửi, nhận thông tin và trình bày dữ liệu có ý nghĩa cho người dùng.
  - VÍ DU: Trình duyệt web (Chrome, Firefox) giúp người dùng gửi yêu cầu truy cập và nhận về thông tin từ các trang web qua giao thức HTTP/HTTPS; Ứng dụng email (Outlook, Gmail) sử dụng giao thức SMTP để gửi và POP3 hoặc IMAP để nhận email.
- Tầng Biểu diễn (Presentation): Là tầng kế tiếp tầng biểu diễn, giúp dịch dữ liệu sang định dạng chung hoặc định dạng tầng ứng dụng có thể sử dụng:
  - Tại máy gửi: tầng biểu diễn gửi dịch dữ liệu được gửi từ tầng ứng dụng sang định dạng chung mà hệ thống mạng có thể hiểu
  - Tại máy nhận: Khi dữ liệu này được gửi qua mạng đến máy tính nhận, tầng biểu diễn ở máy nhận dịch dữ liệu từ định dạng chung (VD: HTTP/HTTPS) trở lại thành định dạng tầng ứng dụng có thể sử dụng (VD: hình ảnh, văn bản).
- Tầng Phiên (Session): Đóng vai trò thiết lập, duy trì và kết thúc giao tiếp giữa 2 máy tính
  - Thiết lập giao tiếp: Tầng Phiên giúp thiết lập kết nối giữa hai ứng dụng (VD: khi bắt đầu cuộc gọi, tầng phiên giúp thiết lập kết nối giữa hai máy tính).
  - Duy trì giao tiếp: Trong suốt phiên giao tiếp, tầng Phiên đảm bảo dữ liệu truyền đi liên tục và không bị mất
  - Kết thúc giao tiếp: Khi phiên hoàn tất (VD: cuộc gọi kết thúc), tầng Phiên đảm bảo rằng kết nối được đóng lại đúng cách và không có dữ liệu bị mất.
- Tầng Giao vận (Transport): 
  


  
