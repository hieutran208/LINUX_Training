**CÁC LỆNH VÀ CÁC THAO TÁC DÙNG TRONG XỬ LÝ VĂN BẢN**

**A. Lệnh cat, tac, sort, split, uniq, nl**

*1. Lệnh cat*
- Mục đích sử dụng: đọc tệp và hiển thị chúng dưới dạng stdout, nghĩa là hiển thị nội dung của tệp trên thiết bị đầu cuối
- Cách sử dụng: Có một số ví dụ về các cách sử dụng phổ biến với lệnh cat

VÍ DỤ 1: cat file.txt => Đọc nội dung file.txt rồi gửi ra màn hình terminal

VÍ DỤ 2: cat file1.txt file2.txt file3.txt => Kết hợp đọc cả 3 file rồi gửi nội dung ra màn hình terminal

VÍ DỤ 3: cat file1.txt > file2.txt => Dùng như một cú pháp sao chép nội dung file1.txt sang file2.txt

VÍ DỤ 4: cat file1.txt file2.txt file3.txt > file-all.txt => Kết hợp đọc cả 3 file rồi gửi nội dung vào file-all.txt (Nếu file-all.txt đã có nội dung và bạn chỉ muốn thêm nội dung vào chứ không muốn ghi đè lên nội dung đã có, dùng cú pháp '>>')

*2. Lệnh tac*
- Mục đích sử dụng: in từng dòng của tệp bắt đầu từ dòng dưới cùng và kết thúc ở dòng trên cùng

VÍ DỤ: tac file.txt => đọc file.txt từ cuối lên đầu (hữu ích khi muốn xem các mục gần đây nhất)

*3. Lệnh sort*

- Mục đích sử dụng: Sắp xếp nội dung file theo thứ tự tăng hoặc giảm (mặc định sẽ xếp dựa trên các kí tự đầu mỗi dòng theo mã ASCII)
- Cách sử dụng: Có một số ví dụ về các cách sử dụng phổ biến với lệnh sort

VÍ DỤ 1: sort file.txt => Sắp xếp các dòng trong tệp, theo các ký tự ở đầu mỗi dòng

VÍ DỤ 2: sort -r file.txt => Sắp xếp các dòng theo thứ tự ngược lại

VÍ DỤ 3: sort -t ',' -k 3 file1.txt => sắp xếp theo cột 3, các cột cách nhau bởi dấu phẩy

VD4. Sắp xếp theo số: sort -n so_lieu.txt => Lệnh này sẽ sắp xếp các dòng trong tệp so_lieu.txt theo giá trị số.

VD5. Sắp xếp theo cột: sort -k 2 ten_tap_tin => Lệnh này sẽ sắp xếp theo cột thứ 2 trong tệp.

*4. Lệnh split*
- Mục đích sử dụng: chia tệp thành các phân đoạn (thường sử dụng trên các tệp tương đối lớn)
- Cách sử dụng: Đây là một số cách thường dùng với lệnh split

CÁCH 1: Chia theo số dòng: split -l [Số dòng cần chia] [file đầu vào] [Tiền tố của các tệp con được chia]n tố của các tệp con được chia]

CÁCH 2: Chia theo kích thước: split -b [Kích thước mỗi tệp con được chia theo bytes] [file đầu vào] [Tiền tố của các tệp con được chia]

CÁCH 3: Chia theo số tệp: split -n [Số các tệp con] [file đầu vào] [Tiền tố của các tệp con được chia]

*5. Lệnh uniq*
- Mục đích sử dụng: bỏ các dòng liên tiếp trùng lặp trong file
- Cách sử dụng: Có một số ví dụ về các cách sử dụng phổ biến với lệnh uniq

VÍ DỤ 1: sort example.txt | uniq => Dùng `sort` trước để đảm bảo các dòng giống nhau ở gần nhau, sau đó xoá bỏ các dòng trùng lặp

VÍ DỤ 2: uniq -c example.txt => Đếm số lần xuất hiện của mỗi dòng

*6. Lệnh nl*
- Mục đích sử dụng: đánh số thứ tự các dòng trong file
  
VÍ DỤ: nl file.txt => Hiển thị nội dung file.txt kèm số dòng lên terminal

**B. Các lệnh xem tệp: ‘head’, ‘tail’, ‘less’, ‘cut’, ‘wc’**

*1. Lệnh head*
- Mục đích sử dụng: Xem phần đầu của file (mặc định là 10 dòng đầu)
  
