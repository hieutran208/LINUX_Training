**LAB 3**

*1. Tạo 1 máy ảo và gán vào 7 đĩa cùng dung lượng*

a. Tạo máy ảo Urbuntu server
- Mở VMware Workstation/Player.
- Chọn "Create a New Virtual Machine" (Tạo máy ảo mới).
- Chọn "Typical (recommended)" và nhấn Next.
- Chọn file ISO: Chọn "Installer disc image file (iso)" và duyệt tới file ISO Urbuntu server đã tải.
- Đặt tên cho máy ảo và chọn vị trí lưu trữ: Đặt tên như "Ubuntu_1" và chọn thư mục lưu.
- Cấu hình phần cứng:
  - Processor: Chọn số lượng lõi CPU mà bạn muốn cấp cho máy ảo (ít nhất 1 lõi).
  - Memory: Chọn dung lượng RAM (ví dụ 2 GB).
  - Hard Disk: Để mặc định hoặc điều chỉnh dung lượng ổ cứng ảo (ít nhất 20 GB).
- Hoàn thành và tạo máy ảo: Nhấn Finish để hoàn thành quá trình tạo máy ảo.

b. Thêm ổ đĩa (tương tự với các ổ còn lại)
- Tắt Urbuntu. Trong menu VMWare nhấp chuột phải vào máy cần gán ổ cứng, chọn Setting
- Trong menu setting, chọn Hard Disk và nhấn Add
- Chọn Hard Disk, sau đó chọn loại ổ cứng là SATA hoặc SCSI (SATA thích hợp cho mục đích thử nghiệm vì cấu hình đơn giản hơn)
- Chọn Create a new virtual disk (Tạo một ổ cứng ảo mới).
- Chọn dung lượng ổ cứng.
- Chọn Store virtual disk as a single file (Lưu ổ cứng ảo dưới dạng một file duy nhất).
- Nhấn Next, sau đó chọn nơi lưu trữ tệp ổ cứng ảo (thường là thư mục mặc định).
- Nhấn Finish để hoàn thành việc thêm ổ cứng mới.

*2. Cài HĐH vào 2 ổ cứng đầu tiên cấu hình softraid1*
- Khởi động máy ảo Urbuntu server, để vào trình cài đặt ta chọn "Try or Install Urbuntu" trong màn hình tùy chọn
- Tiến hành cài đặt: Chọn mặc định các tùy chọn trong trình cài đặt (ngôn ngữ, mạng, loại caì đặt), đến phần "Guide storage configuration" chọn "Custom storage layout" (tùy chỉnh cấu hình lưu trữ) để cấu hình RAID 1
- Tạo phân vùng có dung lượng tầm 1GB trên mỗi ổ dành cho /boot, phần còn lại dành để chứa HĐH. Việc tạo phân vùng cho /boot giúp đảm bảo khả năng khởi động của hệ thống ngay cả khi một trong 2 ổ đĩa gặp sự cố, ngoài ra nếu không tạo phân vùng, công cụ có thể không xem ổ đĩa là một thiết bị hợp lệ để tham gia vào mảng RAID
- **Cấu hình RAID 1:** nhấn vào "Create software RAID", ta có các tùy chọn để tạo RAID
  - Chọn RAID level là RAID 1.
  - Chọn các ổ đĩa/phân vùng muốn tạo RAID
  - Sau khi mảng RAID 1 được tạo, nó sẽ xuất hiện dưới dạng một thiết bị mới (/dev/md0).
  - Định dạng file system phù hợp (ext4)
  - Đặt điểm gắn kết của mảng RAID trong hệ thống (/ nếu mảng RAID dùng để chứa HĐH)
  - Nhấn "Create" để xác nhận
- Tạo mảng RAID dùng để chứa HĐH (/dev/md0) và RAID dành cho boot (/dev/md1) theo các bước như trên, sau đó nhấn Done
- Các bước tiếp theo làm như hướng dẫn để hoàn thành cài đặt

*3. Cấu hình RAID cho 2 ổ dùng RAID 0 và 2 ổ dùng RAID 1*

a. Cấu hình RAID
- sudo mdadm --create /dev/md1 --level=0 --raid-device=2 /dev/sdd /dev/sde
- sudo mdadm --create /dev/md2 --level=1 --raid-device=2 /dev/sdf /dev/sdg

b. Tạo file system cho các mảng raid
- sudo mkfs.ext4 /dev/md1
- sudo mkfs.ext4 /dev/md2

c. Tạo thư mục gán và gán các mảng raid vào hệ thống
- sudo mkdir /mnt/raid1 /mnt/raid2
- sudo mount /dev/md1 /mnt/raid1
- sudo mount /dev/md2 /mnt/raid2

d. Chỉnh sửa trong file cấu hình các thiết bị lưu trữ để các mảng raid tự động mount mỗi khi reboot
- Vào file cấu hình /etc/fstab và thêm các dòng như sau:
  
  ![image](https://github.com/user-attachments/assets/1bbb332b-2449-4fdf-afe0-da0e1541289f)
- Cập nhật file cấu hình mdadm:
  - sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
- Cập nhật initramfs (đảm bảo hệ thống nhận diện được RAID trong quá trình khởi động)
  - sudo update-initramfs -u

*4. Dùng sysbench đánh giá tốc độ của RAID 0 và RAID 1 so với 1 đĩa đơn*

a. 
