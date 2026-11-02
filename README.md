# Bài 9: Thiết Kế Không Gian Đa Profile Và Kiến Trúc Bookmark Cho Trạm Khám Bệnh

## PHẦN 1: PHÂN TÍCH KIẾN TRÚC ĐA PROFILE

### 1. Nguyên nhân gây văng phiên đăng nhập
* Tất cả nhân sự dùng chung 1 Profile mặc định -> chung thư mục lưu trữ User Data.
* Khi đăng nhập nhiều tài khoản khác nhau trên cùng một cửa sổ, các file **Cookies** và **Session Storage** bị ghi đè lẫn nhau khiến hệ thống tưởng bị hack hoặc lỗi định danh, dẫn đến việc tài khoản chính bị văng đột ngột.

### 2. Mô hình 3 Profile chuyên dụng cho trạm khám
| Tên Profile | Màu Theme | Mục đích sử dụng | Dữ liệu độc lập |
| :--- | :--- | :--- | :--- |
| 01. CarePulse | Xanh dương | vận hành phần mềm khám chữa bệnh. | Cookies y tế, lịch sử khám, bookmarks chuyên ngành. |
| 02. Personal | Xám | tra cứu hành chính, email cá nhân ngoài giờ. | Tài khoản Google cá nhân, lịch sử chung. |
| 03. Sandbox / Test | Cam |  thử nghiệm tính năng web. | Không lưu dài hạn, tự xóa sạch sau khi tắt. |
