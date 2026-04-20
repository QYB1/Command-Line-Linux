## Install/Unistall Software (Cài đặt/Gỡ cài đặt gói)
### Mục lục

[1. Install/Uninstall Software (Cài đặt/Gỡ cài đặt)](#caidat)

[2. Build/Cài đặt gói từ source code](#build)

====================================================
<a name="caidat"></a>
## 1. Install/Uninstall Software
### Sử dụng APT để cài đặt
- **Cập nhật danh sách gói**: Trước khi cài đặt phần mềm, bạn nên cập nhật danh sách các gói để đảm bảo bạn có phiên bản mới nhất của gói.
```sh
sudo apt update
```
- **Cài đặt một gói**: Sử dụng lệnh apt install để cài đặt gói.
```sh
sudo apt install vim
```
- **Cài đặt nhiều gói cùng lúc**: Bạn có thể cài đặt nhiều gói cùng lúc bằng cách liệt kê chúng ra sau lệnh
```sh
sudo apt install vim git curl
```
### Sử dụng APT để gỡ cài đặt phần mềm
- **Gỡ cài đặt một gói**: Sử dụng lệnh apt remove để gỡ cài đặt phần mềm mà vẫn giữ lại các tệp cấu hình.
```sh
sudo apt remove vim
```
- **Gỡ cài đặt hoàn toàn một gói**: Sử dụng lệnh apt purge để gỡ bỏ hoàn toàn phần mềm cùng với các tệp cấu hình.
```sh
sudo apt purge vim
```
- **Xóa các gói không cần thiết (auto-remove)**: Sau khi gỡ cài đặt phần mềm, bạn có thể sử dụng lệnh apt autoremove để xóa các gói phụ thuộc không còn cần thiết
```sh
sudo apt autoremove
```
