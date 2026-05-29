# Group convergence

| Cluster                                            | Candidate examples                                                                                                                                                                         | Pattern chung                                                                                                                                                                                                                                   |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Chuẩn hóa dữ liệu phi cấu trúc & Tra cứu thông tin | • Hạnh #1: BOQ khách → đầu mục chuẩn + spec  <br> • Hạnh #3: BOQ đa ngôn ngữ → bản dịch tiếng Việt chuyên ngành  <br> • Minh #1: Tìm lại quyết định labeling cho edge case từ Slack/Notion | **Bản chất:** Đầu vào phân tán, nhiều format, khó tra cứu nhanh.  <br><br> **Giải pháp:** Kết hợp LLM + semantic search/lookup để đọc hiểu context và truy xuất đúng thông tin từ guideline, tài liệu hoặc discussion cũ.                       |
| Gom tụ & Đồng bộ thông tin đa kênh                 | • Khôi #1: Học viên bị quá tải thông tin do rải rác đa kênh  <br> • Khôi #3: Trích xuất task và context từ biên bản họp nhóm                                                               | **Bản chất:** Thông tin bị phân tán trên nhiều nền tảng và cập nhật liên tục theo thời gian thực.  <br><br> **Giải pháp:** Workflow/pipeline thu thập dữ liệu đa nguồn → AI phân loại → AI tóm tắt → hiển thị tập trung.                        |
| Trợ lý hỗ trợ & Kiểm định tự động                  | • Minh #2: QA phát hiện object bị bỏ sót trong frame đông  <br> • Minh #3: Giải đáp rule occlusion cho annotator mới  <br> • Khôi #2: Hỗ trợ fix lỗi setup môi trường chạy code            | **Bản chất:** Giảm bottleneck do con người phải kiểm tra hoặc trả lời lặp lại nhiều lần.  <br><br> **Giải pháp:**  <br> 1. Computer Vision để phát hiện lỗi/missing object.  <br> 2. RAG/Knowledge Base để trả lời guideline hoặc lỗi kỹ thuật. |
| Tính toán công thức cố định                        | • Hạnh #2: Tra catalog + tính công thức giá                                                                                                                                                | **Bản chất:** Bài toán logic cố định, cần độ chính xác cao và deterministic.  <br><br> **Giải pháp:** Rule-based engine hoặc hard-code thay vì dùng LLM để tránh hallucination.                                                                 |

---

# Shortlist và score

| Candidate                                                         | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
| ----------------------------------------------------------------- | -------- | ----------- | ---------------- | -------------- | ------------- | ------------------ | ---------------- | ---- |
| BOQ khách → đầu mục chuẩn + spec                                  | 5        | 5           | 4                | 4              | 1             | 5                  | 5                | 29   |
| Học viên bị quá tải thông tin khóa học do rải rác trên nhiều kênh | 5        | 5           | 4                | 5              | 5             | 5                  | 5                | 34   |
| Tìm lại quyết định labeling cho edge case từ Slack/Notion         | 5        | 5           | 4                | 4              | 5             | 4                  | 5                | 32   |

---

# Problem được chọn

## Học viên bị quá tải thông tin khóa học do rải rác trên nhiều kênh

### Vì sao chọn

* Workflow rõ và dễ mô tả before/after.
* Pain xuất hiện hằng ngày và dễ quan sát.
* Có baseline thời gian để đo impact.
* Có thể validate nhanh với học viên và labcoach.
* Có nhiều pattern/tool ngoài thị trường để research.
* Scope phù hợp để làm pilot nhỏ trong lab.

### Vì sao không chọn các bài khác

#### Tìm lại quyết định labeling cho edge case từ Slack/Notion

* Impact tốt nhưng phụ thuộc data access và semantic search.
* Dễ mở rộng thành hệ thống search/agent lớn vượt scope lab.
* Khó validate quality retrieval trong thời gian ngắn.

#### BOQ khách → đầu mục chuẩn + spec

* Workflow rõ nhưng metric chất lượng khó thống nhất.
* Cần domain knowledge chuyên ngành để đánh giá output đúng/sai.
* Pilot khó setup nhanh trong môi trường lab.

---

# Quick validation

Nhóm thực hiện khảo sát nhanh với học viên và labcoach.

