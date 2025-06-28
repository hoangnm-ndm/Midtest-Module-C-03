# Hướng dẫn làm bài - Bài kiểm tra ReactJS nâng cao

- **Thời gian làm bài**: 150 phút.
- **Yêu cầu môi trường**:
  - Tải Repositỏy mẫu này về máy và thực hiện code trực tiếp trong thư mục này.
  - Sau khi hoàn thành, đẩy code lên GitHub repository cá nhân (đặt ở chế độ **public**) và gửi link repo qua Google Classroom. Không được commit thêm sau khi nộp bài.
  - **Tắt tất cả các extension AI** (như Tabnine, GitHub Copilot, Codeium, v.v.) trong quá trình làm bài.
  - Được phép sử dụng các tài liệu tham khảo giao diện như **TailwindCSS**, **Bootstrap**, **Material-UI**, **Boxicons**, hoặc **FontAwesome**.
- **Công cụ backend**: Sử dụng `json-server` để mock API (cài đặt: `npm install -g json-server`).

## Yêu cầu

Xây dựng ứng dụng **Project Management System (PMS)** sử dụng **ReactJS** và **json-server**, với các tính năng sau:

## 1. Giao diện và Routing (1 điểm)

- Dữ liệu được cung cấp sẵn trong file `db.json` với các thực thể: **Projects**, **Tasks**, và **Users**.
- Xây dựng hệ thống định tuyến với các trang:
  - **Trang danh sách dự án**: Hiển thị tất cả dự án, trạng thái (đang thực hiện, hoàn thành, tạm dừng), và tiến độ (% hoàn thành).
  - **Trang chi tiết dự án**: Hiển thị thông tin dự án và danh sách các nhiệm vụ (tasks) thuộc dự án.
  - **Trang hồ sơ người dùng**: Hiển thị thông tin người dùng và danh sách các dự án/nhiệm vụ họ được giao.
- Xử lý **route không tồn tại (404)** với giao diện lỗi thân thiện, có nút quay lại trang chủ.
- Giao diện phải thân thiện, dễ sử dụng, sử dụng **TailwindCSS**, **Bootstrap**, hoặc **Material-UI** để đảm bảo tính thẩm mỹ.

## 2. Quản lý Dự án (Projects) (2 điểm)

- **GET**: Lấy danh sách dự án từ API và hiển thị thông tin: tên, mô tả, ngày bắt đầu, ngày kết thúc dự kiến, trạng thái, và tiến độ (tiến độ tính theo %).
- **POST**: Thêm dự án mới thông qua form (bao gồm tên, mô tả, ngày bắt đầu, ngày kết thúc, trạng thái, tiến độ).
- **PUT**: Cập nhật thông tin dự án (bao gồm thay đổi trạng thái và tiến độ).
- **DELETE**: Xóa dự án (thêm xác nhận trước khi xóa).
- **Validation**: Đảm bảo các trường bắt buộc (tên, ngày bắt đầu) không được để trống, ngày kết thúc phải lớn hơn ngày bắt đầu.

## 3. Quản lý Nhiệm vụ (Tasks) (2 điểm)

- **GET**: Lấy danh sách nhiệm vụ theo dự án, hiển thị tiêu đề, mô tả, trạng thái (chưa bắt đầu, đang thực hiện, hoàn thành), và người được giao (assignee).
- **POST**: Thêm nhiệm vụ mới cho dự án qua form (bao gồm tiêu đề, mô tả, trạng thái, người được giao, ngày hết hạn).
- **PUT**: Cập nhật thông tin nhiệm vụ (bao gồm thay đổi người được giao).
- **DELETE**: Xóa nhiệm vụ (thêm xác nhận trước khi xóa).
- **Validation**: Đảm bảo tiêu đề nhiệm vụ không trùng lặp trong cùng một dự án và ngày hết hạn hợp lệ.

## 4. Các tính năng nâng cao (3 điểm)

- **Tìm kiếm**:
  - Tìm kiếm dự án theo tên. 0.25 điểm
  - Tìm kiếm nhiệm vụ theo người được giao. 0.25 điểm
- **Lọc và sắp xếp**:
  - Lọc dự án theo trạng thái (đang thực hiện, hoàn thành, tạm dừng). 0.25 điểm
  - Sắp xếp dự án theo tên (A-Z, Z-A), ngày bắt đầu (mới nhất, cũ nhất), hoặc tiến độ (thấp đến cao, cao đến thấp). 0.5 điểm
  - Sắp xếp nhiệm vụ theo trạng thái hoặc ngày hết hạn. 0.25 điểm
- **Thống kê**: Hiển thị bảng thống kê số lượng nhiệm vụ theo trạng thái (chưa bắt đầu, đang thực hiện, hoàn thành) trong một dự án. 0.5 điểm

## 5. Quản lý Người dùng (2 điểm)

- **Đăng ký**: Người dùng đăng ký với email, mật khẩu, tên, và vai trò (admin hoặc member).
- **Đăng nhập**: Đăng nhập bằng email và mật khẩu, lưu trạng thái đăng nhập bằng **localStorage**. Sau khi đăng nhập, chuyển hướng đến trang danh sách dự án.
- **Phân quyền**:
  - Admin có thể thêm/sửa/xóa dự án và nhiệm vụ.
  - Member chỉ có thể xem dự án/nhiệm vụ.
- **Hồ sơ người dùng**:
  - Hiển thị danh sách người dùng.
  - Khi ấn vào người dùng, hiển thị thông tin chi tiết của người dùng (trừ mật khẩu) và danh sách dự án và nhiệm vụ mà người dùng được giao (hiển thị bằng tên - không chấp nhận hiển thị bằng id).

## Quy ước tính điểm

- **Routing và giao diện**: 1 điểm
- **Quản lý dự án**: 2 điểm
- **Quản lý nhiệm vụ**: 2 điểm
- **Tính năng nâng cao**: 3 điểm
- **Quản lý người dùng**: 2 điểm
- Validation không được tính điểm riêng lẻ, nhưng nếu validation thiếu chính xác ở các tính năng **POST**, **PUT** sẽ bị trừ 1/2 số điểm của tính năng đó.

Hết.
