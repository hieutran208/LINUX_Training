**THAO TÁC VỚI TIẾN TRÌNH VÀ TRÌNH QUẢN LÝ TÁC VỤ**

**A. Các câu lệnh thường dùng để theo dõi và quản lý tiến trình**

*Tiến trình: Tiến trình là các chương trình chạy trên hệ thống. PID là số hiệu tiến trình, dùng để nhận biết các tiến trình*

*1. Các câu lệnh ps thường dùng để kiểm tra thông tin tiến trình*

- Hiển thị tất cả các tiến trình trên hệ thống: ps aux (có thể thay bằng 'ps -ef' để kết quả ngắn gọn hơn nhưng sẽ không đầy đủ bằng)
- Hiển thị tiến trình theo tên người dùng: ps –U [tên người dùng]
- Hiển thị tiến trình theo PID: ps -ef -p [các pid cần hiển thị]
- Hiển thị các cột cần thiết của tiến trình đang chạy: ps -e -o [tên các cột cần hiển thị]
- Hiển thị các cột cần thiết và sắp xếp theo cách sử dụng: ps –e -o [tên các cột cần hiển thị] --sort=<tiền tố>[cột cần sắp xếp]

(*Đây cũng là câu lệnh có thể sử dụng để hiển thị tiến trình chiếm nhiều CPU và RAM nhất)

(Tiền tố: “+” sắp xếp theo thứ tự tăng dần, “-” sắp xếp theo thứ tự giảm dần) 

- Tra cứu một tiến trình bất kì dựa trên tên của nó: ps aux | grep <từ khoá>

(*Câu lệnh này có thể dùng để tra cứu PID của tiến trình hoặc để kiểm tra một phần mềm có hoạt động hay không)

*2. Lệnh top/htop để hiển thị trạng thái tiến trình*

a. Lệnh top 
- Giống như ps, top cũng có chức năng hiển thị thông tin tiến trình nhưng nâng cao hơn khi danh sách tiến trình được update liên tục. Ngoài ra có bổ sung thêm nhiều thông số quan trọng như: phân phối CPU, cấp phát bộ nhớ,…giúp dễ dàng theo dõi trạng thái hoạt động của hệ thống, phòng tránh xung đột và bế tắc xảy ra, tối ưu hoá hoạt động của CPU
- Cú pháp: top (Muốn tắt top để về terminal, ta nhấn Ctrl + Z)

b. Lệnh htop
- Câu lệnh htop cũng hiển thị đầy đủ các thông tin như top nhưng có một số tính năng nâng cao hơn như: dùng màu sắc để hiển thị thông tin hệ thống (CPU, RAM, swap), phím tắt để quản lý tiến trình,....
- Muốn sử dụng htop ta phải cài về bằng lệnh: sudo apt install htop
- Cú pháp: htop (Muốn tắt htop để về terminal, ta nhấn Ctrl + Z)

*3. Sử dụng lệnh kill để dừng tiến trình*
- Thông thường, để kết thúc một tiến trình ta dùng cú pháp: *kill <PID tiến trình>*. Đây là cú pháp mặc định, gọi là sigterm
- Nguyên lý hoạt động:
  - Khi sử dụng lệnh kill để yêu cầu dừng một tiến trình, thực tế ta chỉ đang yêu cầu kernel gửi một tín hiệu đến tiến trình đó.
  - Kernel nhận lệnh: Kernel của HĐH sẽ nhận tín hiệu này và gửi tín hiệu (signal) tới tiến trình mục tiêu
  - Tiến trình sẽ nhận tín hiệu từ kernel:
    - nếu là SIGTERM thì có thể nhận tín hiệu này và có thể xử lý nó
    - nếu là SIGKILL (tín hiệu không thể bị chặn hoặc xử lý) thì nó sẽ ngay lập tức bị kết thúc mà không có cơ hội để xử lý hay giải phóng tài nguyên.
- Phân biệt giữa sigterm và sigkill (kill -9)
  - Sigterm: Gửi tín hiệu yêu cầu tự kết thúc tới tiến trình. Đây là tín hiệu yêu cầu tiến trình tự kết thúc một cách an toàn, lưu trữ dữ liệu và giải phóng tài nguyên trước khi dừng.
  - Sigkill: Ép buộc tiến trình kết thúc ngay lập tức mà không cho phép tiến trình xử lý bất kì công việc nào. Do vậy tiến trình không có thời gian để xử lý dữ liệu hoặc giải phóng tài nguyên. Thường chỉ dùng khi tiến trình không phản hồi tín hiệu sigterm thông thường

