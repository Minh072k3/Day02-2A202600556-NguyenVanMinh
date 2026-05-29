Case: **Gán Nhãn Dữ Liệu**
Nhóm dự án OD Labeling đang gặp khó khăn trong việc quản lý, tìm kiếm và đảm bảo chất lượng dữ liệu gán nhãn do workflow thủ công, guideline phức tạp và thông tin quyết định bị phân tán trên nhiều công cụ như Slack, Docs và labeling platform.


| #  | Lăng kính          | Problem quan sát được                                                                                         | Ai đang đau?             | Dấu hiệu thật                                              |
| -- | ------------------ | ------------------------------------------------------------------------------------------------------------- | ------------------------ | ---------------------------------------------------------- |
| 1  | Lặp lại            | Team Lead phải tổng hợp thủ công số lượng frame đã labeling từ CVAT/Roboflow sang Google Sheets mỗi cuối ngày | Team Lead                | Mất khoảng 15–20 phút/ngày chỉ để cập nhật tiến độ         |
| 2  | Lặp lại            | Chia batch ảnh raw và assign thủ công cho từng annotator dựa trên tốc độ làm việc                             | Team Lead                | Thực hiện mỗi lần có data mới, dễ chia không đều workload  |
| 3  | Lặp lại            | Rename hàng loạt file annotation JSON/XML để đúng format khách hàng yêu cầu                                   | Data Engineer, Team Lead | Hay phải sửa tay hoặc chạy script thủ công dễ lỗi          |
| 4  | Tốn thời gian      | QA phải kiểm tra kỹ các bounding box bị occlusion hoặc chồng lấn trong frame đông vật thể                     | QA Reviewer              | Mất 3–5 phút chỉ cho một frame phức tạp                    |
| 5  | Tốn thời gian      | Viết feedback log chi tiết cho batch bị reject kèm screenshot minh họa lỗi                                    | QA Reviewer, Team Lead   | Mất 30–45 phút để giải thích lỗi cho annotator             |
| 6 | AI có thể tốt hơn  | Tìm lại quyết định labeling cho edge case từng được tranh luận trong Slack hoặc Notion                        | Annotator, Team Lead     | Mất 10–15 phút đọc lại thread dài để tìm kết luận cuối     |
| 7 | AI có thể tốt hơn  | QA khó phát hiện các object bị annotator bỏ sót trong frame đông                                              | QA Reviewer              | Missing box thường chỉ bị phát hiện khi khách review       |
| 8 | Pain từ người khác | Annotator mới liên tục hỏi lại rule occlusion dù guideline đã có sẵn                                          | Team Lead                | Bị interrupt nhiều lần mỗi ngày                            |
| 9 | Pain từ người khác | Cả batch bị khách reject vì team hiểu sai một guideline mới cập nhật                                          | PM, Toàn team            | Phải rework số lượng lớn dữ liệu trước deadline            |

