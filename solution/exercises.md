# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Nội dung chính hầu như giống nhau vì mô hình đều chọn nói về Hang Sơn Đoòng nhưng cách diễn đạt và mức độ chi tiết thay đổi khi tăng temperature lên. Temperature thấp cho câu trả lời ổn định và chính xác hơn. Trong khi temperature cao tạo ra câu văn phong phú hơn, thêm nhiều mô tả hơn ở cuối nhưngg dễ xuất hiện khác biệt hoặc thiếu nhất quán về thông tin như chiều dài hang động.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ chọn temperature khoảng 0.5 chatbot hỗ trợ khách hàng. Mức này giúp câu trả lời vẫn ưu tiên độ ổn định, rõ ràng và chính xác nhưng vẫn có được sự tự nhiên trong giao tiếp mà không quá ngẫu nhiên hoặc sáng tạo ngoài ý muốn.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Với cùng mức sử dụng thì GPT-4o đắt hơn khoảng 16.7 lần so với GPT-4o-mini.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> Chi phí cao hơn của GPT-4o là xứng đáng trong các tác vụ cần chất lượng lập luận cao và độ chính xác cao như hỗ trợ nghiên cứu khoa học. GPT-4o-mini phù hợp hơn cho các tác vụ khối lượng lớn, lặp lại và không quá phức tạp như Chatbot hỗ trợ khách hàng hằng ngày.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các tình huống người dùng phải chờ phản hồi dài hoặc có tính tương tác cao, như chatbot hỗ trợ khách hàng, trợ lý học tập, hoặc sinh nội dung nhiều phần. Bởi vì người dùng thấy kết quả xuất hiện ngay nên cảm giác nhanh hơn và ít bị đứng màn hình. Ngược lại, non-streaming phù hợp hơn khi cần kết quả hoàn chỉnh một lần để xử lý tiếp (ví dụ trả về JSON chuẩn, chạy pipeline backend, logging...), vì cách này đơn giản hơn trong triển khai.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
