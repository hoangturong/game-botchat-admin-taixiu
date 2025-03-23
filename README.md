Markdown

# Luck Dice - Hệ thống game cá cược trực tuyến 

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg) 
![License](https://img.shields.io/badge/License-MIT-green.svg) 

Luck Dice là một hệ thống game cá cược trực tuyến được xây dựng bằng Python, sử dụng Flask và SocketIO để cung cấp trải nghiệm chơi game thời gian thực. Dự án bao gồm ba thành phần chính: **server**, **client** (người chơi), và **admin** (quản trị viên). Người chơi có thể tham gia các trò chơi như Tài Xỉu, Chẵn Lẻ, Bầu Cua, đặt cược, trò chuyện, và đổi mã quà tặng (gifcode). Quản trị viên có thể quản lý người chơi, cố định kết quả game, tạo/xóa gifcode, và xem kết quả các phiên chơi. 

## Ảnh chụp màn hình 

### Giao diện người chơi 

![Giao diện người chơi](https://img.upanh.tv/2025/03/24/Screenshot-303.png) 

### Giao diện quản trị viên ️

![Giao diện quản trị viên](https://img.upanh.tv/2025/03/24/Screenshot-301.png) 

## Tính năng chính ✨

### Server ️

- Xử lý logic game (Tài Xỉu, Chẵn Lẻ, Bầu Cua). 
- Quản lý phiên chơi (mỗi phiên 60 giây). 
- Lưu trữ dữ liệu người chơi, cược, tin nhắn, và gifcode bằng SQLite. 
- Giao tiếp thời gian thực với client/admin qua WebSocket. 
- Tích hợp tính năng ẩn cửa sổ cmd khi chạy (Windows). 

### Client (Người chơi) 

- Giao diện đồ họa (GUI) sử dụng Tkinter. 
- Đăng ký, đăng nhập, và quản lý tài khoản. 
- Tham gia các trò chơi: Tài Xỉu, Chẵn Lẻ, Bầu Cua. 
- Đặt cược và xem kết quả thời gian thực. 
- Trò chuyện với người chơi khác. 
- Đổi mã quà tặng (gifcode) để nhận xu. 
- Xem lịch sử chơi. 
- Nhận 100k xu miễn phí khi đăng ký tài khoản mới. 

### Admin (Quản trị viên) ️

- Giao diện đồ họa (GUI) sử dụng Tkinter. 
- Đăng nhập bằng tài khoản admin. 
- Cố định kết quả game (Tài Xỉu, Chẵn Lẻ, Bầu Cua). 
- Quản lý người chơi: cấm/mở cấm, đặt số xu. 
- Quản lý gifcode: tạo, xóa, xem danh sách. 
- Xem kết quả chi tiết của các phiên chơi (bao gồm danh sách cược). 

## Công nghệ sử dụng ️

- **Python 3.10+** (khuyến nghị, Python 3.6 cũng hỗ trợ nhưng cần phiên bản thư viện cũ hơn). 
- **Flask**: Framework cho server API. 
- **Flask-JWT-Extended**: Quản lý xác thực người dùng. 
- **Flask-SocketIO**: Giao tiếp thời gian thực qua WebSocket. 
- **python-socketio**: Client WebSocket cho client/admin. 
- **Tkinter**: Xây dựng giao diện đồ họa cho client và admin. 
- **SQLite**: Cơ sở dữ liệu để lưu trữ thông tin. 
- **requests**: Gửi HTTP request từ client/admin đến server. 

## Yêu cầu hệ thống ⚙️

- Python 3.10+ (khuyến nghị) hoặc Python 3.6 (tối thiểu). 
- Hệ điều hành: Windows, Linux, macOS. 
- Trình quản lý gói: `pip`. 

## Cài đặt ️

### 1. Clone repository 

```bash
git clone [https://github.com/](https://github.com/)<your-username>/luck-dice.git 
cd luck-dice
```
2. Cài đặt Python
Windows/macOS: Tải Python 3.10+ từ python.org và cài đặt.

Linux:

```Bash

sudo apt-get update 
sudo apt-get install python3.10 python3.10-venv python3-pip
```
hoặc cài từ nguồn:

```Bash

sudo apt-get install -y build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev curl libbz2-dev 
wget [https://www.python.org/ftp/python/3.10.12/Python-3.10.12.tgz](https://www.python.org/ftp/python/3.10.12/Python-3.10.12.tgz) 
tar -xzf Python-3.10.12.tgz 
cd Python-3.10.12 
./configure --enable-optimizations 
make -j$(nproc) 
sudo make altinstall
```
3. Cài đặt các thư viện
Tạo môi trường ảo (khuyến nghị):

```Bash

python3.10 -m venv venv 
source venv/bin/activate # Linux/macOS 
venv\Scripts\activate # Windows
```
Cài đặt các thư viện từ requirements.txt:

```Bash

pip install -r requirements.txt
```
Nội dung requirements.txt (cho Python 3.10+):

```Plaintext

Flask==3.0.3 
Flask-JWT-Extended==4.6.0 
Flask-SocketIO==5.3.6 
python-socketio==5.8.0 
python-engineio==4.5.0 
requests==2.32.3
```
Nếu bạn dùng Python 3.6 (không khuyến nghị):

```Plaintext

Flask==2.0.3 
Flask-JWT-Extended==4.4.4 
Flask-SocketIO==5.3.6 
python-socketio==5.8.0 
python-engineio==4.5.0 
requests==2.28.2
```
Lưu ý: Tkinter thường đi kèm với Python. Nếu thiếu: Linux: sudo apt-get install python3-tk Windows/macOS: Đảm bảo cài Python từ python.org.

4. Cấu hình
File server: Server.py
File client: Game.py
File admin: Luck_Dice_Admin.py
Cơ sở dữ liệu: game_global.db (tự động tạo khi chạy server).
Đặt lại JWT_SECRET_KEY trong api.py để đảm bảo bảo mật.
Hướng dẫn chạy ️
1. Chạy server
```Bash

python Server.py
```
Server sẽ chạy trên http://localhost:9999. Đảm bảo không có chương trình nào chiếm cổng 9999.

2. Chạy client (người chơi)
```Bash

python Game.py
```
Đăng ký tài khoản mới hoặc đăng nhập. Mặc định: Nhận 100k xu khi đăng ký.

3. Chạy admin (quản trị viên)
```Bash

python Luck_Dice_Admin.py
```
Đăng nhập bằng tài khoản admin (Password đã đặt khi tạo user admin).

4. Build Game.
```
auto-py-to-exe
```
5. lƯU Ý
   Tôi đã build exe rồi chỉ cần tải phần mềm exe đã build sẵn về chỉ cần thay ip và port.
   Tại:
 ```text
 data/config/config.txt
 ```

# Cách chơi ️

Người chơi

Đăng nhập vào Game.

Chọn trò chơi (Tài Xỉu, Chẵn Lẻ, Bầu Cua).

Đặt cược trong thời gian 60 giây mỗi phiên.

Xem kết quả và nhận thưởng (thắng: nhận gấp đôi số xu cược).

Đổi gifcode để nhận thêm xu.

Trò chuyện với người chơi khác.

Quản trị viên ️

Đăng nhập vào admin.

Cố định kết quả game nếu cần.

Quản lý người chơi: cấm/mở cấm, đặt số xu.

Tạo/xóa gifcode.

Xem kết quả chi tiết các phiên chơi.

# Cấu trúc thư mục

```Plaintext

luck-dice/ 
├── Server.py # File server xử lý logic game và giao tiếp với client/admin.
├── Luck_Dice_Admin.py #File quản lý quả admin đối với server game.
├── Game.py # File giao diện người chơi, cho phép đặt cược và trò chuyện. 
├── Bot.py # File giao diện quản trị viên
```