| Nguồn               | Số mẫu | Tín hiệu xác nhận                                                     | Tín hiệu phản bác                                | Nhóm điều chỉnh                                           |
| ------------------- | ------ | --------------------------------------------------------------------- | ------------------------------------------------ | --------------------------------------------------------- |
| Interview học viên  | 4      | 3/4 người từng bỏ sót deadline hoặc link lab vì thông tin nằm rải rác | 1 người dùng Notion cá nhân nên ít bị ảnh hưởng  | Thu hẹp scope thành “gom và ưu tiên thông báo quan trọng” |
| Interview labcoach  | 2      | Labcoach phải trả lời lặp lại nhiều câu hỏi giống nhau                | Một số vấn đề do học viên không đọc announcement | Thêm boundary: không thay LMS/channels gốc                |
| Mini poll trong lớp | 8      | 6/8 người phải check từ 3 nền tảng trở lên mỗi ngày                   | Một số người chỉ dùng Discord                    | Bổ sung non-AI alternative: dashboard tập trung           |

---

# Insight sau validation

* Pain lớn nhất không phải thiếu thông tin mà là thông tin bị phân tán.
* Học viên mất thời gian tự tổng hợp và xác nhận cái gì quan trọng.
* Deadline và link lab là loại thông tin bị miss nhiều nhất.
* Labcoach bị interrupt bởi các câu hỏi lặp lại.
* AI phù hợp ở bước summarize và prioritize thay vì thay thế hoàn toàn workflow hiện tại.

---

# Research giải pháp

Nhóm tìm các hướng đã có sẵn thay vì giả định phải tự build toàn bộ từ đầu.

| Nguồn / tool / case                      | Họ giải quyết phần nào?       | Điểm mạnh                                | Khoảng trống / rủi ro               | Bài học cho nhóm              |
| ---------------------------------------- | ----------------------------- | ---------------------------------------- | ----------------------------------- | ----------------------------- |
| Slack + Canvas trong lớp học             | Phân vai giữa LMS và chat     | Dễ tìm lại thông tin theo thread/channel | Dễ overlap nếu không có rule        | Cần “single source of truth”  |
| Digital workplace platforms              | Gom nhiều nguồn về một portal | Giảm context switching                   | Dễ thành thêm một hệ thống phức tạp | Giữ portal đơn giản           |
| Workflow Slack/Discord channel structure | Tổ chức thông tin theo topic  | Giảm loạn thông báo                      | Phụ thuộc discipline của người dùng | Cần guideline sử dụng channel |
| Content curation bằng Notion/Trello      | Cấu trúc nội dung học tập     | Người học dễ theo dõi roadmap            | Cần maintain thường xuyên           | Nên có curriculum map         |
| Information overload training            | Dạy kỹ năng quản lý thông tin | Giảm overload cá nhân                    | Không giải quyết system-level pain  | Cần onboarding cho học viên   |

### Research takeaway

* Không nên build AI agent tự vận hành toàn bộ workflow.
* Hướng phù hợp hơn là:

  * Rule/script để collect dữ liệu.
  * AI để summarize và prioritize.
  * Human review trước khi hành động.
* Portal tập trung quan trọng hơn việc thêm quá nhiều automation.

---

# Workflow before/after

## CURRENT STATE — Quá tải thông tin

```text
[Zalo]
[Discord]
[Outlook]
[Teams]
      ↓
[Học viên tự check nhiều app]
      ↓
[Tự đọc và tổng hợp]
      ↓
[Tự xác định deadline/link]
      ↓
[Không chắc → hỏi lại Labcoach]
      ↓
[Miss deadline hoặc mất thời gian]
```

### Pain hiện tại

* Phải check 3–4 nền tảng mỗi ngày.
* Mất khoảng 45–60 phút/ngày để tổng hợp thông tin.
* Dễ bỏ sót deadline hoặc link quan trọng.
* Labcoach bị hỏi lặp lại nhiều lần.

---

## FUTURE STATE — Workflow tập trung

```text
[Discord/Zalo/Outlook/Teams]
                ↓
[Rule/Webhook collect dữ liệu]
                ↓
[AI phân loại]
                ↓
[AI summarize + highlight deadline]
                ↓
[Portal/Notion Dashboard]
                ↓
[Học viên review]
                ↓
[Hành động]
```

### Kỳ vọng sau cải thiện

* Chỉ cần check một nơi tập trung.
* Giảm thời gian tổng hợp xuống dưới 15 phút/ngày.
* Giảm số câu hỏi lặp lại cho Labcoach.
* Giảm tình trạng miss deadline/lab.

---

# Problem Statement v0

