# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Ngược sáng, xe ngược chiều, object sát vòng kính | Bóng/loá làm mất biên box và class xe nhỏ | Intrinsic/extrinsic, timestamp, crop/vòng kính, rules version | Hai người annotate độc lập, QA phân xử bất đồng và giữ evidence ảnh gốc trước khi chốt reference |
| rear | Lùi xe, vật gần bumper, thiếu sáng | Truncated/occluded dễ lẫn và kích thước thay đổi mạnh | Calibration rear, timestamp, vùng bumper/ignore và rule R05 | Review hai lượt mù; kiểm riêng object sát biên với policy truncated đã ghi |
| left | Seam góc trái, xe máy/người đi bộ nhỏ | Méo fisheye và overlap với front/rear làm dễ bỏ sót hoặc nhân đôi | Calibration giữa left-front/left-rear, đồng bộ thời gian, seam polygon | Reviewer kiểm native view trước, sau đó đối chiếu timestamp/calibration; chỉ chốt khi policy seam rõ |
| right | Xe đỗ sát, vật cắt biên, seam góc phải | Box nhỏ và phần vật lộ ít dẫn tới sai class/box | Calibration giữa right-front/right-rear, timestamp, rules version và ignore vùng xe | Annotation độc lập, QA kiểm R01/R04/R05, adjudication có decision log trước khi gắn gold |

- Khi nào cần refresh gold set (đổi camera, calibration hoặc rule): refresh khi đổi vị trí/ống kính camera, intrinsics/extrinsics, pipeline biến đổi/BEV, taxonomy/rules version, hoặc khi QA phát hiện hard case mới chưa được bao phủ.
- Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box: một xe máy xuất hiện đồng thời ở edge của camera left và mid của camera front. Giữ hai native-view box là hợp lệ cho đến khi policy output xác định có hợp nhất hay không; cần timestamp đồng bộ, calibration, seam map và evidence ảnh ở cả hai camera trước khi gán cùng identity hoặc loại một box.
- Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera: đồng thuận có thể cùng lặp một sai lệch, còn quality report ở đây chỉ đối chiếu teaching reference của vài frame ADASIND một camera. Nó không kiểm timestamp, calibration, seam policy hoặc phân bố cảnh của bốn camera.
