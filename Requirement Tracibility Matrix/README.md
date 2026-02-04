# 🔗 RTM - Requirement Traceability Matrix (Ma trận truy vết yêu cầu)

## 1. Tổng quan (Overview)
Tài liệu này xác định mối quan hệ hai chiều giữa **Yêu cầu hệ thống (Requirements)** và **Ca kiểm thử (Test Cases)**. Mục đích là đảm bảo tính toàn vẹn của dự án, chứng minh rằng mọi yêu cầu nghiệp vụ đều đã được kiểm thử kỹ lưỡng.

* **Dự án:** Website E-commerce (Manual Testing)
* **Ngày cập nhật:** 04/02/2026
* **Tổng số yêu cầu (Requirements):** 16
* **Tổng số Test Case:** 45
* **Độ bao phủ (Coverage):** 100% (Tất cả yêu cầu đều có Test Case tương ứng)

## 2. Ma trận truy vết (Traceability Matrix)

| Req ID | Mô tả yêu cầu (Requirement Description) | Test Case IDs (Mapped) | Loại Test (Type) | Trạng thái |
| :--- | :--- | :--- | :--- | :--- |
| **R1** | Người dùng đăng ký bằng email hợp lệ | **TC_AUTH_001** | Positive | ✅ Covered |
| **R2** | Không cho đăng ký khi email sai/trùng | **TC_AUTH_002**, **TC_AUTH_003** | Negative | ✅ Covered |
| **R3** | Mật khẩu tối thiểu 8 ký tự | **TC_AUTH_004**, **TC_AUTH_014** | Boundary | ✅ Covered |
| **R4** | Đăng nhập thành công với thông tin hợp lệ | **TC_AUTH_005**, **TC_AUTH_011**, **TC_AUTH_015** | Positive | ✅ Covered |
| **R5** | Đăng nhập thất bại khi sai mật khẩu/email | **TC_AUTH_006**, **TC_AUTH_007**, **TC_AUTH_008**, **TC_AUTH_012**, **TC_AUTH_013** | Negative / Security | ✅ Covered |
| **R6** | Quên mật khẩu gửi email đặt lại | **TC_AUTH_009**, **TC_AUTH_010** | Positive / Negative | ✅ Covered |
| **R7** | Tìm kiếm hiển thị đúng kết quả | **TC_CART_001**, **TC_CART_002**, **TC_CART_017** | Func / Security | ✅ Covered |
| **R8** | Lọc theo giá / danh mục hoạt động đúng | **TC_CART_003**, **TC_CART_004**, **TC_CART_018** | Positive / Negative | ✅ Covered |
| **R9** | Xem chi tiết sản phẩm | **TC_CART_005** | Positive | ✅ Covered |
| **R10** | Thêm sản phẩm vào giỏ thành công | **TC_CART_006**, **TC_CART_007**, **TC_CART_008**, **TC_CART_009**, **TC_CART_010** | Pos / Neg / Bound | ✅ Covered |
| **R11** | Cập nhật số lượng trong giỏ | **TC_CART_011**, **TC_CART_012**, **TC_CART_016** | Positive / Boundary | ✅ Covered |
| **R12** | Xoá sản phẩm khỏi giỏ / Quản lý giỏ | **TC_CART_013**, **TC_CART_014**, **TC_CART_015**, **TC_CART_019**, **TC_CART_020** | Pos / Neg | ✅ Covered |
| **R13** | Thanh toán bắt buộc nhập địa chỉ | **TC_CHECKOUT_003**, **TC_CHECKOUT_004** | Negative | ✅ Covered |
| **R14** | Chọn phương thức thanh toán | **TC_CHECKOUT_001**, **TC_CHECKOUT_002**, **TC_CHECKOUT_005** | Positive / Negative | ✅ Covered |
| **R15** | Đặt hàng thành công / Xử lý đơn hàng | **TC_CHECKOUT_006**, **TC_CHECKOUT_009**, **TC_CHECKOUT_010** | Negative / Edge | ✅ Covered |
| **R16** | Lưu lịch sử đơn hàng | **TC_CHECKOUT_007**, **TC_CHECKOUT_008** | Positive / Negative | ✅ Covered |

## 3. Phân tích chi tiết (Coverage Analysis)

### 3.1. Module Authentication (Xác thực)
* **Độ phủ:** Rất cao.
* **Điểm nhấn:** Ngoài các case chức năng thông thường, nhóm đã bao gồm kiểm thử bảo mật (**SQL Injection - TC_AUTH_013**) và kiểm thử biên cho độ dài mật khẩu (**TC_AUTH_014** kiểm tra mật khẩu 6 ký tự so với yêu cầu 8 ký tự).

### 3.2. Module Product & Cart (Sản phẩm & Giỏ hàng)
* **Độ phủ:** Đầy đủ các luồng nghiệp vụ.
* **Điểm nhấn:**
    * Đã kiểm soát tốt các case nhập liệu sai logic: Số lượng bằng 0 (`TC_CART_008`), Số lượng âm (`TC_CART_009`), Lọc giá Min > Max (`TC_CART_004`).
    * Có kiểm thử bảo mật XSS tại ô tìm kiếm (`TC_CART_017`).

### 3.3. Module Checkout (Thanh toán)
* **Độ phủ:** Đảm bảo luồng tiền và đơn hàng.
* **Điểm nhấn:**
    * Xử lý tốt các hành vi người dùng bất thường: Double click nút đặt hàng (`TC_CHECKOUT_009`), Reload trang sau khi đặt (`TC_CHECKOUT_010`).
    * Kiểm tra validation địa chỉ kỹ lưỡng (`TC_CHECKOUT_003`, `TC_CHECKOUT_004`).

## 4. Kết luận
Bộ Test Case hiện tại đã đáp ứng **100%** yêu cầu đề ra trong tài liệu đặc tả. Tỷ lệ các Test Case Negative (Âm tính) và Boundary (Biên) chiếm tỷ trọng hợp lý (~40%), đảm bảo khả năng phát hiện lỗi cao cho hệ thống.