# Phân công nhóm · Day 11 SVM360/Fisheye

## Thành viên và vai trò

| Thành viên | Vai trò chính | Phạm vi trách nhiệm |
|---|---|---|
| Nguyễn Xuân Quang | A — annotator/rework | Thực hiện slice `B2-mid`: gán nhãn, tự kiểm, khóa `r1_craft`, chẩn đoán P4 và rework P5. Trong P3, Quang đã QA mù export `B2-edge` nhận từ bạn cùng nhóm. |
| Phù Ngô Việt Anh | B — blind QA | Nhận export đã khóa của thành viên khác, QA mù theo rule, ghi `qa_review.md` và finding `r2_qa`; không mở teaching reference/model trước khi gửi nhận xét. |
| Châu | C — điều phối/kỹ thuật | Chạy CVAT local trên máy mạnh, quản lý task/export và luồng bàn giao; kiểm tra evidence, triage/decision log và tổng hợp trước khi nộp. |

## Quy trình bàn giao

1. Quang gán nhãn slice `B2-mid`, tự kiểm, export và khóa `r1_craft`. Sau khi khóa, không sửa trực tiếp XML đã khóa.
2. B nhận ZIP/export **đã khóa** cùng slice và mã khóa, thực hiện QA mù. Nhận xét chỉ dựa trên ảnh gốc và rule; lưu tại `submission/r2_qa/qa_review.md` và `findings.csv` với `round=r2_qa`.
3. Châu cùng Quang đối chiếu QA với ảnh gốc, reference và báo cáo P4. Mỗi finding được quyết định là `rework`, `keep_with_reason` hoặc `escalate` và có owner.
4. Quang chỉ rework các finding P0/P1 thuộc slice `B2-mid`, export ZIP mới, khóa vòng `rework` và tạo `submission/rework/delta.md`.
5. B kiểm lại các thay đổi được giao; Châu rà soát evidence, các file P6 và kết quả `lab11.py check` trước khi nộp.

## Quy ước làm việc

- Máy Châu là máy chạy CVAT local; mỗi thành viên vẫn đọc guideline và chịu trách nhiệm cho review/decision của mình trên máy riêng.
- Slice của người làm nhãn là slice được `mode.json` cấp. Khi QA, dùng **slice của file nhận**, không dùng slice cá nhân theo mặc định.
- Không dùng prediction/model như bằng chứng duy nhất để sửa nhãn. Ca chưa đủ bằng chứng được ghi `E5_unresolved` và `action=escalate`.
- Mọi lần export dùng để QA hoặc rework đều phải có mã lock để truy vết đúng phiên bản.
