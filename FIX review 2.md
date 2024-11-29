- Các loại stream:
  - stdin:
    - là dữ liệu được truyền vào câu lệnh khi chương trình cần dữ liệu đầu vào. Stdin thường lấy từ bàn phím, hoặc từ một tệp hay một chương trình khác
    - Có thể thay đổi nguồn stdin bằng cú pháp redirect input (<) thay vì lấy từ bàn phím như mặc định
  - stdout:
    - là kết quả trả về sau khi thực hiện câu lệnh thành công. Stdout thường xuất ra terminal, hoặc xuất ra một tệp/chương trình khác
    - Có thể thay đổi đích của stdout bằng cú pháp redirect output (>) thay vì xuất ra terminal như mặc định
  - stderr: là lỗi trả về khi thực hiện câu lệnh không thành công. Stderr thường xuất ra terminal, hoặc xuất ra tệp/chương trình khác

- Log có thể để ở thư mục khác hay không?
  - Mặc định, các file log sẽ để trong thư mục /var/log. Tuy nhiên có thể thay đổi vị trí file log của một ứng dụng bằng cách thay đổi đường dẫn log của file cấu hình liên quan đến dịch vụ/ứng dụng, sau đó restart lại dịch vụ/ứng dụng này
  - VÍ DỤ: Với Apache hoặc Nginx, có thể thay đổi đường dẫn log trong các file cấu hình /etc/apache2/apache2.conf hoặc /etc/nginx/nginx.conf
  - Có thể thay đổi thư mục log của rsyslog bằng cách thay đổi đường dẫn log trong file cấu hình /etc/rsyslog.conf (*.* /new/log/directory/syslog)
  
