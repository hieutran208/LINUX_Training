**STREAMS, REDIRECTION VÀ PIPES**(*)

**A. Các loại stream trong Linux**

*Stream (luồng) là kênh trung gian giúp phân phối dữ liệu giữa các chương trình hoặc giữa chương trình và hệ thống. Standard Input (stdin), Standard Output (stdout) và Standard Error (stderr) là ba luồng chính, dùng trong việc quản lý đầu vào, đầu ra, và xử lý lỗi khi thực thi lệnh.*

*1. Standard Input (stdin):*
- Mã đại diện: 0
- Mô tả : stdin là dữ liệu được truyền vào câu lệnh khi chương trình cần dữ liệu đầu vào. Stdin thường là từ bàn phím, ngoài ra có thể từ 1 file hoặc một chương trình khác
- Cách hoạt động khi sử dụng stdin để nhận dữ liệu đầu vào:
  - Khi một chương trình chạy và cần dữ liệu đầu vào thì nó sẽ đọc từ stdin
  - Stdin sẽ tiếp nhận dữ liệu đầu vào (từ bàn phím hoặc tệp) để truyền vào chương trình để chương trình xử lý
    - Nếu dữ liệu đến từ bàn phím, stdin sẽ chờ người dùng nhập và nhấn Enter.
    - Nếu dữ liệu đến từ tệp hoặc pipe, HĐH sẽ tự động truyền dữ liệu vào stdin khi chương trình yêu cầu.
- Ví dụ về cách sử dụng:
  - VD1: Khi chạy lệnh cat,lệnh sẽ yêu cầu nội dung từ bàn phím thông qua stdin. Stdin nhận và đọc dữ liệu từ nguồn (bàn phím) rồi truyền vào chương trình để xử lý.
  - VD2: Chuyển hướng stdin: có thể chuyển dữ liệu từ một tệp vào stdin của một chương trình thay vì nhập thủ công: cat < file.txt

*2. Standard Output (stdout)*
- Mã đại diện: 1
- Mô tả : stdout là kết quả được trả về sau khi thực thi câu lệnh thành công. Stdout mặc định xuất ra màn hình, hoặc có thể xuất ra một tệp hoặc chương trình khác
- Cách hoạt động khi sử dụng stdout để xuất dữ liệu:
  - Khi chương trình muốn xuất ra dữ liệu (thông báo, kết quả,...), nó sẽ gửi dữ liệu đến stdout
  - Stdout sẽ tiếp nhận dữ liệu từ chương trình rồi chuyển tiếp đến đích:
    - Khi không có chuyển hướng, stdout sẽ chuyển tiếp dữ liệu đến màn hình.
    - Khi có chuyển hướng, dữ liệu có thể được chuyển tiếp đến tệp hoặc chương trình khác
- Ví dụ về cách sử dụng:
  - Xuất dữ liệu ra terminal: Khi nhập lệnh echo "Hello, world!", dữ liệu vừa nhập sẽ được tiếp nhận bởi stdout rồi ghi vào đích (terminal).
  - Chuyển hướng vào tệp: Dùng > để stout chuyển hướng kết quả vào tệp thay vì hiển thị trên màn hình. Ví dụ: ls > output.txt

*3. Standard Error (stderr)*
- Mã đại diện: 2
- Mô tả: stderr là lỗi trả về nếu câu lệnh thực thi bị lỗi. Stderr thường xuất ra màn hình, ngoài ra có thể xuất ra một tệp hoặc một chương trình khác
- Cách hoạt động của stderr như sau:
  - Khi có lỗi xảy ra trong chương trình, các dữ liệu lỗi hoặc cảnh báo sẽ được gửi qua stderr (Điều này giúp phân biệt giữa dữ liệu bình thường gửi qua stdout).
  - Stderr sẽ tiếp nhận các dữ liệu lỗi rồi chuyển tiếp đến đích:
    - Nếu không có chuyển hướng, stderr sẽ chuyển tiếp dữ liệu lỗi ra terminal
    - Nếu có chuyển hướng, stderr sẽ chuyển tiếp dữ liệu lỗi đến một tệp hoặc một chương trình khác
