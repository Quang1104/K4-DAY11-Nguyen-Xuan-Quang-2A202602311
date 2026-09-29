# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 9 | 3 | 1 | 5 | 8 | MISSING (3) |
| mid | 8 | 4 | 3 | 4 | 9 | MISSING (2) |
| edge | 3 | 2 | 2 | 2 | 1 | WRONG_CLASS (2) |

## Nhận xét

- Người gán nhãn (L) mất nhiều nhất ở `mid`: 4 missing và 3 spurious. Model (M) cũng thừa nhiều nhất ở `mid` với 9 box; tại `center`, M thừa 8 box. `edge` ít mẫu hơn nhưng L có 2 missing, 2 spurious và lỗi chính là `WRONG_CLASS`.
- Ở các ca L/R đồng thuận nhưng M bỏ sót hoặc gọi sai class, đây là tín hiệu lệch miền của model trên ảnh fisheye và object nhỏ/méo; không phải bằng chứng để thay nhãn theo model. Các ca R/M cùng có nhưng L thiếu được giao rework theo ảnh gốc và R01/R04. Kết luận chỉ dựa trên ba frame của một camera; không suy rộng thành chất lượng của toàn hệ SVM hoặc vị trí gần/xa xe.
