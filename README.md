# UAV-Formation-Control-
# ĐIỀU KHIỂN ĐỘI HÌNH NHIỀU UAV SỬ DỤNG PI-BACKSTEPPING KẾT HỢP BỘ QUAN SÁT NHIỄU HOSM

## 1. Giới thiệu đề tài

Dự án tập trung nghiên cứu và mô phỏng hệ thống điều khiển đội hình nhiều thiết bị bay không người lái (UAV) sử dụng phương pháp điều khiển PI-Backstepping kết hợp bộ quan sát nhiễu trượt bậc cao (High-Order Sliding Mode – HOSM).

Mục tiêu của đề tài là thiết kế hệ thống điều khiển giúp các UAV bám theo quỹ đạo mong muốn, duy trì cấu hình đội hình và nâng cao khả năng chống chịu trước tác động của nhiễu ngoài.

Mô hình được xây dựng và mô phỏng trên phần mềm MATLAB/Simulink R2025a.

## 2. Mục tiêu nghiên cứu

Các mục tiêu chính của đề tài bao gồm:

- Xây dựng mô hình động lực học phi tuyến của UAV.
- Thiết kế bộ điều khiển PI-Backstepping nhằm đảm bảo khả năng bám quỹ đạo.
- Tích hợp bộ quan sát HOSM để ước lượng các thành phần nhiễu chưa xác định.
- Nâng cao độ chính xác bám quỹ đạo và khả năng duy trì đội hình.
- Đánh giá hiệu quả của hệ thống điều khiển thông qua kết quả mô phỏng.
- So sánh chất lượng điều khiển giữa hai trường hợp có và không sử dụng HOSM.

## 3. Phương pháp điều khiển

### 3.1. Bộ điều khiển PI-Backstepping

Bộ điều khiển PI-Backstepping được thiết kế dựa trên mô hình động lực học phi tuyến của UAV.

Phương pháp này kết hợp kỹ thuật thiết kế đệ quy Backstepping với thành phần tích phân nhằm giảm sai số xác lập và cải thiện chất lượng bám quỹ đạo.

### 3.2. Bộ quan sát nhiễu HOSM

Bộ quan sát nhiễu HOSM (High-Order Sliding Mode) được tích hợp vào hệ thống nhằm ước lượng các thành phần nhiễu tác động lên UAV.

Thông tin nhiễu ước lượng được sử dụng trong luật điều khiển để bù ảnh hưởng của nhiễu, qua đó cải thiện độ chính xác và tính bền vững của hệ thống.

### 3.3. Chiến lược điều khiển đội hình Leader–Follower

Hệ thống sử dụng cấu trúc điều khiển đội hình Leader–Follower gồm ba UAV:

- UAV 1 đóng vai trò UAV dẫn đầu (Leader), thực hiện bám quỹ đạo tham chiếu.
- UAV 2 và UAV 3 đóng vai trò UAV bám theo (Follower).
- Các UAV bám theo duy trì vị trí tương đối mong muốn so với UAV dẫn đầu.

Mục tiêu là đảm bảo các UAV di chuyển theo quỹ đạo đặt đồng thời duy trì cấu hình đội hình trong quá trình bay.

## 4. Môi trường mô phỏng

Hệ thống được xây dựng và mô phỏng với:

- Phần mềm: MATLAB R2025a.
- Công cụ mô phỏng: Simulink.
- Mô hình: Động lực học phi tuyến UAV.
- Bộ điều khiển: PI-Backstepping.
- Bộ quan sát nhiễu: HOSM.
- Cấu hình đội hình: 01 Leader và 02 Follower.

## 5. Các trường hợp mô phỏng

Để đánh giá hiệu quả của bộ quan sát HOSM, đề tài thực hiện hai trường hợp mô phỏng.

### 5.1. Trường hợp 1: Có sử dụng HOSM

Kích hoạt bộ quan sát nhiễu cho cả ba UAV:

```matlab
P.useHOSM = [1 1 1];
```

