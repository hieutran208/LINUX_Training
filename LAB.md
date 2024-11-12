**LAB 2**

1. Tạo 2 máy ảo Urbuntu trong VMWare (mục này làm như đã trình bày ở file 1)

a. Cài đặt VMWare và download file ISO Urbuntu về máy 

b. Tạo máy ảo Urbuntu trên VMWare (làm tương tự với máy ảo thứ 2)

2. Gán vào ổ cứng 60GB (làm tương tự với máy ảo thứ 2)

a. Disk và ổ đĩa
- Disk chỉ đơn giản là đĩa lưu trữ vật lý (ví dụ: HDD, SSD).
- Ổ đĩa là thiết bị dùng để chứa, đọc và ghi dữ liệu vào disk, nó có thể chứa một hoặc nhiều disk.

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

3. Phân vùng ổ cứng (làm tương tự với máy ảo thứ 2)
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

4. Cách để phân vùng tự mount mỗi khi reboot
   
*Để phân vùng tự mount mỗi khi reboot, ta cần cấu hình trên file /etc/fstab (file cấu hình các thiết bị lưu trữ và cách gán chúng vào hệ thống)*
- Mở file /etc/fstab để chỉnh sửa: vim /etc/fstab
- Mỗi dòng trong file đại diện cho 1 thiết bị/phân vùng và cách nó được gán
  - <device>   <mount_point>   <filesystem_type>   <options>   <dump>   <pass>
  - <device>: Tên thiết bị hoặc phân vùng (ví dụ: /dev/sda1 hoặc UUID).
  - <mount_point>: Thư mục nơi phân vùng sẽ được mount (ví dụ: /data1).
  - <filesystem_type>: Loại hệ thống file (ví dụ: ext4, xfs, ext3).
  - <options>: Các tùy chọn mount (mặc định có thể là defaults).
  - <dump>: Thường là 0 (tùy chọn sao lưu, thường không cần thay đổi).
  - <pass>: Thứ tự kiểm tra hệ thống file khi boot (thường là 0 hoặc 1).
- Thêm các dòng cho các phân vùng như ảnh sau

![image](https://github.com/user-attachments/assets/df31e3a9-3caa-4380-9b15-26a2861060fe)
- Lưu lại tệp và thoát
- Kiểm tra lại tệp /etc/fstab ,nếu không báo lỗi tức là tệp cấu hình đã đúng : sudo mount -a


**LAB 3**

1. Tạo 1 máy ảo với 7 disk cùng dung lượng (thực hiện tương tự như LAB 2)

2. Cấu hình RAID cho 6 ổ cứng đầu tiên (2 ổ đầu dùng softraid1, 2 ổ tiếp theo dùng RAID 0, 2 ổ cuối cùng dùng RAID 1)

a. Cấu hình RAID
- 2 ổ đầu tiên: sudo mdadm --create /dev/md0 --level=1 --raid-device=2 /dev/sdb /dev/sdc
- 2 ổ tiếp theo: sudo mdadm --create /dev/md1 --level=0 --raid-device=2 /dev/sdd /dev/sde
- 2 ổ cuối cùng: sudo mdadm --create /dev/md2 --level=1 --raid-device=2 /dev/sdf /dev/sdg

b. Tạo file system cho các mảng raid
- sudo mkfs.ext4 /dev/md0
- sudo mkfs.ext4 /dev/md1
- sudo mkfs.ext4 /dev/md2

c. Tạo thư mục gán và gán các mảng raid vào hệ thống
- sudo mkdir /mnt/raid0 /mnt/raid1 /mnt/raid2
- sudo mount /dev/md0 /mnt/raid0
- sudo mount /dev/md1 /mnt/raid1
- sudo mount /dev/md2 /mnt/raid2

d. Chỉnh sửa trong file cấu hình các thiết bị lưu trữ để các mảng raid tự động mount mỗi khi reboot
![image](https://github.com/user-attachments/assets/b059c243-3bf1-4b7d-9188-e07cc37e5d59)
