**IP, DNS và GATEWAY**

**A. IP động và IP tĩnh**

*1. Khái niệm và trường hợp sử dụng*
- Gateway là điểm trung gian giúp các thiết bị trong mạng nội bộ giao tiếp với internet (thường là router hoặc modem)
- IP (Internet Protocol) là địa chỉ dùng để nhận diện thiết bị trên mạng, có 2 loại là IP động và IP tĩnh
- IP động:
  - Là địa chỉ được máy chủ DHCP tự động cấp phát cho các thiết bị khi kết nối vào mạng từ một dải IP đã cấu hình trước. IP động thay đổi mỗi khi thiết bị kết nối lại vào mạng
  - Máy chủ DHCP là một dịch vụ tự động cấp phát địa chỉ IP được tích hợp trên máy chủ hay các thiết bị mạng
  - Trường hợp dùng IP động:
    - Khi có một số thiết bị kết nối vào mạng gia đình thì sử dụng IP động giúp không phải cấu hình thủ công cho từng thiết bị một
    - Các thiết bị cá nhân hoặc di động không cần địa chỉ IP cố định (máy tính cá nhân, điện thoại,....). Chúng sẽ tự động nhận một IP động khi kết nối vào mạng Wi-Fi.
- IP tĩnh
  - Là địa chỉ được cấu hình thủ công cho 1 thiết bị, không thay đổi qua các lần kết nối khác nhau
  - Trường hợp dùng IP tĩnh:
    - Các máy chủ hay thiết bị mạng cần một địa chỉ IP cố định để các thiết bị khác kết nối vào
    - Các thiết bị từ xa như camera giám sát cần IP tĩnh để các thiết bị khác có thể truy cập một cách ổn định

*2. Cấu hình trên Urbuntu*

a. Cấu hình IP động
- Khi cấu hình IP động, cổng mạng sẽ tự động nhận một địa chỉ IP từ máy chủ DHCP
- Urbuntu dùng netplan để cấu hình mạng. Để cấu hình IP động ta mở thư mục /etc/netplan, tìm file cấu hình .yaml và chỉnh sửa trong file này
- Để cấu hình IP động cho cổng mạng ens33, ta cần thay đổi tệp như sau:

  ![image](https://github.com/user-attachments/assets/654b358d-80db-41ea-86aa-cdf999daadc7)
  - network: (Dưới phần này sẽ khai báo toàn bộ các cấu hình mạng trong hệ thống)
  - version: 2 (Đây là phiên bản Netplan, phiên bản 2 là phiên bản phổ biến hiện nay và hỗ trợ các tính năng mới nhất)
  - renderer: networkd
    - renderer chỉ ra công cụ hệ thống sử dụng để cấu hình mạng.
    - networkd là công cụ thường được sử dụng cho máy chủ hoặc các hệ thống không có giao diện đồ họa. Nếu dùng Ubuntu Desktop sẽ là NetworkManage
  - ethernets (ethernets là phần khai báo cho mạng có dây. Nếu cấu hình mạng Wi-Fi thì sử dụng wifis thay vì ethernets)
  - ens33 (tên cổng mạng muốn cấu hình)
  - dhcp4: true (có nghĩa là cổng ens33 sẽ nhận địa chỉ IP IPv4 tự động thông qua giao thức DHCP)
- Lưu và thoát khỏi tệp cấu hình, sau đó dùng lệnh sudo netplan apply để áp dụng cấu hình

b. Cấu hình IP tĩnh 
- Khi cấu hình IP tĩnh, cổng mạng sẽ có một địa chỉ IP cố định
- Để cấu hình IP tĩnh ta cũng dùng vim chỉnh sửa trong file .yaml như trên
- Để cấu hình IP tĩnh cho cổng mạng ens33, ta cần thay đổi tệp như sau:

  ![image](https://github.com/user-attachments/assets/5ecbb528-b252-463c-8c71-1944137dfe57)
  - dhcp4: false (Khi cấu hình IP tĩnh, cần đặt dhcp4: false để tắt chế độ nhận địa chỉ IP tự động từ máy chủ DHCP.)
  - addresses: (addresses là danh sách các địa chỉ IP muốn gán cho interface ens33)
    - Địa chỉ IP được chỉ định phải có mặt nạ mạng (subnet mask), ví dụ: 192.168.1.100/24
      - 192.168.1.100: Đây là địa chỉ IP tĩnh muốn gán cho cổng mạng ens33.
      - /24 là mặt nạ mạng (subnet mask), có nghĩa là 24 bit đầu tiên trong địa chỉ IP sẽ được sử dụng để xác định mạng con (subnet). Trong trường hợp này, mặt nạ mạng là 255.255.255.0, cho phép tối đa 254 thiết bị trong cùng một mạng con.
  - gateway4: chỉ ra địa chỉ IP của gateway mặc định cho cổng mạng ens33. Gateway là địa chỉ của router hoặc thiết bị kết nối vào mạng ngoài (Internet). Trong ví dụ trên, gateway4: 192.168.1.1 có nghĩa là địa chỉ của router hoặc gateway trong mạng của bạn là 192.168.1.1.
  - nameservers chỉ định các máy chủ DNS (Domain Name System) mà hệ thống sẽ sử dụng để phân giải tên miền thành địa chỉ IP. Trong ví dụ trên, hệ thống sẽ sử dụng Google DNS với các địa chỉ IP:
    - 8.8.8.8: Đây là một máy chủ DNS công cộng của Google.
    - 8.8.4.4: Đây là một máy chủ DNS khác của Google.
