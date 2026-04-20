## Quản lý người dùng, Phân quyền người dùng

### Mục lục
[1. Quản lý người dùng](#chmod)

[2. Phân quyền người dùng](#chown)

==================================================
<a name="chmod"></a>
## 1. Quản lý người dùng
### Tạo người dùng mới
- Bạn có thể sử dụng lệnh adduser hoặc useradd để tạo người dùng mới. Sau khi chạy lệnh này, hệ thống sẽ yêu cầu bạn cung cấp mật khẩu cho người dùng và một số thông tin bổ sung như tên đầy đủ, số điện thoại,...
```sh
sudo adduser username
```

- Sử dụng useradd: Đây là lệnh cấp thấp hơn so với adduser và yêu cầu nhiều tùy chọn hơn. Lệnh passwd sẽ giúp bạn thiết lập mật khẩu cho người dùng.
```sh
sudo useradd -m username
sudo passwd username
```

### Xóa người dùng
- Để xóa một người dùng khỏi hệ thống, bạn có thể sử dụng lệnh deluser hoặc userdel.
  - Sử dụng deluser
    ```sh
    sudo deluser username
    ```
  - Sử dụng userdel, tùy chọn -r sẽ xóa luôn thư mục home của người dùng
    ```sh
    sudo userdel -r username
    ```

### Sửa thông tin người dùng
- Bạn có thể chỉnh sửa thông tin người dùng, như tên đầy đủ hoặc shell đăng nhập bằng lệnh usermod
- Thay đổi shell mặc định:
  ```sh
  sudo usermod -s /bin/bash username
  ```
- Đổi tên người dùng:
  ```sh
  sudo usermod -l newusername oldusername
  ```
- Thay đổi thư mục home của người dùng:
  ```sh
  sudo usermod -d /new/home/path username
  ```

### Khóa và mở tài khoản người dùng
- Khóa tài khoản:
  ```sh
  sudo usermod -L username
  ```
- Mở khóa tài khoản:
  ```sh
  sudo usermod -U username
  ```

### Quản lý nhóm
- Tạo nhóm mới:
  ```sh
  sudo groupadd groupname
  ```
- Thêm người dùng vào nhóm, tùy chọn -aG sẽ thêm người dùng vào nhóm mà không xóa họ khỏi các nhóm khác
  ```sh
  sudo usermod -aG groupname username
  ```
- Xóa người dùng khỏi nhóm
  ```sh
  sudo gpasswd -d username groupname
  ```
- Xem nhóm của một người dùng
  ```sh
  groups username
  ```

<a name="chown"></a>
## 2. Phân quyền người dùng

### Quyền đọc, ghi, thực thi (rwx)
- Linux sử dụng 3 loại quyền chính cho tệp và thư mục:
  - r: Quyền đọc (read)
  - w: Quyền ghi (write)
  - x: Quyền thực thi (execute)
  - Các quyền này được áp dụng cho chủ sở hữu (user), nhóm (group), và người khác (others). Bạn có thể xem quyền của tệp hoặc thư mục bằng lệnh ls -l.
  ```sh
  -rw-r--r--
  ```
  - Chủ sở hữu (Owner) có quyền đọc và ghi (rw-)
  - Nhóm (Group) có quyền đọc (r--)
  - Những người khác (others) cũng chỉ có quyền đọc (r--)

### Thay đổi quyền tệp và thư mục
= Để thay đổi quyền tệp, bạn sử dụng lệnh chmod
- Thay đổi quyền theo kiểu ký tự:
  ```sh
  chmod u+rwx filename # Thêm quyền đọc, ghi, thực thi cho chủ sở hữu
  chmod g-w filename # Bỏ quyền ghi cho nhóm
  chmod o+x filename # Thêm quyền thực thi cho người khác
  ```
- Thay đổi quyền bằng cách sử dụng giá trị số:
  ```sh
  chmod 755 filename
  ```
  - 7 = đọc (4) + ghi (2) + thực thi (1)
  - 5 = đọc (4) + thực thi (1)
  - Quyền 755 có nghĩa là: Chủ sở hữu có toàn quyền (rwx), còn lại nhóm và người dùng khác chỉ có quyền đọc và thực thi (r-x)

### Thay đổi chủ sở hữu và nhóm của tệp/thư mục
- Thay đổi chủ sở hữu của tệp:
  ```sh
  sudo chown newuser filename
  ```
- Thay đổi nhóm sở hữu của tệp:
  ```sh
  sudo chown :newgroup filename
  ```
- Thay đổi cả chủ sở hữu và nhóm sở hữu cùng lúc:
  ```sh
  sudo chown newuser:newgroup filename
  ```

### Sử dụng sudo để cấp quyền quản trị
- Trong Ubuntu, người dùng thông thường không có quyền truy cập vào các tệp hệ thống hoặc cài đặt phần mềm. Để cấp quyền quản trị cho người dùng, bạn có thể thêm họ vào nhóm sudo
  - Thêm người dùng vào nhóm sudo
    ```sh
    sudo usermod -aG sudo username
    ```

