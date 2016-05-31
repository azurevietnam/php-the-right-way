---
title: Các file thiết đặt
isChild: true
anchor:  configuration_files
---

## Các file thiết đặt (Configuration Files) {#configuration_files_title}

Khi tạo một file thiết đạt cho ứng dụng, bạn nên tuân theo các phương thức  sau:

- File thiết nên được chứa tại một nơi không thể được truy cập trực tiếp.
- Nếu phải lưu file trong thư mục gốc của web, hãy lưu với dạng `.php` để chắc rằng các thông tin sẽ không hiện ra  
trình duyệt với dạng text.
- Thông tin trong file thiết dặt cần được bảo vệ bằng cách mã hóa, hay hạn chế permission.
- Không nên commit các file thiết dặt chứa những thông tin nhạy cảm như password, API token, ...
