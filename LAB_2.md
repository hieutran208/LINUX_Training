**LAB 2**

**1. Tạo 2 máy ảo Urbuntu trong VMWare**

a. Cài đặt VMWare và download file ISO Urbuntu về máy 
- Tải xuống file ISO của Ubuntu Server từ trang chính thức: https://ubuntu.com/download/server
- Tải file .bundle của VMWare từ trang chính thức, sau đó cd vào thư mục download và cài về máy

b. Tạo một máy ảo Urbuntu trên VMWare (tương tự với máy ảo thứ 2)
- Mở VMware Workstation/Player.
- Chọn "Create a New Virtual Machine" (Tạo máy ảo mới).
- Chọn "Typical (recommended)" và nhấn Next.
- Chọn file ISO: Chọn "Installer disc image file (iso)" và duyệt tới file ISO đã tải.
- Đặt tên cho máy ảo và chọn vị trí lưu trữ: Đặt tên như "Ubuntu_1" và chọn thư mục lưu.
- Cấu hình phần cứng:
  - Processor: Chọn số lượng lõi CPU mà bạn muốn cấp cho máy ảo (ít nhất 1 lõi).
  - Memory: Chọn dung lượng RAM (ví dụ 2 GB).
  - Hard Disk: Để mặc định hoặc điều chỉnh dung lượng ổ cứng ảo (ít nhất 20 GB).
- Hoàn thành và tạo máy ảo: Nhấn Finish để hoàn thành quá trình tạo máy ảo.
- Bật Urbuntu và làm theo hướng dẫn để hoàn tất cài đặt

**2. Gán vào ổ cứng 60GB (tương tự với máy ảo thứ 2)**

a. Disk và ổ đĩa
- Disk là thiết bị lưu trữ vật lý (HDD, SSD,CD,...).
- Ổ đĩa là thiết bị sử dụng disk để lưu trữ và truy xuất dữ liệu, bao gồm một/nhiều đĩa và cơ chế đọc/ghi dữ liệu từ đĩa

b. Các bước gán ổ cứng
- Tắt Urbuntu. Trong menu VMWare nhấp chuột phải vào máy cần gán ổ cứng, chọn Setting
- Trong menu setting, chọn Hard Disk và nhấn Add
- Chọn Hard Disk, sau đó chọn loại ổ cứng là SATA hoặc SCSI (SATA thích hợp cho mục đích thử nghiệm vì cấu hình đơn giản hơn)
- Chọn Create a new virtual disk (Tạo một ổ cứng ảo mới).
- Chọn dung lượng ổ cứng là 60 GB.
- Chọn Store virtual disk as a single file (Lưu ổ cứng ảo dưới dạng một file duy nhất).
- Nhấn Next, sau đó chọn nơi lưu trữ tệp ổ cứng ảo (thường là thư mục mặc định).
- Nhấn Finish để hoàn thành việc thêm ổ cứng mới.
- Mở lại Urbuntu và kiểm tra bằng lệnh fdisk -l, ta có thông tin ổ cứng 60 GB vừa gán
![image](https://github.com/user-attachments/assets/5e4619c7-84ee-4575-a801-3ef1e6d4e76d)

**3. Phân vùng ổ cứng (làm tương tự với máy ảo thứ 2)**
- Khởi động fdisk: sudo fdisk /dev/sdb
- Phân vùng ổ cứng /dev/sdb: Diễn giải cách chia phân vùng 1 10GB, 2 phân vùng còn lại làm tương tự
  - Tạo phân vùng mới bằng cách nhấn n + ENTER
  - Chọn loại (p: primary; e:extend (nếu muốn tạo thêm phân vùng con))
  - Chọn kích thước: Chọn sector bắt đầu và sector kết thúc của phân vùng để tính kích thước (1 sector = 512 bytes)
  - Ghi thay đổi và thoát fdisk: nhấn w + ENTER (không muốn ghi thay đổi nhấn q)
  - Làm tương tự với 2 phân vùng còn lại, ta chia được 3 phân vùng của ổ cứng như sau:
![image](https://github.com/user-attachments/assets/016cce58-4d70-4543-b93e-b167732dced4)
- Định dạng phân vùng:
  - sudo mkfs.ext4 /dev/sdb1
  - sudo mkfs.xfs /dev/sdb2 (cài thêm xfsprogs)
  - sudo mkfs.ext3 /dev/sdb3
- Tạo thư mục gán và gán các phân vùng vào thư mục tương ứng:
  - sudo mkdir /data1 /data2 /data3
  - sudo mount /dev/sdb1 /data1
  - sudo mount /dev/sdb2 /data2
  - sudo mount /dev/sdb3 /data3
- Kiểm tra lại cấu hình phân vùng bằng lệnh df -T (-T hiển thị thêm loại file system của mỗi phân vùng), ta có kết quả như sau:
![image](https://github.com/user-attachments/assets/51e463d7-dde7-42bf-b1db-517f58a84d2b)

**4. Cách để phân vùng tự mount mỗi khi reboot**
   
*Để phân vùng tự mount mỗi khi reboot, ta cần cấu hình trên file /etc/fstab (file cấu hình các thiết bị lưu trữ và cách gán chúng vào hệ thống)*
- Mở file /etc/fstab để chỉnh sửa: vim /etc/fstab
- Mỗi dòng trong file đại diện cho 1 thiết bị/phân vùng và cách nó được gán, các mục từ trái qua phải mang ý nghĩa:
  -  Tên thiết bị hoặc phân vùng (ví dụ: /dev/sda1 hoặc UUID).
  -  Thư mục nơi phân vùng sẽ được mount (ví dụ: /data1).
  -  Loại hệ thống file (ví dụ: ext4, xfs, ext3).
  -  Các tùy chọn mount (mặc định có thể là defaults).
  -  Thường là 0 (tùy chọn sao lưu, thường không cần thay đổi).
  -  Thứ tự kiểm tra hệ thống file khi boot (thường là 0 hoặc 1).
- Thêm các dòng cho từng phân vùng như ảnh sau

![image](https://github.com/user-attachments/assets/93fc3d56-a7e4-4be5-856d-a70035c4b420)
- Lưu lại tệp và thoát
- Kiểm tra lại tệp /etc/fstab ,nếu không báo lỗi tức là tệp cấu hình đã đúng : sudo mount -a
