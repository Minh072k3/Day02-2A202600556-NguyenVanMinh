# 03 — Individual Reflection

## Đóng góp của Minh trong nhóm

| Hoạt động               | Minh đã làm gì?                                                                      | Kết quả                                                  |
| ----------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------- |
| Scan cá nhân            | Đưa ra 7 problem về OD Labeling, guideline và workflow annotation                  | Nhóm có thêm candidate về AI workflow và semantic search |
| Pitch                   | Pitch problem “Học viên bị quá tải thông tin do rải rác đa kênh”                     | Problem được đưa vào shortlist và chọn làm final scope   |
| Challenge               | Challenge risk của việc build Agent quá rộng và khó validate                         | Nhóm thu hẹp scope về Workflow thay vì Agent             |
| Workflow                | Vẽ current state và future state cho workflow học viên check nhiều kênh              | Nhóm dùng làm workflow chính cho bản final               |
| Research                | Research các case về Slack, LMS integration, digital workplace, information overload | Nhóm thấy nên dùng pattern “AI summarize + human review” |
| Rule / Workflow / Agent | Lập luận chọn Workflow thay vì Agent                                                 | Nhóm thống nhất hướng triển khai cuối cùng               |
| Validation              | Tham gia quick interview với học viên và labcoach                                    | Có evidence về pain thật và baseline thời gian           |
| Problem Statement       | Viết và refine Problem Statement v0 → v1                                             | Scope và boundary rõ hơn                                 |

---

# Bảng dùng AI trong reflection

| Phase             | Tôi dùng AI để làm gì?                                       | AI hữu ích ở đâu?                           | AI sai/hời hợt ở đâu?                                   | Tôi sửa gì                                 |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------- | ------------------------------------------------------- | ------------------------------------------ |
| Scan              | Gợi ý thêm problem về workflow học tập và overload thông tin | Giúp mở rộng nhanh nhiều hướng problem      | Một số problem quá rộng hoặc không có actor rõ          | Loại các problem không có workflow thật    |
| Workflow          | Nhờ AI chuyển mô tả thành Mermaid/workflow                   | Tiết kiệm thời gian trình bày flow          | AI đôi lúc gộp nhiều bước thành một                     | Tách lại step collect → summarize → review |
| Research          | Nhờ AI tìm case/tool tương tự                                | Tìm nhanh các pattern LMS, Slack, dashboard | Một số case quá enterprise hoặc không phù hợp scope lab | Chỉ giữ các pattern có thể pilot nhỏ       |
| Validation        | Nhờ AI gợi ý câu hỏi interview                               | Có thêm câu hỏi để khai thác pain cụ thể    | AI đôi lúc hỏi quá chung chung                          | Sửa câu hỏi theo đúng context lớp học/lab  |
| Problem Statement | Nhờ AI review boundary và metric                             | Giúp problem statement rõ hơn               | AI đề xuất Agent quá sớm                                | Hạ scope về Workflow                       |
| Decision          | Nhờ AI phân tích Rule / Workflow / Agent                     | Giúp so sánh nhanh ưu nhược điểm            | AI thiên về automation quá nhiều                        | Giữ human review là bước bắt buộc          |

---

# Bài học của Minh

* Problem tốt không phải problem “nghe AI nhất”, mà là problem có workflow, actor và metric rõ.
* Workflow visualization giúp thấy rõ:

  * bước nào dùng rule là đủ,
  * bước nào AI thực sự tạo thêm giá trị.
* Không phải lúc nào Agent cũng là lựa chọn đúng.
  Trong case này, Workflow phù hợp hơn vì:

  * luồng xử lý khá tuyến tính,
  * risk thấp hơn,
  * dễ validate nhanh trong lab.
* Research không phải để copy sản phẩm khác, mà để học pattern thiết kế:

  * AI summarize,
  * con người review,
  * không giao toàn quyền cho AI.
* Validation sớm giúp tránh việc chọn problem chỉ vì “nghe hay”.

---

# Nếu làm lại

* Tôi sẽ interview nhiều học viên hơn để có baseline rõ hơn về:

  * thời gian check thông tin,
  * tỷ lệ miss deadline,
  * số lần hỏi lại labcoach.
* Tôi sẽ thử pilot nhỏ sớm hơn thay vì dành nhiều thời gian refine solution.
* Tôi sẽ đo cụ thể hơn:

  * số notification/ngày,
  * số platform phải check,
  * thời gian đọc announcement,
    để metric thực tế và dễ compare hơn.
