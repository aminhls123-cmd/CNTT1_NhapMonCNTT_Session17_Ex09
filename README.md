# Bài 9: Thiết Kế Không Gian Đa Profile Và Kiến Trúc Bookmark Cho Trạm Khám Bệnh

## Phần 1: Phân tích kiến trúc đa Profile

### 1. Nguyên nhân gây văng phiên đăng nhập
* Tất cả nhân sự dùng chung 1 Profile mặc định -> chung thư mục lưu trữ User Data.
* Khi đăng nhập nhiều tài khoản khác nhau trên cùng một cửa sổ, các file **Cookies** và **Session Storage** bị ghi đè lẫn nhau khiến hệ thống tưởng bị hack hoặc lỗi định danh, dẫn đến việc tài khoản chính bị văng đột ngột.

### 2. Mô hình 3 Profile chuyên dụng cho trạm khám
| Tên Profile | Mục đích sử dụng | Dữ liệu độc lập |
| :--- | :--- | :--- |
| 01. CarePulse | vận hành phần mềm khám chữa bệnh. | Cookies y tế, lịch sử khám, bookmarks chuyên ngành. |
| 02. Personal | tra cứu hành chính, email cá nhân ngoài giờ. | Tài khoản Google cá nhân, lịch sử chung. |
| 03. Sandbox / Test | thử nghiệm tính năng web. | Không lưu dài hạn, tự xóa sạch sau khi tắt. |

## Phần 2: Thiết kế hệ thống Bookmark và Quy trình an toàn

### 4. Mẹo dùng "Favicon-Only" tiết kiệm diện tích
* Nhấp chuột phải vào Bookmark Edit xóa sạch phần tên, để trống hoặc 1 dấu cách Save.
* Kết quả: Thanh công cụ chỉ hiện icon nhỏ gọn, giúp tăng số lượng link hiển thị gấp 3 lần mà không bị tràn màn hình.

### 5. Xử lý bẫy an ninh & Cảnh báo Cloud Sync
* Khi cho khách/đoàn thanh tra mượn máy 30 phút: Bắt buộc dùng Guest Profile để mở ra một không gian tạm thời, tự động xóa sạch toàn bộ lịch sử và cookies ngay khi tắt máy.
* Cảnh báo Cloud Sync: Tuyệt đối không bật đồng bộ tài khoản cá nhân trên máy tính phòng khám dùng chung. Có thể bị lộ thông tin cá nhân
