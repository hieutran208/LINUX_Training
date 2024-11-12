**LAB 2**

1. Tạo 2 máy ảo Urbuntu trong VMWare

a. Cài đặt VMWare và file ISO Urbuntu về máy (đã đề cập ở file 1)

b. Tạo máy ảo Urbuntu trên VMWare (làm tương tự với máy ảo thứ 2)
- Mở VMware Workstation/Player.
- Chọn "Create a New Virtual Machine" (Tạo máy ảo mới).
- Chọn "Typical (recommended)" và nhấn Next.
- Chọn file ISO: Chọn "Installer disc image file (iso)" và duyệt tới file ISO đã tải.
- Đặt tên cho máy ảo và chọn vị trí lưu trữ: Đặt tên như "Ubuntu_VM1" và chọn thư mục lưu.
- Cấu hình phần cứng:
  - Processor: Chọn số lượng lõi CPU mà bạn muốn cấp cho máy ảo (ít nhất 1 lõi).
  - Memory: Chọn dung lượng RAM (ví dụ 2 GB).
  - Hard Disk: Để mặc định hoặc điều chỉnh dung lượng ổ cứng ảo (ít nhất 20 GB).
- Hoàn thành và tạo máy ảo: Nhấn Finish để hoàn thành quá trình tạo máy ảo.

2. Gán vào ổ cứng 60GB (làm tương tự với máy ảo thứ 2)
- Tắt Urbuntu. Trong menu VMWare nhấp chuột phải vào máy cần gán ổ cứng, chọn Setting
- Trong menu setting, chọn Hard Disk và nhấn Add
- Chọn Hard Disk, sau đó chọn loại ổ cứng là SATA hoặc SCSI (SATA thích hợp cho mục đích thử nghiệm hơn vì cấu hình đơn giản)
- Chọn Create a new virtual disk (Tạo một ổ cứng ảo mới).
- Chọn dung lượng ổ cứng là 60 GB.
- Chọn Store virtual disk as a single file (Lưu ổ cứng ảo dưới dạng một file duy nhất).
- Nhấn Next, sau đó chọn nơi lưu trữ tệp ổ cứng ảo (thường là thư mục mặc định).
- Nhấn Finish để hoàn thành việc thêm ổ cứng mới.
- Mở lại Urbuntu và kiểm tra, ta có thông tin ổ cứng vừa tạo
![image](https://github.com/user-attachments/assets/5e4619c7-84ee-4575-a801-3ef1e6d4e76d)

3. Phân vùng ổ cứng (làm tương tự với máy ảo thứ 2)
