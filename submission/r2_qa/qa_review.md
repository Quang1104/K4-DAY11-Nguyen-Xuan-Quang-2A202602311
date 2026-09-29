# QA review · B2-edge

Mã khóa: 6147-6108

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_082170.jpg | L3 | R04 | Box L3 đang là `Bus`, nhưng đối tượng vàng ở vùng giữa-trái là xe ba bánh/auto-rickshaw; cần đổi class thành `ThreeWheeler`. |
| adasind_102750.jpg | L4 | R04 | Box L4 đang là `Bus`, nhưng phương tiện bị cắt ở mép trái là xe ba bánh/auto-rickshaw; cần đổi class thành `ThreeWheeler`. |
| adasind_069450.jpg | L1 | R05 | Box L1 nằm sát mép trái (xtl=4) và phần phương tiện bị cắt bởi biên ảnh; cần kiểm lại và bật `truncated=true` nếu phần vật thể tiếp tục ra ngoài khung hình. |

Đã xem đủ ba frame trên qa_overlay.html. Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
