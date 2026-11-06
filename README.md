# Trắc nghiệm Giáo lý Hôn nhân K2 – 2026

Ứng dụng web trắc nghiệm một file, giúp ôn tập và thi thử bộ câu hỏi Giáo lý Hôn nhân (khóa K2, 2026). Viết bằng HTML/CSS/JavaScript thuần (Vanilla JS), không cần cài đặt, không cần server, không phụ thuộc thư viện ngoài.

## Cấu trúc dự án

| File | Mô tả |
| --- | --- |
| `index.html` | Ứng dụng hoàn chỉnh (giao diện + logic). Dữ liệu câu hỏi được nhúng sẵn trong thẻ `<script id="quiz-data" type="application/json">`. |
| `trac_nghiem.json` | Ngân hàng câu hỏi gốc (132 câu, loại `single_choice`). Dùng làm nguồn để cập nhật dữ liệu nhúng trong file HTML. |

## Cách sử dụng

Mở trực tiếp file `index.html` bằng trình duyệt hiện đại (Chrome, Edge, Firefox, Safari). Không cần chạy server hay kết nối mạng.

## Tính năng

- **Hai chế độ làm bài**
  - *Luyện tập*: không giới hạn thời gian, có nút "Kiểm tra đáp án" để xem đúng/sai ngay từng câu.
  - *Thi thử*: đồng hồ đếm ngược (mặc định 30 phút, cho phép 1–300 phút), chỉ hiển thị đáp án sau khi nộp bài; tự nộp khi hết giờ.
- **Tùy chọn bộ đề**: chọn số câu (10 / 20 / 50 / tất cả), đảo thứ tự câu hỏi, đảo thứ tự đáp án.
- **Làm bài**: thanh điều hướng danh sách câu, tìm kiếm và lọc câu hỏi, đánh dấu câu cần xem lại, thanh tiến độ, thống kê số câu đã trả lời/chưa trả lời/đã đánh dấu.
- **Phím tắt**: `1`–`9` chọn đáp án, `←` `→` chuyển câu, `Esc` đóng ngăn danh sách câu hỏi (trên màn hình nhỏ).
- **Kết quả**: biểu đồ tròn, phần trăm, số điểm, thời gian đã dùng và xếp loại:
  - ≥ 90%: Xuất sắc
  - ≥ 75%: Tốt
  - ≥ 50%: Đạt
  - < 50%: Cần cải thiện
- **Xem lại bài làm**: tìm kiếm và lọc theo trạng thái từng câu.
- **Luyện tập lại câu sai**: tạo lượt luyện tập mới chỉ gồm các câu làm sai (tùy chọn gồm cả câu chưa trả lời).
- **Lưu tự động**: tiếp tục lượt làm bài đang dở khi tải lại trang; lưu lịch sử 20 lượt gần nhất.
- **Giao diện**: sáng/tối, responsive cho điện thoại, hỗ trợ truy cập (ARIA, điều hướng bàn phím, tôn trọng `prefers-reduced-motion`).

## Dữ liệu lưu trên trình duyệt

Ứng dụng dùng `localStorage` (không gửi dữ liệu đi đâu) với các khóa:

- `quizapp.session.v1` – phiên làm bài hiện tại
- `quizapp.history.v1` – lịch sử làm bài
- `quizapp.prefs.v1` – tùy chọn đã chọn lần trước
- `quizapp.theme` – giao diện sáng/tối

Xóa dữ liệu trang web trong trình duyệt để đặt lại toàn bộ.

## Định dạng ngân hàng câu hỏi

`trac_nghiem.json` là mảng các câu hỏi:

```json
[
  {
    "id": "q-001",
    "type": "single_choice",
    "content": "Nội dung câu hỏi?",
    "options": [
      { "id": "A", "text": "Phương án A" },
      { "id": "B", "text": "Phương án B" }
    ],
    "correctAnswer": "B"
  }
]
```

Quy tắc kiểm tra dữ liệu khi tải (câu không hợp lệ sẽ bị bỏ qua và hiển thị cảnh báo trên màn hình chào):

- `id` bắt buộc, không rỗng và không được trùng.
- `type` hiện chỉ hỗ trợ `single_choice`.
- `content` không được rỗng.
- `options` có từ 2 đến 6 phương án, mỗi phương án có `id` (không trùng) và `text`.
- `correctAnswer` phải là `id` của một trong các phương án.

## Cập nhật nội dung câu hỏi

1. Chỉnh sửa `trac_nghiem.json`.
2. Thay nội dung thẻ `<script id="quiz-data" type="application/json">…</script>` trong `index.html` bằng nội dung JSON mới (dạng một dòng hoặc nhiều dòng đều được).
3. Mở lại file HTML để kiểm tra.
