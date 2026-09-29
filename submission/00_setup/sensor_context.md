# Sensor context

- Rig: theo quan sát, đây là một camera fisheye góc nhìn rất rộng đặt trên hoặc sát thân xe, nhìn ra phía trước/ngang
  đường. ADASIND trong bài không kèm thông số rig/calibration chi tiết, nên không suy diễn vị trí lắp chính xác.
- `ego_body`: phần thân xe tối xuất hiện ở hai mép dưới, rõ hơn ở góc dưới trái/phải của frame; phần này được xem là
  ego body/biên xe khi quyết định ignore hoặc không gán nhãn vật thể.
- Vòng kính (lens circle): vòng tối/viền cong bao quanh ảnh, rõ ở các mép và hai góc dưới; phần ảnh hữu ích gần như
  nằm trong một hình tròn lớn, chiếm khoảng 90% bề ngang và hầu hết chiều cao frame.