Trong trường hợp này, bộ điều khiển PI-Backstepping sử dụng thông tin nhiễu ước lượng từ HOSM để thực hiện bù nhiễu.

### 5.2. Trường hợp 2: Không sử dụng HOSM

Tắt bộ quan sát nhiễu:

```matlab
P.useHOSM = [0 0 0];
```

Trường hợp này chỉ sử dụng bộ điều khiển PI-Backstepping, không tích hợp thành phần bù nhiễu từ HOSM.

Hai trường hợp được thực hiện trong cùng điều kiện mô phỏng để đánh giá sự khác biệt về chất lượng điều khiển.

## 6. Đánh giá kết quả mô phỏng

Chất lượng điều khiển được đánh giá thông qua các tiêu chí:

- Khả năng bám quỹ đạo vị trí của các UAV.
- Khả năng bám vận tốc.
- Sai số duy trì đội hình giữa các UAV.
- Đáp ứng của các tín hiệu điều khiển.
- Khả năng ước lượng nhiễu của bộ quan sát HOSM.
- Sai số bình phương trung bình căn bậc hai (RMSE).
- Thời gian xác lập của hệ thống.

Kết quả mô phỏng được sử dụng để phân tích và so sánh hiệu quả của bộ điều khiển PI-Backstepping trong hai trường hợp có và không có HOSM.

## 7. Mã nguồn MATLAB/Simulink

Kho lưu trữ bao gồm các thành phần:

- Các tệp mô hình Simulink (`.slx`) mô phỏng hệ thống điều khiển đội hình UAV.
- Các tệp MATLAB (`.m`) thiết lập tham số và điều kiện ban đầu.
- Chương trình thực hiện mô phỏng.
- Chương trình xử lý dữ liệu và trực quan hóa kết quả.
- Chương trình đánh giá chất lượng điều khiển và tính toán các chỉ số RMSE, thời gian xác lập.

## 8. Hướng dẫn chạy mô phỏng

**Bước 1:** Tải toàn bộ mã nguồn từ GitHub về máy tính.

**Bước 2:** Mở phần mềm MATLAB R2025a.

**Bước 3:** Thiết lập thư mục làm việc và thêm các thư mục chứa mã nguồn vào MATLAB Path.

**Bước 4:** Chạy các tệp khởi tạo để thiết lập tham số và điều kiện ban đầu, phần THAM_SO_UAV, run sau đó vào Simulink Run Simulation

**Bước 5:** Mở mô hình Simulink của hệ thống UAV.

**Bước 6:** Lựa chọn trường hợp mô phỏng bằng cách bật hoặc tắt HOSM:

```matlab
% Truong hop co HOSM
P.useHOSM = [1 1 1];

% Truong hop khong co HOSM
P.useHOSM = [0 0 0];
```

**Bước 7:** Nhấn Run trong Simulink để thực hiện mô phỏng.

**Bước 8:** Chạy chương trình đánh giá kết quả để hiển thị đồ thị trong code PLOT_UAV, tính toán RMSE và thời gian xác lập.

## 9. Thông tin tác giả

**Họ và tên:** Dương Quốc Tuấn

**Đơn vị:** Đại học Bách khoa Hà Nội (HUST).

**Lĩnh vực nghiên cứu:**
- Điều khiển phi tuyến.
- Điều khiển đội hình UAV.
- Điều khiển bám quỹ đạo.
- Bộ quan sát nhiễu và điều khiển bền vững.

## 10. Mục đích sử dụng

Kho mã nguồn được xây dựng nhằm phục vụ mục đích học tập, nghiên cứu và mô phỏng các thuật toán điều khiển đội hình UAV.

Các chương trình và mô hình mô phỏng được cung cấp để hỗ trợ việc tham khảo, kiểm chứng và tái lập các kết quả nghiên cứu được trình bày trong báo cáo.

## 11. Tài liệu tham khảo

- Bài báo nghiên cứu: *Mathematics 2025, 13, 1520*.
- Tài liệu MATLAB/Simulink của MathWorks.
