# Changelog 

Nơi tổng hợp những sự thay đổi của dự án, giúp new coder nhìn qua là biết tổng quan 
dự án đã từng có những tính năng nào, trải qua những lần nâng cấp ra sao. 

Format changelog học theo [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
và cách đánh version thì học theo [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

với mỗi lần update version là một cái `heading 2`, 
gồm một đến ba cái`heading 3`, thuộc 3 mục:

- **Add** : tính năng thêm vào 
- **Change** : tính năng thay đổi / loại bỏ 
- **Fix** : fix bug 

version thì theo format `x.y.z` với 

- `x`: phiên bản lớn, `1.0.0` là phiên bản đầu tiên lên production, 
  khi nâng số này thì thường là một lần update lớn, 
  thậm chí không tương thích với bản cũ (như python 3.x vs python 2.x vậy)
- `y`: phiên bản nhỏ, mỗi lần thêm/sửa/xóa tính năng thì nâng số này. 
- `z`: phiên bản fix bug, mỗi lần release để fix bug thì nâng số này. 

chú ý, phần version thì đặt vào giữa cặp dấu ngoặc vuông `[1.2.3]` để thuận tiện trong việc parse version khi chạy CI/CD

## [1.0.0] - 2026-11-07

### Add

- Phiên bản đầu tiên của ứng dụng trắc nghiệm Giáo lý Hôn nhân K2 2026
- Ngân hàng câu hỏi một lựa chọn, tải từ dữ liệu có kèm giải thích đáp án và liên kết tham khảo
- Chế độ Luyện tập (không giới hạn thời gian, kiểm tra đáp án từng câu) và Thi thử (đồng hồ đếm ngược, xem đáp án sau khi nộp bài)
- Chọn số câu hỏi trước khi làm bài, xem kết quả và xem lại bài làm
- Lưu và tiếp tục bài làm dang dở
- Chuyển giao diện sáng/tối
- Hiển thị thông tin phiên bản trên header của `index.html`
