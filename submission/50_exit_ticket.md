# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó là lỗi `DUPLICATE` hay cần một quy
   tắc riêng? Vì sao? Cần một quy tắc seam/cross-camera riêng. Hai box có thể là hai quan sát native-view hợp lệ của
   cùng vật ở hai camera, nên chưa thể gọi `DUPLICATE` như hai box lặp trong cùng một ảnh. Chỉ sau khi có mục tiêu
   output, timestamp đồng bộ, calibration và seam policy mới quyết định giữ cả hai, hợp nhất hay liên kết identity.
2. Một vật đi qua nhiều frame trên cùng camera: khi nào giữ cùng track ID, khi nào thêm keyframe hoặc trạng thái
   Outside? Nêu bằng chứng sẽ cần trước khi nối track qua hai camera. Giữ cùng track ID khi vẫn thấy cùng vật liên
   tục trên cùng camera; thêm keyframe khi hình học/class/attribute thay đổi đáng kể; đặt Outside khi vật rời trường
   nhìn hoặc không còn quan sát được. Để nối qua hai camera cần timestamp đồng bộ, calibration/seam map, hướng di
   chuyển liên tục và evidence ảnh ở cả hai view; chỉ gần nhau về vị trí không đủ.
3. Nhìn lại cả buổi: một chỗ bạn tin nhãn mình đúng nhưng reference hoặc người soát nghĩ khác (dẫn frame/`object_ref`),
   bạn đã xử lý thế nào, và nếu làm lại slice này bạn sẽ đổi gì trong cách làm? Ở `adasind_086220.jpg` L4/R5, nhãn
   ban đầu gọi xe là `Car` nhưng reference và review theo R04 nhận diện auto-rickshaw là `ThreeWheeler`. Tôi đối
   chiếu lại ảnh gốc, compare/conflict và rule, sau đó rework thay vì giữ nhãn theo ấn tượng ban đầu. Nếu làm lại,
   tôi sẽ rà riêng tất cả phương tiện nhỏ ở mid/edge bằng checklist R04 trước khi lock, và ghi ngay ca không chắc
   thành escalation thay vì suy đoán.
