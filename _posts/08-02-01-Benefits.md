---
title: Lợi ích
isChild: true
anchor:  templating_benefits
---

## Lợi ích {#templating_benefits_title}

Lợi ích chính khi dùng template là sự tách bạch của code và phần còn lại của ứng dụng.
Template có chức năng hiển thị các nội dung được định dạng, không có chức năng tìm kiếm thông tin hay các chức 
năng phức tạp khác. Code của bạn sẽ sạch hơn, dễ đọc hơn, hữu ích cho môi trường là việc nhóm, nơi mà 
các lập trình viên làm việc với code ở server (controllers, models) và người thiết kế làm việc ở client-side.

Template cũng cung cấp sự tổ chức cho code giao diện, được đặt trong thư mục views, trong mỗi file riêng biệt. 
Phương thức tiếp cận này giúp tài sử dụng code khi mà một đoạn code lớn được chia thành nhiều đoạn nhỏ, 
các phần có thề tái sử dụng, thường dược gọi là các partial. Ví dụ, header và footer của trang web có 
thể khai báo như là template, và được kéo vào ở đầu và cuối mỗi file tempalte.

Cuối cùng, tùy thuộc vào thư viện mà bạn dùng, template có thể hỗ trợ thêm bảo mật bằng cách tự động 
escape các nội dung do người dùng tạo ra. Một vài thư viện cung cấp sand-box, nơi mà các template designer 
chỉ được truy cập tới các biến và hàm nằm trong white-list.























