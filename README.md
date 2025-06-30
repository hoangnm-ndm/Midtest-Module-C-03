# Hướng dẫn làm bài - Bài kiểm tra ReactJS nâng cao

- **Thời gian làm bài**: 150 phút.
- **Yêu cầu môi trường**:
  - Tải Repository mẫu này về máy và thực hiện code trực tiếp trong thư mục này.
  - Sau khi hoàn thành, chấm bài tại lớp.
  - **Tắt tất cả các extension AI** (như Tabnine, GitHub Copilot, Codeium, v.v.) trong quá trình làm bài.
  - Được phép sử dụng các tài liệu tham khảo giao diện như **TailwindCSS**, **Bootstrap**, **Material-UI**, **Boxicons**, hoặc **FontAwesome**.
- **Công cụ backend**: Sử dụng `json-server` để mock API (cài đặt: `npm install -g json-server`).

## Yêu cầu

Xây dựng ứng dụng **Project Management System (PMS)** sử dụng **ReactJS** và **json-server**, với các tính năng sau:

## 1. Giao diện và Routing (1 điểm)

- Dữ liệu được cung cấp sẵn trong file `db.json` với các thực thể: **Projects**, **Tasks**, và **Users**.
- Xây dựng hệ thống định tuyến với các trang:
  - **Trang danh sách dự án**: `/` hoặc `/projects` Hiển thị tất cả dự án, trạng thái (đang thực hiện, hoàn thành, tạm dừng), và tiến độ (% hoàn thành).
  - **Trang chi tiết dự án**: `/projects/:id` Hiển thị thông tin dự án và danh sách các nhiệm vụ (tasks) thuộc dự án.
- Xử lý **route không tồn tại (404)** với giao diện lỗi thân thiện, có nút quay lại trang chủ.
- Có header và navigation bar với các liên kết đến trang danh sách dự án và trang chi tiết dự án.

## 2. Quản lý Dự án (Projects) (2 điểm)

- Url: `/projects`
- **GET**: Lấy danh sách dự án từ API và hiển thị thông tin: tên, mô tả, ngày bắt đầu, ngày kết thúc dự kiến, trạng thái, và tiến độ (tiến độ tính theo %).
- **POST**: Thêm dự án mới thông qua form (bao gồm tên, mô tả, ngày bắt đầu, ngày kết thúc, trạng thái, tiến độ).
- **PUT**: Cập nhật thông tin dự án.
- **DELETE**: Xóa dự án (thêm xác nhận trước khi xóa).
- **Validation**: Đảm bảo các trường là bắt buộc, ngày kết thúc phải lớn hơn ngày bắt đầu.

```javascript
const statusOptions = [
  { value: "in-progress", label: "Đang thực hiện" },
  { value: "completed", label: "Hoàn thành" },
  { value: "paused", label: "Tạm dừng" },
];
```

## 3. Quản lý Nhiệm vụ (Tasks) (2 điểm)

- Url: `/projects/:projectId/tasks`
- **GET**: Lấy danh sách nhiệm vụ theo dự án, hiển thị tiêu đề, mô tả, trạng thái, người được giao (assignee), ngày đến hạn (dueDate).
- **POST**: Thêm nhiệm vụ mới cho dự án qua form.
- **PUT**: Cập nhật thông tin nhiệm vụ.
- **DELETE**: Xóa nhiệm vụ (thêm xác nhận trước khi xóa).
- **Validation**: Đảm bảo các trường là bắt buộc, ngày hết hạn khi giao task cần ở thì tương lai.

## 4. Các tính năng nâng cao (2 điểm)

- **Lọc và sắp xếp**:
  - Lọc dự án theo trạng thái (0.5 điểm).
  - Sắp xếp dự án theo tên (A-Z, Z-A), ngày bắt đầu (mới nhất, cũ nhất), hoặc tiến độ (thấp đến cao, cao đến thấp) (0.5 điểm).
  - Sắp xếp nhiệm vụ theo trạng thái hoặc ngày hết hạn (0.5 điểm).
- **Thống kê**: Hiển thị bảng thống kê số lượng nhiệm vụ theo trạng thái (chưa bắt đầu, đang thực hiện, hoàn thành) trong một dự án (0.5 điểm).

## 5. Authentication & Authorization (3 điểm)

- **Đăng ký:** 1 điểm
  - Cho phép người dùng đăng ký tài khoản mới với các trường: tên, email, mật khẩu.
  - Role mặc định là `member`.
  - **Validation:** Email là duy nhất, mật khẩu tối thiểu 6 ký tự.
- **Đăng nhập:** 1 điểm
  - Cho phép người dùng đăng nhập với email và mật khẩu.
  - **Validation:** Hiển thị thông báo lỗi nếu đăng nhập không thành công.
  - Lưu và duy trì trạng thái đăng nhập trong localStorage (bao gồm thông tin user và token).
- **Bảo vệ các route:** 1 điểm
  - Chỉ cho phép người dùng đã đăng nhập truy cập vào các trang xem dự án và nhiệm vụ.
  - Hiển thị thông báo lỗi nếu người dùng chưa đăng nhập khi cố gắng truy cập.
  - Chỉ admin mới có quyền thêm, sửa, xóa dự án và nhiệm vụ, thành viên trong nhóm chỉ có thể xem.

## Quy ước tính điểm

- **Routing và giao diện**: 1 điểm
- **Quản lý dự án**: 2 điểm
- **Quản lý nhiệm vụ**: 2 điểm
- **Tính năng nâng cao**: 2 điểm
- **Authentication & Authorization**: 3 điểm

**Hết.**
