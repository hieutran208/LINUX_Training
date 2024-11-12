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
- Vào file cấu hình /etc/fstab và thêm các dòng như sau:

![image](https://github.com/user-attachments/assets/b059c243-3bf1-4b7d-9188-e07cc37e5d59)
- Cập nhật file cấu hình mdadm:
  - sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
- Cập nhật initramfs (đảm bảo hệ thống nhận diện được RAID trong quá trình khởi động)
  - sudo update-initramfs -u

3. Cài HĐH vào mảng RAID chứa 2 ổ cứng đầu tiên
   