VÍ DỤ 1: head file.txt => Hiển thị nội dung 10 dòng đầu file.txt lên terminal

VÍ DỤ 2: head -n 20 file.txt => Hiển thị nội dung 20 dòng đầu file.txt lên terminal

*2. Lệnh tail*
- Mục đích sử dụng: Xem phần cuối của file (mặc định là 10 dòng cuối)
  
VÍ DỤ 1: tail file.txt => Hiển thị nội dung 10 dòng cuối file.txt lên terminal

VÍ DỤ 2: tail -f file.txt => Hiển thị các nội dung gần nhất thêm vào file.txt

*3. Lệnh less*
- Mục đích sử dụng: Hiển thị nội dung file dưới dạng trang (thường dùng cho các file có kích thước lớn)

*Các thao tác sử dụng:*

- Trang trước: Dùng phím Space hoặc bấm phím b
- Trang kế: Dùng phím Enter hoặc phím d
- Đến đầu file: Dùng phím g
- Đến cuối file: Dùng phím G
- Tìm kiếm từ: sử dụng '/', sau đó gõ từ cần tìm kiếm
- Thoát khỏi giao diện: Ctrl + Z

*4. Lệnh cut*
- Mục đích sử dụng: Trích xuất các phần cụ thể của văn bản từ file đầu vào.
- Cú pháp cơ bản: cut -d <khoảng cách giữa các trường> -f <tên trường cần tin> <file_name>

VÍ DỤ 1 (lấy các kí tự cụ thể trong chuỗi): echo "Hello World" | cut -b 1,2,3,5,8,9 => In ra chữ "Heloor" 

VÍ DỤ 2 (Trích xuất cột đầu tiên khi tệp có các trường cách nhau bằng tab): cut -d ' ' -f1 file.txt

VÍ DỤ 3 (Trích xuất các kí tự từ 1->3 trong mỗi dòng): cut -c1-3 file.txt

*5. Lệnh wc*
- Mục đích sử dụng: đếm số từ, số dòng và ký tự trong tệp

VÍ DỤ 1: wc file.txt => Hiển thị lần lượt số dòng, số từ và số kí tự trong file

VÍ DỤ 2: wc -w file.txt => Chỉ đếm số từ (options -l và -m sẽ chỉ hiển thị số dòng và số kí tự)

**C. Các lệnh grep, sed, awk**

*1.Lệnh grep*
- Mục đích sử dụng: Dùng để tìm kiếm mẫu văn bản
- Cách sử dụng: Có một số ví dụ về các cách sử dụng phổ biến với lệnh grep

VÍ DỤ 1: grep "line" file.txt => Tìm kiếm từ "line" trong file.txt (nếu muốn tìm chuỗi dùng option -r)

VÍ DỤ 2: grep -i "Line" file1.txt file2.txt => Tìm kiếm từ trong nhiều file, không phân biệt chữ hoa, chữ thường

VÍ DỤ 3: grep -n "error" file.txt => Tìm kiếm và hiển thị số dòng chứa chuỗi "error"

VÍ DỤ 4: grep -c "error" file.txt => Đếm số dòng chứa chuỗi "error"

VÍ DỤ 4: grep -v "error" file.txt => Hiển thị số dòng không chứa chuỗi "error"


*2. Lệnh sed*
- Mục đích sử dụng: chỉnh sửa văn bản trực tiếp từ file
- Cách sử dụng: Có một số ví dụ về các cách sử dụng phổ biến với lệnh sed

VÍ DỤ 1: sed '3s/this/This/' file.txt => thay thế 'this' thành 'This' ở dòng thứ 3 trong file.txt với option -s

VÍ DỤ 2: sed 's/this/This/g' file.txt => thay thế 'this' thành 'This' trong mọi lần xuất hiện với option -g

VÍ DỤ 3: sed '3d' file.txt => Xoá dòng thứ 3 trong tệp

VÍ DỤ 4: sed '/keyword/d' file.txt => Xoá các dòng có chứa từ 'keyword' trong tệp

VÍ DỤ 5: sed 's/^/PREFIX: /' sample.txt => Chèn chuỗi vào đầu mỗi dòng

VÍ DỤ 6: sed -i 's/^/PREFIX: /' sample.txt => Thay đổi trực tiếp trong file (không tạo file tạm)

*3. Lệnh awk*
- Mục đích sử dụng: xử lý văn bản theo hàng và cột, chủ yếu dùng trong các tệp có cấu trúc
- Cách sử dụng: Có một số cách sử dụng phổ biến với lệnh awk

