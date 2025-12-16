# XÁC ĐỊNH VÀ ĐẶC ĐIỂM HÓA NGƯỜI DÙNG QUYỀN LỰC TRONG THREADS

## Giới thiệu
Dự án này tập trung vào việc xác định và đặc điểm hóa người dùng quyền lực (power users) trong mạng xã hội Threads thông qua phân tích mạng xã hội (Social Network Analysis - SNA). Hai phương pháp chính được sử dụng:

1. **Phân tích các chỉ số centrality truyền thống**: Degree, Closeness, Betweenness, Eigenvector.
2. **Opsahl Generalized Degree Centrality**: Kết hợp số lượng kết nối và trọng số tương tác để xác định power users.

## Mục tiêu
- Xây dựng quy trình phân tích để xác định power users trong mạng xã hội Threads.
- Phân tích vai trò của power users trong việc lan truyền thông tin và kết nối mạng.
- Cung cấp các kết quả định lượng và trực quan hóa để hỗ trợ nghiên cứu.

## Cấu trúc dự án
Dự án bao gồm các tệp chính sau:

### 1. `Define_Power_User.ipynb`
- **Mục tiêu**: Phân tích các chỉ số centrality truyền thống để xác định power users.
- **Nội dung chính**:
  - Đọc và tiền xử lý dữ liệu từ `users.csv` và `posts.csv`.
  - Tính toán các chỉ số centrality: Degree, Closeness, Betweenness, Eigenvector.
  - Phân tích và trực quan hóa kết quả.
  - Xuất danh sách power users dựa trên các chỉ số truyền thống.
  - So sánh với tập a=0.5 từ opsahl với các phương pháp, chỉ số

### 2. `opsahl_power_user_users_posts.ipynb`
- **Mục tiêu**: Áp dụng Opsahl Generalized Degree Centrality để xác định power users.
- **Nội dung chính**:
  - Đọc và tiền xử lý dữ liệu từ `users.csv` và `posts.csv`.
  - Trích xuất các cạnh tương tác và tổng hợp trọng số.
  - Xây dựng đồ thị mạng xã hội và tính toán Opsahl centrality.
  - Phân tích và trực quan hóa sự thay đổi thứ hạng của các nút theo giá trị alpha.
  - Xuất danh sách power users dựa trên tứ phân vị thứ ba (Q3).

## Quy trình phân tích
1. **Tiền xử lý dữ liệu**:
   - Đọc dữ liệu từ `users.csv` và `posts.csv`.
   - Chuẩn hóa tên cột và ánh xạ danh tính người dùng.
2. **Tính toán các chỉ số centrality**:
   - Sử dụng các chỉ số truyền thống và Opsahl centrality để đánh giá vai trò của từng người dùng.
3. **Phân tích và trực quan hóa**:
   - Phân tích sự phân bố của các chỉ số centrality.
   - Vẽ biểu đồ thay đổi thứ hạng và xác định nhóm power users.
4. **Xuất kết quả**:
   - Lưu bảng xếp hạng và danh sách power users vào các tệp CSV.

## Kết quả
- **Danh sách power users**:
  - Được xác định dựa trên các chỉ số centrality truyền thống và Opsahl centrality.
  - Power users chiếm khoảng 1.1% tổng số người dùng, đóng vai trò quan trọng trong mạng xã hội.
- **Biểu đồ và bảng số liệu**:
  - Trực quan hóa sự phân bố và vai trò của power users trong mạng.

## Yêu cầu hệ thống
- Python 3.8 trở lên.
- Các thư viện:
  - pandas
  - numpy
  - networkx
  - matplotlib

## Hướng dẫn sử dụng
1. **Cài đặt thư viện**:
   ```bash
   pip install pandas numpy networkx matplotlib
   ```
2. **Chạy các notebook**:
   - Mở và chạy lần lượt các notebook `Define_Power_User.ipynb` và `opsahl_power_user_users_posts.ipynb`.
3. **Kết quả**:
   - Kết quả được lưu trong các tệp CSV:
     - `opsahl_rankings_all.csv`
     - `opsahl_power_alpha05_Q3.csv`

### Chi tiết notebook `Define_Power_User.ipynb`

Notebook này thực hiện các bước sau để xác định người dùng quyền lực trong mạng xã hội Threads:

1. **Nhập thư viện và cấu hình I/O**:
   - Sử dụng các thư viện như `pandas`, `numpy`, `networkx`, `matplotlib`, và `scipy`.
   - Thiết lập thư mục dữ liệu đầu vào (`Threads_Dataset`) và đầu ra (`output`).
2. **Đọc và chuẩn hóa dữ liệu**:
   - Đọc dữ liệu từ các tệp `users.csv` và `posts.csv`.
   - Chuẩn hóa các cột dữ liệu như `user_url`, `post_url`, và `parent_url` để đảm bảo tính nhất quán.
   - Lọc các bài đăng để chỉ giữ lại những bài có tác giả nằm trong danh sách người dùng hợp lệ.
3. **Xây dựng ánh xạ**:
   - Tạo ánh xạ từ `post_url` đến `author_user_url` để xác định tác giả của các bài đăng và các liên kết cha mẹ.

Notebook này là bước đầu tiên trong việc phân tích mạng xã hội Threads, tập trung vào việc chuẩn bị dữ liệu và xây dựng cơ sở cho các phân tích tiếp theo.

---
**Người thực hiện**: Nhóm 16 IS353.Q11

**Ngày hoàn thành**: 12/12/2025