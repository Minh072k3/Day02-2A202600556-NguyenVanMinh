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

# TOP 3 PROBLEMS — OD Labeling Project

| Rank | Problem                                                                                | Vì sao chọn                                                | Điều còn chưa chắc  |                        
| ---- | -------------------------------------------------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------- | -------------------- |
| 1    | Tìm lại quyết định labeling cho edge case từng được tranh luận trong Slack hoặc Notion | Workflow rõ, pain thật, AI fit mạnh nhất, dễ làm pilot nhỏ | Semantic search có đủ chính xác không       |
| 2    | QA khó phát hiện các object bị annotator bỏ sót trong frame đông                       | Impact trực tiếp lên chất lượng dataset và reject rate     | False positive và độ chính xác model        |
| 3    | Annotator mới liên tục hỏi lại rule occlusion dù guideline đã có sẵn                   | Pain lặp lại hằng ngày, dễ validate và scope phù hợp lab   | Guideline có đủ rõ để AI trả lời đúng không | 

---

# TOP 1 — Problem Card

## Bài toán 1 câu

Annotator và Team Lead mất nhiều thời gian tìm lại quyết định labeling cho các edge case vì thông tin nằm rải rác trên Slack, Notion và guideline docs.

## Actor

* Annotator
* QA Reviewer
* Team Lead

## Thời điểm / bối cảnh

Khi gặp edge case chưa chắc cách labeling đúng, team phải tìm lại quyết định cũ trước khi tiếp tục annotate hoặc QA.

## Current workflow

1. Annotator gặp edge case
2. Search keyword trên Slack/Notion
3. Đọc nhiều thread hoặc guideline liên quan
4. Ping Team Lead nếu vẫn chưa chắc
5. Team Lead giải thích lại hoặc tìm decision cũ
6. Annotator tiếp tục labeling

## Bottleneck

Bước đọc lại thread dài và tìm kết luận cuối cùng mất khoảng 10–15 phút/lần.

## Impact

* Giảm tốc độ labeling
* Interrupt Team Lead nhiều lần/ngày
* Dễ hiểu sai guideline nếu tìm nhầm thread

## Success metric

* Giảm thời gian tìm decision từ 10–15 phút xuống dưới 2 phút
* Giảm số lần hỏi lại Team Lead
* Giảm lỗi labeling do hiểu sai edge case

## Non-AI alternative

* Pin message
* Tag thread
* Viết FAQ guideline

## AI hypothesis

AI semantic search + summarize có thể retrieve đúng discussion và tóm tắt kết luận cuối cùng theo context.

## Quick gut

Workflow

---

# Draft Workflow — Current State

```text
CURRENT STATE — 10~15 phút/lần

[Annotator gặp edge case]
        ↓
[Search keyword trên Slack]
        ↓
[Đọc nhiều thread]
        ↓
[Search thêm trên Notion]
        ↓
[Không chắc kết luận]
        ↓
[Ping Team Lead]
        ↓
[Lead giải thích lại]
        ↓
[Tiếp tục labeling]
```

---

# Draft Workflow — Future State

```text
FUTURE STATE — dưới 2 phút/lần

[Annotator gặp edge case]
        ↓
[AI semantic search]
        ↓
[AI summarize decision + guideline liên quan]
        ↓
[Annotator xác nhận]
        ↓
[Tiếp tục labeling]

Fallback:
Nếu confidence thấp → hỏi Team Lead
```

---
