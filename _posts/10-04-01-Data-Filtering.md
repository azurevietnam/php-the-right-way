---
title: Lọc dữ liệu
isChild: true
anchor:  data_filtering
---

## Lọc dữ liệu (Data Filtering) {#data_filtering_title}

KHông bao giờ tin tưởng các input bên ngoài vào code PHP của bạn. 
Luôn luôn làm sạch and validate các input bên ngoài trước khi sử dụng trong code 
Hàm `filter_var()` và `filter_input()` có thể làm sạch text và validate các chuỗi định dạng (như địa chỉ email).

Các input bên ngoài có thể là mọi thứ: `$_GET` và `$_POST`, vài giá trị của `$_SERVER` và 
HTTP request body của hàm `fopen('php://input', 'r')`. Nhớ rằng các input bên ngoài không chỉ giới hạn ở các 
dữ liêu mà người dùng nhập. Các file được upload và download, giá trị của session, cookie và dữ liêu của bên thứ ba 
cũng là input ngoại.
Khi các dữ liệu bên ngoài có thể được lưu trữ, kết hợp, và truy cập sau này, nó vẫn là input ngoài. Mỗi khi 
bạn xuất ra, thực thi, nối, hay kéo dữ liêu vào code, hãy chắc rằng nó đã được lọc và có thể tin tưởng.

Dữ liệu có thể được lọc khác nhau tùy theo mục đích của chúng. Ví dụ khi input không được lọc được xuất ra HTML, 
nó có thể thực thi HTML và javascript trên trang của bạn! Đây là một dạng tấn công khá nguy hiểm (Cross-Site Scripting - XSS). 
Dùng hàm `strip_tags()` để loại bỏ các thẻ html và escape các ký tự đặt biệt dùng hàm `htmlentities()` hoặc `htmlspecialchars()`.

Một ví dụ khác là truyền vào các tùy chọn khi thực thi trên giao diện dòng lệnh. Điều này cực kỳ nguy hiểm, 
và thường là một ý tưởng tồi. Nhưng bạn có thể dùng hàm có sẵn là `escapeshellarg()` để làm sạch các tham số truyền 
qua dòng lệnh.


Một ví dụ cuối cùng là việc chấp nhận input ngoại để xác dịnh file nào sẽ load trong hệ thống file. Điều này 
 có thể bị khai thác bằng cách đổi tên file thành một đường dẫn. Bạn cần phải gỡ bỏ `"/"`, `"../"`, [null bytes][6], 
 hay các ký tự khác có trong đường dẫn để nó không thể mở các file nhạy cảm.

* [Learn about data filtering][1]
* [Learn about `filter_var`][4]
* [Learn about `filter_input`][5]
* [Learn about handling null bytes][6]

### Làm sạch dữ liệu (Sanitization)

Làm sạch sữ liệu loại bỏ (hay escapes) các ký tự không hợp lệ hay không an toàn từ input ngoại.

Ví dụ, bạn có thể làm sạch dữ liệu bên ngoài trước khi xuất ra HTML hay đưa vào câu truy vấn SQL với tính năng 
bind parameter của [PDO](#databases)

Đôi khi bạn phải chấp nhận một số thẻ HTML an toàn, đây là một việc khó khăn và nhiều lập trình viên đã tránh 
việc này bằng cách sử dụng các định dạng khác như Markdown hay BBCode, mặc dù thư viện [HTML Purifier][html-purifier] cũng thực hiện được điều này.

[See Sanitization Filters][2]

### Giải mã đối tượng (Unserialization)

Thật nguy hiểm khi `unserialize()` từ người dùng hay các nguồn không đáng tin cậy.  
Làm như vậy có thể cho phép một số người dùng ác ý có thể khởi tạo đối tượng (với các thuộc tính mà người dùng khai báo). 
Vì vậy bạn nên tránh `unserialize()` các dữ liệu không đáng tin. Trong trường hợp bắt buột phải làm như vậy 
sử dụng tùy chọn [`allowed_classes`][unserialize] của PHP7 để loại đối tượng nào đươc phép unserialize.

### Validation

Validate các input ngoại chứa các dữ liệu được mong đợi. Ví dụ, bạn có thể muốn validate địa chỉ email, số điện thoại, tuổi, ...

[See Validation Filters][3]


[1]: http://php.net/book.filter
[2]: http://php.net/filter.filters.sanitize
[3]: http://php.net/filter.filters.validate
[4]: http://php.net/function.filter-var
[5]: http://php.net/function.filter-input
[6]: http://php.net/security.filesystem.nullbytes
[html-purifier]: http://htmlpurifier.org/
[unserialize]: https://secure.php.net/manual/en/function.unserialize.php
