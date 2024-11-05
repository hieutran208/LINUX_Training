**THAO TÁC VỚI CÁC LỆNH XỬ LÝ VĂN BẢN**

**Lệnh cat, tac, sort, split, uniq, nl**

*1. Lệnh cat*
- Mục đích sử dụng: đọc tệp và hiển thị chúng dưới dạng stdout, nghĩa là hiển thị nội dung của tệp trên thiết bị đầu cuối
- Cách sử dụng: Có một số ví dụ về các cách sử dụng phổ biến với lệnh cat

VÍ DỤ 1: cat file.txt => Đọc nội dung file.txt rồi gửi ra màn hình terminal

VÍ DỤ 2: cat file1.txt file2.txt file3.txt => Kết hợp đọc cả 3 file rồi gửi nội dung ra màn hình terminal

VÍ DỤ 3: cat file1.txt > file2.txt => Dùng như một cú pháp sao chép nội dung file1.txt sang file2.txt

VÍ DỤ 4: cat file1.txt file2.txt file3.txt > file-all.txt => Kết hợp đọc cả 3 file rồi gửi nội dung vào file-all.txt (Nếu file-all.txt đã có nội dung và bạn chỉ muốn thêm nội dung vào chứ không muốn ghi đè lên nội dung đã có, dùng cú pháp '>>')

*2. Lệnh tac*
- Mục đích sử dụng: in từng dòng của tệp bắt đầu từ dòng dưới cùng và kết thúc ở dòng trên cùng
- Cách sử dụng: Đây là ví dụ về cách sử dụng phổ biến với lệnh tac

VÍ DỤ: tac file.txt => đọc file.txt từ cuối lên đầu (hữu ích khi muốn xem các mục gần đây nhất)

*3. Lệnh sort*

- Mục đích sử dụng: Sắp xếp nội dung file theo thứ tự tăng hoặc giảm (mặc định sẽ xếp dựa trên các kí tự đầu mỗi dòng theo mã ASCII)
- Cách sử dụng: Có một số ví dụ về các cách sử dụng phổ biến với lệnh sort

VÍ DỤ 1: sort file.txt => Sắp xếp các dòng trong tệp, theo các ký tự ở đầu mỗi dòng

VÍ DỤ 2: sort -r file.txt => Sắp xếp các dòng theo thứ tự ngược lại so với lần sắp xếp gần nhất

VÍ DỤ 3: cat file1.txt file2.txt | sort => Kết hợp hai tệp, sau đó sắp xếp các dòng và hiển thị ra màn hình

*4. Lệnh split*
- Mục đích sử dụng: chia tệp thành các phân đoạn có kích thước bằng nhau để xem và thao tác dễ dàng hơn (thường sử dụng trên các tệp tương đối lớn)
- Cách sử dụng: Đây là một số cách thường dùng với lệnh split

CÁCH 1: Chia theo số dòng: split -l [Số dòng cần chia] [file đầu vào] [Tiền tố của các tệp con được chia]n tố của các tệp con được chia]

CÁCH 2: Chia theo kích thước: split -b [Kích thước mỗi tệp con được chia theo bytes] [file đầu vào] [Tiền tố của các tệp con được chia]

CÁCH 3: Chia theo số tệp: split -n [Số các tệp con] [file đầu vào] [Tiền tố của các tệp con được chia]

*5. Lệnh uniq*
- Mục đích sử dụng: bỏ các dòng liên tiếp trùng lặp trong file
- Cách sử dụng: Có một số ví dụ về các cách sử dụng phổ biến với lệnh uniq

VÍ DỤ 1: sort example.txt | uniq => Dùng `sort` trước để đảm bảo các dòng giống nhau ở gần nhau, sau đó xoá bỏ các dòng trùng lặp

VÍ DỤ 2: uniq -c example.txt => Đếm số lần xuất hiện của mỗi dòng

