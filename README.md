# K26CNTT2_IT108_Session10_Ex05
Bài tập số 5

# Phần 1. Thiết kế Kiến trúc Luồng Dữ Liệu (Mô hình IPO)

Mô tả chi tiết luồng xử lý dữ liệu tuyển dụng tự động hóa từ khâu tiếp nhận hồ sơ đến khi phát hành thư mời phỏng vấn:

### 1. Phân tích các thành phần trong mô hình IPO

- **Input (Dữ liệu đầu vào):**
  - Hồ sơ đăng ký tuyển dụng của ứng viên (Họ tên, Email, Số điện thoại).
  - Điểm đánh giá chuyên môn (Thang điểm 10).
  - Trình độ kỹ năng ngoại ngữ (IELTS, TOEIC, hoặc cấp độ giao tiếp).
  - Vị trí ứng tuyển (1 trong 5 vị trí Lập trình viên của Startup).

- **Process (Xử lý & Sàng lọc):**
  - Quản lý và chuẩn hóa dữ liệu ứng viên trong bảng tính `Quan_Ly_Ung_Vien.xlsx` tuân thủ 5 Quy tắc Vàng Database.
  - Sử dụng công cụ **Filter** trong Excel để lọc danh sách thỏa mãn đồng thời 2 điều kiện:
    - `Điểm chuyên môn > 8`
    - `Kỹ năng ngoại ngữ` đạt yêu cầu.
  - Áp dụng tính năng **Mail Merge (Trộn thư)** để tự động điền thông tin các ứng viên đạt yêu cầu từ Excel vào mẫu `Thu_Moi_Phong_Van_Mau.docx`.

- **Output (Kết quả đầu ra):**
  - Danh sách ứng viên trúng tuyển vòng hồ sơ đã được lọc.
  - Các Thư mời phỏng vấn (Invitation Letter) cá nhân hóa hoàn chỉnh tương ứng cho từng ứng viên đạt tiêu chuẩn.

---

### 2. Bảng tóm tắt mô hình IPO quy trình tuyển dụng

| Thành phần IPO | Chức năng trong hệ thống | Chi tiết thực thi trong bài toán |
| :--- | :--- | :--- |
| **Input (Đầu vào)** | Thu thập dữ liệu hồ sơ | Nhập thông tin ứng viên, điểm chuyên môn, ngoại ngữ vào Excel |
| **Process (Xử lý)** | Phân loại & Tự động hóa | Bật Filter lọc (Điểm > 8 & Ngoại ngữ) + Trộn thư Mail Merge |
| **Output (Đầu ra)** | Trích xuất sản phẩm | Xuất danh sách đạt chuẩn và file Thư mời phỏng vấn hoàn chỉnh |

---

## Phần 2. Mô tả thiết kế sản phẩm

### 1. Cấu trúc file Word mẫu thư mời (`Thu_Moi_Phong_Van_Mau.docx`)
- **Định dạng Styles chuẩn:**
  - Tiêu đề công ty / Thư mời: Sử dụng `Heading 1` và `Heading 2`.
  - Các mục thông tin chi tiết: Sử dụng `Heading 2`.
  - Nội dung thư: Sử dụng nhãn `Normal`.
- **Nhãn thông tin Trộn thư (Mail Merge Fields):**
  - `«Ho_Ten»` - Họ và tên ứng viên.
  - `«Vi_Tri_Ung_Tuyen»` - Vị trí Lập trình viên ứng tuyển.
  - `«Thoi_Gian_PV»` - Thời gian ấn định phỏng vấn.
  - `«Dia_Diem_PV»` - Địa điểm hoặc Link phỏng vấn online.

---

### 2. Bảng quản lý ứng viên Excel (`Quan_Ly_Ung_Vien.xlsx`)
Tuân thủ **5 Quy tắc Vàng Database**:
1. **Dòng tiêu đề duy nhất:** Chỉ có 1 hàng Header ở dòng đầu tiên, không gộp ô (Merge cells).
2. **Dữ liệu nguyên tử (Atomic Data):** Tách riêng Họ tên, Email, Số điện thoại, Điểm số thành từng cột độc lập.
3. **Không có dòng/cột trống:** Cấu trúc dữ liệu liên tục để bộ lọc Filter hoạt động chính xác.
4. **Định dạng dữ liệu thống nhất:** Cột "Điểm chuyên môn" để dạng Number, cột "Mã ứng viên" để dạng Text/Code.
5. **Không tính toán chung vào vùng dữ liệu:** Không chèn các dòng Total/Average ngắt đoạn bảng dữ liệu.

---

## Phần 3. Danh sách kiểm tra hoàn thiện (Task List)

- [x] Thiết kế xong sơ đồ luồng dữ liệu IPO trong file `README.md`
- [x] Tạo file Word `Thu_Moi_Phong_Van_Mau.docx` gắn chuẩn Heading Styles và nhãn Mail Merge
- [x] Tạo file Excel `Quan_Ly_Ung_Vien.xlsx` chuẩn Database và thiết lập bộ lọc Filter (Điểm > 8 & Ngoại ngữ)
- [ ] Push toàn bộ các file lên GitHub Repository theo đúng quy định tên repo: `K26CNTT2_IT108_Session10_Ex05`