CÁCH 1: awk -F ',' '{print $cột_thứ_1 $cột_thứ_2 }' file.txt => In ra các cột cụ thể, các cột phân tách bởi dấu phẩy

CÁCH 2: awk '$số_thứ_tự_cột điều_kiện {print $0}' file.txt => In ra các dòng thoả mãn điều kiện trong một cột cụ thể

CÁCH 3: awk '{sum += $số_thứ_tự_cột} END {print "SUM:", sum}' file.txt => Tính tổng các giá trị trong một cột cụ thể

**D. Trình soạn thảo vim**(*)

*1. Các chế độ làm việc của vim*

a. Chế độ command mode
- Là chế độ mặc định khi mở vim. Ở chế độ này ta có thể di chuyển con trỏ, thực hiện các thao tác như sao chép, dán, xóa, tìm kiếm, và điều khiển con trỏ.
- Chuyển sang chế độ khác: Nhấn phím 'i' để chuyển sang insert mode và nhấn ':' để chuyển sang ex mode

b. Chế độ insert mode
- Đây là chế độ có thể gõ chữ vào văn bản giống như các trình soạn thảo văn bản khác.
- Chuyển sang chế độ khác: Nhấn 'esc' để trở về chế độ command mode

c. Chế độ ex mode
- Thực hiện các câu lệnh phức tạp hoặc không thực hiện được trong chế độ command mode. Nếu như command mode chủ yếu thực hiện các thao tác với văn bản thi ex mode thực hiện các lệnh toàn cục liên quan đến quản lý tệp, cấu hình Vim và các thao tác nâng cao.
- Chuyển qua chế độ khác: Nhấn 'esc' để trở lại chế độ command mode

*2. Các thao tác cơ bản khi sử dụng vim*

a. Tạo/mở một file bất kì
- Sau khi mở Terminal, gõ lệnh vim + [đường dẫn đến file] để mở file. 

b. Chèn văn bản vào file
- Sau khi mở file, trình soạn thảo sẽ ở chế độ command mode. Để chèn văn bản ta cần nhấn phím “i” để chuyển sang chế độ insert mode. Ở chế độ này, ta có thể gõ chữ vào văn bản từ bàn phím. Khi hoàn thành, nhấn “esc” để quay lại chế độ command mode. 

c. Điều hướng con trỏ 
- Khi điều hướng con trỏ, ta chủ yếu dùng các phím mũi tên. Nhưng nếu file lớn, ta cũng có thể di chuyển tới dòng bất kì bằng lệnh “:<số dòng>” (ví dụ dòng số 5 thì nhấn “:5”); di chuyển đến đầu văn bản bằng lệnh gg và cuối văn bản bằng lệnh G 

d. Xoá trong văn bản
- Muốn xoá một kí tự ta nhấn “x” hoặc delete 
- Xoá 1 dòng tính từ vị trí con trỏ nhấn “:d”
- dG: Xoá từ vị trí con trỏ đến cuối file (G=shift+g)
- Để hoàn tác ta nhấn “u”

e. Tìm kiếm trong văn bản
- Để tìm kiếm các từ, ta nhấn câu lệnh “/<từ cần tìm>” rồi nhấn ENTER. Sau khi đã có kết quả, nhấn "n" để con trỏ di chuyển đến kết quả tiếp theo hoặc Shift+n để quay lại kết quả trước

f. Thoát khỏi trình soạn thảo 
- Ở command mode, để thoát khỏi vim sau khi lưu các thay đổi, gõ :x hoặc :wq. Nếu muốn thoát mà không lưu thay đổi, gõ :q!.

g. Sao chép, dán và cắt
- 3yy: Sao chép 3 dòng hiện tại.
- y$: Sao chép đến cuối dòng
- p: Dán văn bản đã sao chép vào sau con trỏ.
- P: Dán văn bản đã sao chép vào trước con trỏ.
- dd: Cắt dòng hiện tại.
- yw: Sao chép từ hiện tại.

h. Thay thế:
- :%s/old/new/g: Thay thế tất cả từ old thành new trong toàn bộ tệp.
- :3,7s/old/new/g: Thay thế từ dòng 3 đến dòng 7 các từ old thành new 
  
i. Các câu lệnh khác: https://viblo.asia/p/cac-cau-lenh-vim-ma-cac-developer-nen-biet-ByEZkLyglQ0