=> SIGTERM là tín hiệu dừng tiến trình đúng đắn, cho phép tiến trình thực hiện các thao tác cần thiết trước khi kết thúc, như lưu trữ dữ liệu và giải phóng tài nguyên. SIGKILL chỉ nên được sử dụng khi SIGTERM không phản hồi hoặc khi tiến trình treo và không thể dừng bằng cách thông thường. Việc sử dụng SIGKILL có thể gây ra một số hậu quả như mất dữ liệu hoặc tạo tiến trình zombie gây ra vấn đề trong việc quản lý tài nguyên.

**B. Ý nghĩa các thông số khi theo dõi tiến trình**

*1. Các thông số tiến trình khi hiển thị thông tin với lệnh ps*
![image](https://github.com/user-attachments/assets/66a42ee3-7613-474a-a5e4-7b5c717ad806)

Ý nghĩa các trường trong bảng hiển thị thông tin tiến trình:
- USER: Tên người dùng thực hiện tiến trình
- PID: Số hiệu (ID định danh) của tiến trình
- %CPU: % sử dụng CPU của tiến trình
- %MEM: % sử dụng bộ nhớ của tiến trình
- VSZ: Kích thước bộ nhớ ảo sử dụng bởi tiến trình (tổng bộ nhớ ảo mà tiến trình yêu cầu)
- RSS: Kích thước bộ nhớ thực sử dụng bởi tiến trình (tiêu thụ thực tế của tiến trình trong RAM)
- TYY: Tên thiết bị đầu cuối điều khiển, nếu không có sẽ thấy “?”
- STAT: Trạng thái của tiến trình (S: sleeping; Ss: là tiến trình lãnh đạo phiên, ở trạng thái sleeping; I: rảnh rỗi; R: đang chạy)
- START: Thời gian bắt đầu của tiến trình 
- TIME: Tổng thời gian sử dụng CPU của tiến trình
- COMMAND: Tên tiến trình (Câu lệnh thực hiện)

*2. Các thông số khi hiển thị thông tin với lệnh top*

a. Các thông số hệ thống
![image](https://github.com/user-attachments/assets/d2311744-2f17-4262-87a7-b26bc961fb0d)

Ý nghĩa các thông số hệ thống tại các dòng trong phần khoanh đỏ:

- Dòng đầu tiên lần lượt hiển thị các thông số về hệ thống:  
  - Thời gian hiện tại của hệ thống: là thời gian thực tế mà máy chủ đang sử dụng để tính toán và đo lường các sự kiện
  - Thời gian uptime: Thời gian hệ thống hoạt động kể từ lần hoạt động cuối cùng
  - Số lượng người dùng đã log in
  - Mức độ tải trung bình của CPU  trong 1 phút, 5 phút và 15 phút qua.

- Dòng thứ 2 lần lượt hiển thị tổng số tác vụ và số tác vụ theo trạng thái: 
  - Tổng số tác vụ trên máy chủ
  - Số tác vụ đang chạy
  - Số tác vụ đang trong trạng thái ngủ
  - Số tác vụ ở trạng thái dừng
  - Số tác vụ ở trạng thái zombie (đã dừng nhưng chưa được giải phóng)

- Dòng thứ 3 hiển thị phân phối CPU lần lượt như sau: 
  - us: Phần trăm phân phối cho tiến trình người dùng
  - sy: Phần trăm phân phối cho tiến trình hệ thống 
  - ni: Phần trăm phân phối cho tiến trình có mức độ ưu tiên thấp
  - id: Phần trăm CPU đang rảnh
  - wa: Phần trăm CPU để đợi khi các tiến trình I/O đang xử lí (wa)
  - hi: Phần trăm CPU để xử lí các gián đoạn phần cứng
  - si: Phần trăm CPU để xử lí các gián đoạn phần mềm
  - st: Phần trăm CPU do máy ảo sử dụng 

- Dòng thứ 4 lần lượt hiển thị các thông số về bộ nhớ vật lý (RAM) :
  - Tổng dung lượng RAM cài đặt trên hệ thống
  - Bộ nhớ trống
  - Bộ nhớ đã sử dụng
  - Dung lượng đang được dùng làm bộ đệm (buffer) và bộ nhớ cache

- Dòng thứ 5 lần lượt hiển thị các thông số về swap space (Swap là RAM ảo, được sử dụng khi bộ nhớ vật lý (RAM) bị đầy):
  - Tổng swap có sẵn (kB)
  - Tổng swap còn trống
  - Tổng swap đã sử dụng
  - Bộ nhớ khả dụng

b. Các thông số tiến trình
![image](https://github.com/user-attachments/assets/900f7e26-a522-4ae6-901a-e7d27fe7dd81)

Ý nghĩa các trường trong bảng hiển thị thông tin tiến trình:
- PID: Số hiệu (ID định danh) của tiến trình
- USER: Tên người dùng thực hiện tiến trình
- PR: Mức độ ưu tiên (20 là mức mặc định; 0 là mức cao nhất; rt là mức đặc biệt dành cho các tiến trình real-time)
- NI: Mức độ nice (PR = 20 + NI)
- VIRT: Kích thước bộ nhớ ảo sử dụng bởi tiến trình
- RES: Kích thước bộ nhớ thực sử dụng bởi tiến trình
- SHR: Kích thước bộ nhớ có thể chia sẻ với các tiến trình khác
- S: Trạng thái của tiến trình (S: sleeping; Ss: là tiến trình lãnh đạo phiên, ở trạng thái sleeping; I: rảnh rỗi; R: đang chạy)
- %CPU: % sử dụng CPU của tiến trình
- %MEM: % sử dụng bộ nhớ của tiến trình
- TIME+: Thời gian tiến trình đã được chạy
- COMMAND: Tên tiến trình (Câu lệnh thực hiện)

=> Nếu mục đích sử dụng là để theo dõi trạng thái hoạt động của toàn hệ thống thì sử dụng lệnh top. Nếu mục đích sử dụng là trích xuất các thông tin cụ thể của tiến trình thì sử dụng lệnh ps 

- us:
  - Phần trăm thời gian CPU dành để thực hiện các chương trình do người dùng chạy (như trình duyệt, game,...)
  - Nếu chỉ số này cao (70%), có thể hệ thống đang chạy nhiều ứng dụng người dùng hoặc phần mềm nặng. Hệ thống có thể chậm hơn nếu CPU không đủ mạnh 
- sy
  - Phần trăm thời gian CPU dành để thực hiện các tác vụ của HĐH (quản lý bộ nhớ, hệ thống tệp, và các dịch vụ hệ thống)
  - Trên 30% là mức cần chú ý, vì khi hệ điều hành chiếm quá nhiều tài nguyên CPU, điều đó có thể chỉ ra các vấn đề về các tác vụ nền (sao lưu, quét virus, hoặc bảo trì hệ thống), điều này có thể gây ảnh hưởng đến hiệu suất các ứng dụng người dùng.
- id
  - Phần trăm thời gian mà CPU ở trạng thái nhàn rỗi.
  - Nếu chỉ số này trên 80%, nghĩa là hệ thống không có tác vụ nặng và không sử dụng hết tài nguyên CPU.
- st
  - Phần trăm thời gian  CPU dành để chạy các tác vụ liên quan đến máy ảo (Virtual Box, VMWare,...)
  - Từ 20% có thể chỉ ra rằng các máy ảo đang chiếm dụng quá nhiều tài nguyên CPU của hệ thống vật lý, làm giảm hiệu suất của các ứng dụng trên máy vật lý.
- wa
  - Phần trăm thời gian CPU ở trạng thái chờ đợi dữ liệu khi yêu cầu dữ liệu từ các thiết bị I/O (như ổ đĩa, mạng.)
  - Từ 20-30% là mức cần chú ý. Điều này cho thấy hệ thống đang gặp phải tắc nghẽn I/O (ổ đĩa cứng chậm, SSD đầy, hoặc vấn đề về đến mạng)

*3. Các thông số khi hiển thị thông tin với lệnh htop*
![image](https://github.com/user-attachments/assets/1892c745-4518-4e8d-89bf-5e9bbef241de)

Về cơ bản, tên các cột hiển thị thông tin tiến trình sẽ giống với lệnh top. Tuy nhiên có chút khác biệt khi có một số phần thông tin hệ thống (CPU, RAM, SWAP) được hiển thị dưới dạng thanh ngang có màu sắc:
- CPU Usage: Hiển thị nhiều thanh ngang màu sắc giúp dễ dàng theo dõi mức độ sử dụng CPU (màu xanh là phần CPU đang làm việc với các tác vụ người dùng, màu đỏ là phần CPU đang làm việc với các tác vụ hệ thống, màu xám là phần CPU ở trạng thái rảnh rỗi). Nếu có nhiều nhân CPU thì mỗi nhân sẽ có 1 thanh riêng biệt
- Memory Usage: Cung cấp thông tin về bộ nhớ RAM và swap (Xanh dương (Blue): Dành cho bộ nhớ "cache". Đây là bộ nhớ mà hệ thống giữ lại để tăng tốc độ truy cập dữ liệu, có thể được giải phóng khi cần thiết; Xanh lá cây (Green): Bộ nhớ đang sử dụng bởi các tiến trình. Đây là bộ nhớ được phân bổ cho các ứng dụng đang chạy; Vàng (Yellow): Buffers — Đây là bộ nhớ được sử dụng để lưu trữ tạm thời các dữ liệu (ví dụ như các buffer của hệ thống tệp); Đỏ (Red): Bộ nhớ swap (được sử dụng trên ổ đĩa). Màu đỏ cảnh báo về việc hệ thống đang sử dụng swap, điều này có thể làm giảm hiệu suất vì swap chậm hơn rất nhiều so với RAM; Tím (Magenta): Kernel hoặc bộ nhớ liên quan đến hệ điều hành (kernel memory).)

*4. Ý nghĩa chỉ số load average*
- Load Average (trung bình tải): thể hiện **trung bình số process mà server phải thực hiện trong một khoảng thời gian**. Khi sử dụng câu lệnh top/htop để theo dõi tiến trình, load average được hiển thị dưới dạng 3 số liên tiếp nhau, biểu thị số process trung bình mà server phải thực hiện trong 1, 5 và 15 phút vừa qua
- Ý nghĩa thông số:
  - Load Average = Số core CPU: Khi load average gần bằng số lượng CPU cores, hệ thống hoạt động ở mức hiệu suất tối ưu, không bị quá tải.
  - Load Average < Số core CPU: Hệ thống không bị quá tải, có thể có ít tiến trình hoặc hệ thống đang ở trạng thái ít bận rộn.
  - Load Average > Số core CPU: Hệ thống có thể bị quá tải, nếu tiến trình cần CPU nhiều hơn số lượng core có sẵn, tốc độ xử lý sẽ bị chậm đi.
- Các nguyên nhân làm tăng loadAVG
  - CPU Utilization: mức sử dụng CPU tăng cao, hệ thống sẽ bị quá tải, dẫn đến thời gian phản hồi chậm hoặc giảm hiệu suất
  - Disk I/O (Hoạt động Đọc/Ghi đĩa): Nếu hệ thống phải thực hiện quá nhiều thao tác đọc/ghi vào ổ đĩa (nhất là với các ổ cứng HDD, thường có tốc độ chậm hơn SSD), tốc độ truy cập dữ liệu sẽ giảm, dẫn đến tắc nghẽn và tăng độ trễ.
  - Network Traffic (Lưu lượng mạng): Nếu có quá nhiều dữ liệu được truyền tải qua mạng, băng thông có thể bị vượt quá, dẫn đến nghẽn mạng và làm giảm tốc độ truyền tải.

**C. Byobu và cách sử dụng byobu**

*Byobu là một công cụ quản lý phiên terminal giúp bạn tạo và quản lý nhiều cửa sổ (windows) trong cùng một phiên làm việc, nó giúp quản lý nhiều tác vụ và phiên làm việc cùng lúc mà không bị mất tiến trình khi ngắt kết nối.*

*1. Lợi ích khi sử dụng byobu*
- Quản lý nhiều phiên làm việc trong cùng một cửa sổ terminal: Byobu cho phép tạo và quản lý nhiều phiên làm việc (session) trong cùng một cửa sổ terminal mà không cần phải mở nhiều terminal, có thể dễ dàng chuyển đổi giữa các phiên làm việc mà không bị gián đoạn công việc, giúp tối ưu hóa việc sử dụng tài nguyên và quản lý các tiến trình.
- Giữ trạng thái phiên làm việc: Khi làm việc với máy chủ từ xa qua SSH, nếu không may kết nối bị gián đoạn thì khi kết nối lại cũng sẽ có thể giữ nguyên trạng thái phiên chứ không cần phải chạy lại các tiến trình từ đầu
- Phù hợp với các tiến trình dài hạn: Khi chạy các tiến trình dài hạn với máy chủ từ xa, ta có thể tách khỏi phiên làm việc và tiến trình vẫn tiếp tục chạy ở phía máy chủ

*2. Các thao tác sử dụng cơ bản*

a. Khởi động byobu
- Cài đặt byobu về máy: sudo apt install byobu
- Khởi động byobu: byobu

b. Tạo, Đóng và Đổi tên cửa sổ byobu
- Tạo cửa sổ mới:
  - Nhấn F2 để mở một cửa sổ mới.
  - Đóng cửa sổ hiện tại: Nhấn Ctrl + D hoặc gõ lệnh exit trong cửa sổ để đóng nó.
- Đổi tên cửa sổ: Nhấn F8, sau đó nhập tên mới cho cửa sổ và nhấn Enter.

c. Chuyển đổi qua lại giữa các cửa sổ
- Di chuyển tới cửa sổ kế tiếp: Nhấn F3.
- Di chuyển tới cửa sổ trước đó: Nhấn F4.

d. Chia và quản lý trong một cửa sổ
- Chia cửa sổ theo chiều dọc: Nhấn Shift + F2.
- Chia cửa sổ theo chiều ngang: Nhấn Ctrl + F2.
- Di chuyển giữa các khung: Sử dụng Shift + mũi tên.
  
e. Đóng Byobu và tất cả các cửa sổ: gõ lệnh byobu kill-session.
