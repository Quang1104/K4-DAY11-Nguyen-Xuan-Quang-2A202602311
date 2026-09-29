# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B2 | MISSING | 9 |
| center | B2 | SPURIOUS | 10 |
| center | C0 | SPURIOUS | 2 |
| edge | B2 | ATTRIBUTE | 1 |
| edge | B2 | MISSING | 3 |
| edge | B2 | SPURIOUS | 2 |
| edge | B2 | WRONG_CLASS | 3 |
| mid | B2 | MISSING | 8 |
| mid | B2 | SPURIOUS | 12 |
| mid | B2 | WRONG_CLASS | 3 |
| unknown | C0 | IGNORE_SCOPE | 1 |

## Top defects
- SPURIOUS: 26 (ví dụ frame adasind_019560.jpg)
- MISSING: 20 (ví dụ frame adasind_060000.jpg)
- WRONG_CLASS: 6 (ví dụ frame adasind_082170.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: Lỗi tập trung ở `B2-mid`, nhất là vùng `mid`: 12 SPURIOUS và 8 MISSING. Ở các frame có vật nhỏ/méo vì fisheye, thao tác đọc hình rồi vẽ box dễ bỏ sót hoặc tạo box thừa; với phương tiện đặc biệt còn dễ nhầm class. Ví dụ `adasind_086220.jpg` L4/R5 là `Car` so với `ThreeWheeler`, còn `adasind_102750.jpg` có nhiều ca R04 (`Bus`/`Car`/`ThreeWheeler`/`Truck`). Đây là kết luận từ ảnh và so sánh L/R; model chỉ là nguồn hỗ trợ, không phải căn cứ tự quyết nhãn.
- Cách sửa và ai nhận việc (`owner`): Nguyễn Xuân Quang (`annotator`) đã rework các ca P1 của slice `B2-mid`; delta cho thấy `mid` giảm missing 4→0 và spurious 3→1, `edge` giảm missing 2→1 và spurious 2→1. Phù Ngô Việt Anh (`qa`) kiểm mù các thay đổi được bàn giao. Ca `adasind_102750.jpg` `L1+M3` còn bất đồng với reference được giữ ở `E5_unresolved`, `action=escalate` để Châu/QA kết luận thay vì tự sửa theo model.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): `screenshots/adasind_086220_r04_cvat.png` và `screenshots/adasind_102750_r04_cvat.png` là ảnh CVAT của các frame review; `r3_diag/local_quality_conflicts.csv`, `r1_craft/compare.md` và các dòng `r3_diag` trong `findings.csv` ghi object_ref/IoU. Quy tắc class được đối chiếu là R04 trong `docs/02-rules-vi.md`.
