# Guideline patch

- **Rule mới đề xuất:** Bổ sung checklist R04 cho vật nhỏ/méo trên ảnh fisheye: trước khi chọn `Car`, `Bus` hay `Truck`, kiểm thân xe có khoang ba bánh/cabin mở đặc trưng của auto-rickshaw không. Nếu có, gán `ThreeWheeler`; nếu thân xe không đủ nhìn rõ, giữ case để QA/escalation thay vì suy đoán theo kích thước box.
- **Áp dụng cho:** R04, class `ThreeWheeler` / `Car` / `Bus` / `Truck`, ưu tiên box nhỏ ở zone `mid` và `edge`.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** R04 đã nêu ánh xạ class, nhưng không nêu một điểm kiểm trực quan cho auto-rickshaw khi fisheye làm thân xe méo hoặc bị che một phần. Trong `adasind_086220.jpg` và `adasind_102750.jpg`, sự thiếu bước kiểm này dẫn tới các bất đồng class dù box có vị trí gần khớp.
- **`rules_version` mới:** v1.0.0 → v1.1.0.
- **Hiệu lực từ:** Vòng annotation tiếp theo sau P6; không hồi tố hoặc sửa âm thầm export `r1_craft` đã khóa.
