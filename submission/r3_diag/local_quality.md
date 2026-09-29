# Đối chiếu chất lượng cục bộ — rectangle

Teaching reference, không phải gold set đã phê duyệt; không có điểm đạt tự động.
Nguồn: export r1_craft đã khóa SHA256 `a0bd01fd4f485b0fb37a10118a03e3d8d412e403fb7b35a41834c0ca9a248d66`; slice `B2-mid`.
Ghép hình học greedy một-một theo IoU ≥ 0.50, rồi so class; H ≥ 40 px.
Box trái nằm chủ yếu trong ignore_region reference không tính. Polygon, polyline, track không được chấm.
Đây là phép tính offline của lab, không phải báo cáo hay kết quả tương đương CVAT Premium.

Frame được tính: adasind_060000.jpg, adasind_086220.jpg, adasind_102750.jpg. Frame thiếu trong export: không.
TP=11; FP=6; FN=9; số lần đối chiếu=22; mean IoU của TP=0.860.

| Chỉ số | Micro | Macro | Nhãn thấp nhất |
|---|---:|---:|---:|
| accuracy | 0.500 | 0.886 | 0.773 |
| precision | 0.647 | 0.639 | 0.000 |
| recall | 0.550 | 0.356 | 0.000 |
| jaccard | 0.423 | 0.347 | 0.000 |
| dice | 0.595 | 0.448 | 0.000 |

| Nhãn | TP | FP | FN | Accuracy | Precision | Recall | Jaccard | Dice |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Bike | 3 | 0 | 1 | 0.955 | 1.000 | 0.750 | 0.750 | 0.857 |
| Bus | 0 | 1 | 0 | 0.955 | 0.000 | 0.000 | 0.000 | 0.000 |
| Car | 0 | 4 | 0 | 0.818 | 0.000 | 0.000 | 0.000 | 0.000 |
| Pedestrian | 2 | 0 | 2 | 0.909 | 1.000 | 0.500 | 0.500 | 0.667 |
| ThreeWheeler | 5 | 1 | 4 | 0.773 | 0.833 | 0.556 | 0.500 | 0.667 |
| Truck | 1 | 0 | 2 | 0.909 | 1.000 | 0.333 | 0.333 | 0.500 |

| Frame | TP | FP | FN | Accuracy | Precision | Recall |
|---|---:|---:|---:|---:|---:|---:|
| adasind_060000.jpg | 7 | 0 | 3 | 0.700 | 1.000 | 0.700 |
| adasind_086220.jpg | 3 | 2 | 2 | 0.500 | 0.600 | 0.600 |
| adasind_102750.jpg | 1 | 4 | 4 | 0.167 | 0.200 | 0.200 |

Confusion matrix: hàng = teaching reference; cột = export đã khóa.
`<missing>` là thiếu box; `<extra>` là box thừa. Xem `local_quality_confusion.csv`.

| Reference \ Export | Bike | Bus | Car | Pedestrian | ThreeWheeler | Truck | <missing> |
|---|---:|---:|---:|---:|---:|---:|---:|
| Bike | 3 | 0 | 0 | 0 | 0 | 0 | 1 |
| Bus | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Car | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Pedestrian | 0 | 0 | 0 | 2 | 0 | 0 | 2 |
| ThreeWheeler | 0 | 1 | 2 | 0 | 5 | 0 | 1 |
| Truck | 0 | 0 | 0 | 0 | 1 | 1 | 1 |
| <extra> | 0 | 0 | 2 | 0 | 0 | 0 | 0 |

Chi tiết xung đột trong `local_quality_conflicts.csv`; dữ liệu máy đọc trong `local_quality.json`.
Mismatching label đóng góp một FP cho class vẽ và một FN cho class reference; attribute khác được báo riêng.
Micro accuracy đếm mỗi cặp ghép sai class là một lần đối chiếu; Jaccard đếm cả FP và FN.
Macro/worst bỏ nhãn không xuất hiện ở cả hai phía; chỉ số không có mẫu là N/A.
