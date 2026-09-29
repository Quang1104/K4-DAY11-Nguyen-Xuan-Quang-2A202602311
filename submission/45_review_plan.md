# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| B2-mid · `adasind_102750.jpg` | Nhiều ca R04 và R01: sai class, spurious, missing; có một ca E5 cần escalation | Frame có cả zone mid/edge và các xe nhỏ/méo, là nơi dễ nhầm `Car`/`Bus`/`ThreeWheeler`/`Truck`; delta vẫn còn finding chưa phân xử | Ảnh CVAT `screenshots/adasind_102750_r04_cvat.png`, compare/local-quality conflicts, decision D03–D04 và R04 |
| B2-mid · `adasind_060000.jpg` | Missing Pedestrian tại R6+M8 và R10+M5 | Hai nguồn độc lập cùng thấy object, phù hợp để kiểm hiệu quả rework R01 và cách rà vùng mid | Findings R6+M8/R10+M5, compare và `annotations-v2.xml`; khi review thực tế chụp thêm overlay CVAT của frame này |

Giới hạn của kết luận từ ba frame ADASIND: đây chỉ là ba frame của một camera, nên số lỗi cho biết nơi cần soi tiếp chứ không ước lượng được tỷ lệ lỗi tổng thể, chất lượng bốn camera SVM, hay độ khó theo khoảng cách thực.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv`: lấy đủ front/rear/left/right × normal/hard, phân tán theo
thời gian/cảnh để không đếm một chuỗi frame liền nhau như nhiều ca độc lập. Hard slice được tăng ở left/right vì
seam, sát biên kính và vật thể nhỏ. Đây là kế hoạch tìm ca cần soi và tạo candidate cho review; chưa có sampling
frame ngẫu nhiên, nhãn độc lập và thống kê sai số nên không thể suy ra tỷ lệ lỗi toàn hệ.
