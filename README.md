# Command-Line-Linux
Một số lệnh cơ bản trong Linux

[1. Kiến thức cơ bản về các khối lệnh trong Linux](#lenhlinux)
[2. Kiến thức các khối lệnh cơ bản dùng dể xử lý văn bản](#vanban)

==================================================================
<a name="lenhlinux"></a>
## 1. Kiến thức cơ bản về các khối lệnh trong Linux
### Quản lý phần cứng
- `lscpu:` Hiển thị thông tin về CPU của hệ thống
- `lshư:` Hiển thị thông tin chi tiết về phần cứng của máy tính, bao gồm CPU, bộ nhớ, thiết bị lưu trữ, và mạng
- `lsusb:` Hiển thị danh sách các thiết bị USB đang được kết nối
- `lspci:` Hiển thị thông tin về các thiết bị kết nối qua bus PCI
- `df -h:` Hiển thị tổng quan về không gian ổ đĩa đã sử dụng và còn trống trên các phân vùng hệ thống

### Quản lý đĩa (Disk Management)
- `fdisk:` Quản lý các phân vùng trên ổ đĩa. Ví dụ: sudo fdisk /dev/sdX (sdX là ổ đĩa bạn muốn quản lý)
- `lsblk:` Hiển thị các khối thiết bị (block devices) và phân vùng của chúng
- `df:` Kiểm tra dung lượng ổ đĩa
- `du:` Kiểm tra dung lượng sử dụng của các thư mục hoặc tệp. Ví dụ: du -sh /path/to/directory
- `mkfs:` Tạo hệ thống tập tin trên phân vùng. Ví dụ: sudo mkfs.ext4 /dev/sdXn (sdXn là phân vùng bạn muốn format)

### Quản lý tệp (File Management)
- `ls:` Liệt kê tệp và thư mục trong một thư mục. Câu lệnh: ls -l
- `cp:` Sao chép tệp hoặc thư mục. Câu lệnh: cp source_file destination_file
- `mv:` Di chuyển hoặc đổi tên tệp. Câu lệnh: mv old_file_name new_file_name
- `rm:` Xóa tệp hoặc thư mục. Câu lệnh: rm file_name
- `chmod:` Thay đổi quyền truy cập của tệp hoặc thư mục. Ví dụ: chmod 755 file_name
- `chown:` Thay đổi quyền sở hữu của tệp hoặc thư mục. Câu lệnh: sudo chown user:group file_name
- `find:` Tìm kiếm tệp và thư mục theo tên. Câu lệnh: find /path -name "file_name"

### Quản lý tiến trình (Proccess Management)
- `ps:` Hiển thị danh sách các tiến trình đang chạy. Câu lệnh: ps aux
- `top:` Giám sát tiến trình đang chạy theo thời gian thực. Câu lệnh: top
- `htop:` Giám sát tiến trình với giao diện người dùng cải tiến so với top (cần cài đặt). Câu lệnh: htop
- `kill:` Dừng một tiến trình bằng ID. Câu lệnh: kill PID (PID là ID của tiến trình bạn muốn dừng, killall: Dừng tất cả các tiến trình có cùng tên)
- `nice và renice:` Điều chỉnh độ ưu tiên của tiến trình. Câu lệnh: nice -n 10 proccess_name (Chạy tiến trình với độ ưu tiên 10)
- `netstat:` Hiển thị thong tin về các kết nối mạng, port mở, và trạng thái mạng.
```sh
netstat -pnlt
```
- `ss:` Giống netstat nhưng nhanh hơn và hiệu quả hơn trong việc hiển thị các socket đang mở
```sh
ss -tuln
```
- `lsof:` Hiển thị thông tin về các tệp và port mà tiến trình đang mở
```sh
lsof -i :port_number
```
- `nmap:` Quét các port mở trên một máy (cần cài đặt)
```sh
nmap localhost
```
- `ufw:` Quản lý tường lửa (firewall) trên hệ thống Ubuntu, có thể cho phép hoặc từ chối các kết nối port
```sh
sudo ufw allow 22 #**Mở port 22 (SSH)**
sudo ufw deny 80 #**Chặn port 80 (HTTP)**
sudo ufw status #**Kiểm tra trạng thái firewall**
```
- `cat:` Hiển thị nội dung tệp văn bản hoặc nối nhiều tệp với nhau.
```sh
cat file.txt # Hiển thị nội dung của file.txt
```
- `nano:` Trình chỉnh sửa văn bản đơn giản và dễ sử dung.
```sh
nano file.txt
```
- `vi và vim:` Trình soạn thảo văn bản mạnh mẽ, vim là phiên bản nâng cao của vi.
```sh
vi file.txt
vim file.txt
```
- `grep:` Dùng để tìm kiếm chuỗi trong tệp hoặc kết quả của lệnh khác.
```sh
grep "chuỗi cần tìm" file.txt
```
- `sed:` Dùng để xử lý và thay đổi nội dung văn bản trong tệp hoặc luồng dữ liệu.
```sh
sed 's/old/new/g' file.txt # Thay thế 'old' bằng 'new' trong file.txt
```

<a name="vanban"></a>
## 2. Kiến thức các khối lệnh cơ bản dùng để xử lý văn bản
### Lệnh cat
#### 1. Cú pháp cơ bản
cat <tùy chọn> <tệp>
#### 2. Các trường hợp sử dụng phổ biến của lệnh cat:
- Hiển thị nội dung của tệp
```sh
cat filename.txt
```
- Nối (ghép) nhiều tệp lại với nhau
```sh
cat file1.txt file2.txt > merged.txt
```
- Tạo một tệp văn bản mới (Nhập nội dung từ bàn phím)
```sh
cat > newfile.txt
```

### Lệnh nano
#### 1. Cú pháp cơ bản: nano <tên tệp>
#### 2. Các thao tác cơ bản với nano
- Mở tệp để chỉnh sửa
```sh
nano myfile.txt
```
- Lưu tệp: Sau khi chỉnh sửa, để lưu tệp, nhấn Ctrl + O (Write Out). Sau đó, nano sẽ yêu cầu xác nhận tên tệp. Nhấn Enter để lưu tệp với tên hiện tại.
- Thoát khỏi nano: nhấn Ctrl + X. Nhấn Y để lưu, hoặc N để thoát mà không lưu.
- Cắt (cut): Để cắt một dòng, di chuyển con trỏ đển dòng đó và nhấn Ctrl + K
- Dán (paste): Để dán văn bản đã cắt, nhấn Ctrl + U
- Sao chép (copy): Di chuyển con trỏ đến điểm bắt đầu, nhấn Alt + 6 để sao chép dòng hoặc một đoạn văn bản đã chọn
- Tìm kiếm văn bản: Nhấn Ctrl + W để tìm kiếm một từ hoặc chuỗi trong tệp. Nhập từ khóa bạn muốn tìm và nhấn Enter
- Thay thế văn bản: Nhấn Ctrl + \ để bắt đầu thay thế. Bạn sẽ được yêu cầu nhập từ khóa cần thay thế và từ mới để thay thế

### Lệnh vi và vim
#### 1. Cú pháp cơ bản
```sh
vi filename.txt
vim filename.txt
```
#### 2. Các thao tác cơ bản với vi/vim
- Chế độ bình thường (Normal mode): Đây là chế độ mặc định khi bạn mở vi/vim. Bạn có thể điều hướng, sao chép, dán, xóa, và di chuyển trong tệp nhưng không thể nhập văn bản. Để quay lại chế độ bình thường từ bất kỳ chế độ nào khác, nhấn phím Esc
- Chế đọ Insert (Insert mode): Trong chế độ này, bạn có thể nhập và chỉnh sửa văn bản. Để chuyển sang chế độ chèn, nhấn một trong các phím sau:
  - i: Chèn tại vị trí con trỏ chuột
  - I: Chèn ở đầu dòng hiện tại
  - a: Chèn sau con trỏ
  - A: Chèn ở cuối dòng hiện tại
  - o: Chèn một dòng mới phía dưới dòng hiện tại
  - O: Chèn một dòng mới phía trên dòng hiện tại
  - Để quay lại chế độ bình thường. Nhấn Esc
- Chế độ lệnh (Command mode)
  - Trong chế độ này, bạn có thể thực hiện các lệnh như lưu tệp, thoát, tìm kiếm, thay thế, v.v
  - Để chuyển sang chế độ lệnh từ chế độ bình thường, nhấn dấu : (dấu hai chấm)
  - Sau khi nhập lệnh, nhấn Enter để thực thi

### Lệnh Grep
#### 1. Cú pháp cơ bản
```sh
grep <tùy chọn> "chuỗi_cần_tìm" <tên tệp>
```
#### 2. Các tùy chọn cơ bản của lệnh Grep
- Tìm kiếm không phân biệt chữ hoa/thường
  - Dùng tùy chọn -i để tìm kiếm không phân biệt chữ hoa và chữ thường
    ```sh
    grep -i "Linux" example.txt
    ```
- Hiển thị số dòng chứa chuỗi tìm kiếm
  - Dùng tùy chọn -n để hiển thị số dòng nơi tìm thấy chuỗi
    ```sh
    grep -n "Linux" example.txt
    ```
- Hiển thị số dòng tìm thấy (count)
  - Dùng tùy chọn -c để đếm số dòng chứa chuỗi tìm kiếm
    ```sh
    grep -c "Linux" example.txt
    ```
- Tìm kiếm chính xác từ (whole word match)
  - Dùng tùy chọn -w để tìm những dòng chứa từ hoàn chỉnh (không phải một phần của từ khác)
    ```sh
    grep -w "Linux" example.txt
    ```
- Hiển thị các dòng không chứa chuỗi
  - Dùng tùy chọn -v để hiển thị những dòng không chứa chuỗi tìm kiếm
    ```sh
    grep -v "Linux" example.txt
    ```
- Tìm kiếm trong nhiều tệp
  - Bạn có thể tìm kiếm trong nhiều tệp cùng lúc
    ```sh
    grep "Linux" file1.txt file2.txt
    ```
- Kết hợp grep với các lệnh khác
  - Tìm kiếm trong kết quả của một lệnh khác: Dùng grep để tìm kiếm trong kết quả của các lệnh khác thông qua pipe (|)
    ```sh
    ps aux | grep "root"
    ```
