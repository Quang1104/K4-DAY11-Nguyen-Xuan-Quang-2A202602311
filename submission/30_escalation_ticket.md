# Escalation ticket

## Ticket 1

- **Frame:** `adasind_102750.jpg`, object_ref `L1+M3` (cell `LM_noR`).
- **Ảnh chụp:** `submission/screenshots/adasind_102750_r04_cvat.png`.
- **Expected impact:** Nếu phân xử sai `Car` và `ThreeWheeler`, thống kê R04 của slice bị lệch và cùng một hình dạng xe có thể bị rework không nhất quán ở các vòng sau.
- **Owner:** `qa`.
- **Recommendation:** QA mở frame gốc cùng overlay/reference, kiểm lại thân xe ở vị trí L1+M3 và xác nhận class canonical. Ghi quyết định vào decision log; nếu cần, chuyển guideline patch R04 cho Lab Coach trước khi áp dụng rộng hơn.