- Cách sử dụng:
  - Hiển thị lỗi ra màn hình: Khi có lỗi xảy ra, stderr sẽ gửi thông báo lỗi ra màn hình. Ví dụ: ls /nonexistent_directory
  
=> Nếu thư mục không tồn tại, một thông báo lỗi sẽ xuất hiện.
- Chuyển hướng stderr vào tệp: Dùng 2> để ghi thông báo lỗi vào tệp thay vì hiển thị trên màn hình. Ví dụ: ls /nonexistent_directory 2> error.log (Thông báo lỗi sẽ được lưu vào error.log thay vì hiển thị trên màn hình.)

**B. Redirect Input, Output và cách Piping Data giữa các Programs**

*1. Redirect Output*

- Là cú pháp cho phép chương trình thay đổi đích xuất dữ liệu đầu ra, thay vì xuất ra màn hình như mặc định

>: Chuyển hướng stdout sang một file. Nếu file đã tồn tại, nó sẽ bị ghi đè.

    Ví dụ: echo "Hello" > output.txt sẽ ghi "Hello" vào file output.txt.

>>: Chuyển hướng stdout sang một file và thêm vào cuối file.

    Ví dụ: echo "Hello again" >> output.txt sẽ thêm "Hello again" vào cuối output.txt.

2>: Chuyển hướng stderr sang một file.

    Ví dụ: ls non_existing_file 2> error.txt sẽ ghi lỗi vào error.txt.

*2. Redirect Input*
- Là cú pháp cho phép chương trình thay đổi nguồn dữ liệu nhận vào, thay vì nhận dữ liệu từ bàn phím như mặc định.

<: Chuyển hướng stdin từ một file thay vì nhập từ bàn phím.

    Ví dụ: cat < input.txt sẽ đọc dữ liệu từ input.txt thay vì từ bàn phím.
    
*3. Piping Data giữa các Programs*

- Đây là cú pháp giúp chuyển dữ liệu từ stdout của một chương trình này làm stdin của một chương trình khác. Cú pháp này giúp kết nối các chương trình lại với nhau để thực hiện một chuỗi thao tác xử lý dữ liệu.
  
*Các cách sử dụng:*

a.Tìm kiếm tệp
- VÍ DỤ: Sử dụng ls để liệt kê các tệp và sau đó dùng grep để tìm kiếm một tệp cụ thể: ls | grep "file.txt"

=> Lệnh trên sẽ liệt kê tất cả các tệp trong thư mục hiện tại và chỉ hiển thị tệp có tên file.txt.

b. Đếm Số Dòng
- VÍ DỤ: Kết hợp cat và wc -l để đếm số dòng trong một tệp: cat file.txt | wc -l

=> Ở đây, cat file.txt đọc nội dung của file.txt và wc -l đếm số dòng trong đầu ra đó.

c. Sắp Xếp và Xóa Duplicates
- VÍ DỤ: Đọc một tệp, sắp xếp nội dung, và loại bỏ các dòng trùng lặp: cat list.txt | sort | uniq

=> Lệnh này sẽ hiển thị danh sách các mục duy nhất trong list.txt.

d. Kiểm Tra Tiến Trình
- VÍ DỤ: Sử dụng ps để liệt kê các tiến trình và grep để tìm kiếm một tiến trình cụ thể: ps aux | grep "nginx"

=> Lệnh này sẽ tìm kiếm trong danh sách các tiến trình hiện tại để xem thông tin về tiến trình nginx.

e. Kết Hợp Nhiều Lệnh
- VÍ DỤ: Đọc tệp, tìm kiếm từ khóa, sắp xếp và loại bỏ trùng lặp: cat file.txt | grep "keyword" | sort | uniq