| Field          | Nội dung                                                                |
| -------------- | ----------------------------------------------------------------------- |
| Actor          | Học viên tham gia khóa học/lab sử dụng nhiều kênh để theo dõi thông tin |
| Workflow       | Tự mở nhiều app → đọc thông báo → tìm deadline/link → tự tổng hợp       |
| Bottleneck     | Thông tin phân tán và cập nhật liên tục                                 |
| Impact         | Mất 45–60 phút/ngày; dễ bỏ sót deadline                                 |
| Success Metric | Giảm thời gian tổng hợp và số lần miss thông báo                        |
| Boundary       | AI chỉ hỗ trợ summarize/prioritize                                      |

---

# Rule / Workflow / Agent

| Mức      | Phương án                                        | Khi nào đủ                       | Rủi ro                      | Chọn?              |
| -------- | ------------------------------------------------ | -------------------------------- | --------------------------- | ------------------ |
| Rule     | Dashboard + filter thông báo                     | Đủ nếu chỉ cần tập trung dữ liệu | Không hiểu context          | Không chọn toàn bộ |
| Workflow | Collect dữ liệu → AI summarize → học viên review | Workflow tuyến tính, rõ bước     | AI summarize sai hoặc thiếu | Chọn               |
| Agent    | AI tự đọc, tự nhắc, tự follow-up                 | Chỉ cần khi workflow phức tạp    | Scope lớn, nhiều permission | Chưa chọn          |

## Mức chọn: Workflow

### Vì sao

* Data collection có thể làm bằng webhook/script.
* Pain chính là đọc hiểu và tổng hợp thông tin.
* AI phù hợp ở bước summarize và prioritize.
* Học viên vẫn là người quyết định cuối cùng.
* Chưa cần AI tự lập kế hoạch hay tự follow-up.

---

# Problem Statement v1

| Field                 | Nội dung                                                                                  |
| --------------------- | ----------------------------------------------------------------------------------------- |
| Actor                 | Học viên phải theo dõi thông tin từ nhiều kênh như Zalo, Discord, Outlook và Teams        |
| Workflow              | Mở nhiều app → đọc announcement → tìm deadline/link → tự tổng hợp → hỏi lại nếu chưa chắc |
| Bottleneck            | Tự tổng hợp và xác nhận thông tin mất thời gian vì thông tin phân tán                     |
| Impact                | 45–60 phút/ngày; dễ miss deadline; labcoach bị interrupt nhiều lần                        |
| Success Metric        | Giảm thời gian tổng hợp xuống dưới 15 phút/ngày                                           |
| Boundary              | AI không thay thế nguồn gốc hay tự gửi thông báo                                          |
| AI intervention point | Sau bước collect dữ liệu, trước bước học viên tự đọc                                      |
| Mức chọn              | Workflow                                                                                  |
| Rủi ro & Human review | AI có thể summarize sai → học viên phải review lại nguồn gốc                              |

---

# Final decision

## Decision

* Go với scope nhỏ.
* Validate workflow trước khi build hệ thống hoàn chỉnh.

---

## Pilot nhỏ nhất

### Dataset

* Dùng dữ liệu mẫu từ 2 tuần học gần nhất.

### Workflow pilot

1. Học viên paste announcement từ Discord/Teams/Outlook vào prompt chuẩn.
2. AI draft:

   * summary
   * deadline
   * action items
3. Học viên review trước khi sử dụng.

### Đo lường

* Thời gian tổng hợp thông tin.
* Số lần hỏi lại Labcoach.
* Số deadline/task bị miss.

---

## Exit / rollback

* Nếu học viên vẫn phải đọc lại hơn 70% nội dung gốc trong 2 tuần liên tiếp → rollback về dashboard + filter notification đơn giản.
* Nếu AI summarize sai deadline hoặc sai context → không dùng output trực tiếp.
* Nếu workflow không giảm rõ thời gian tổng hợp → dừng hướng AI summarize.

---

## Decision rationale

### Problem rõ

Thông tin khóa học bị phân tán trên nhiều kênh.

### Workflow rõ

Collect dữ liệu → AI summarize → học viên review.

### Metric rõ

* Giảm thời gian tổng hợp.
* Giảm miss deadline.
* Giảm câu hỏi lặp lại.

### Có non-AI components

* Sync dữ liệu.
* Filter/tagging bằng rule/script.

### AI chỉ nằm ở một bước cụ thể

* Tóm tắt và highlight thông tin quan trọng.

### Human review rõ

* Học viên vẫn là người kiểm tra và quyết định cuối cùng.
