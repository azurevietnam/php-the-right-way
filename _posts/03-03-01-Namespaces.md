---
isChild: true
anchor:  namespaces
---

## Namespaces {#namespaces_title}

Như đã đề cập, cộng đồng PHP rất rộng lớn và cung cấp rất nhiều thư viện. Điều đó có nghĩa là 
một thư viện PHP có thể có một hay nhiều class trùng tên với các class của một thư viện khác. 
Khi hai thư viện này được dùng trong cùng một project (cùng namspace) sẽ xảy ra xung đột và sinh ra lỗi.

_Namespaces_ là giải pháp cho vấn đề này. Bạn có thể hình dung giống như hai file cùng tên có thể cùng 
tồn tại trong một hệ thống khi được chứa trong hai thư mục khác nhau. Và giống như vậy, hai class cùng tên 
chứa trong hai namspace khác nhau có thể cùng tồn tại.

Một điều quan trọng là khi khai báo một namespace cho code của mình, các lập trình viên khác có thể 
sử dụng code của bạn mà không sợ bị xung đột với các thư viện khác.

One recommended way to use namespaces is outlined in [PSR-4][psr4], 
which aims to provide a standard file, class and
namespace convention to allow plug-and-play code.

Một vài đề nghị khi dùng namespace được liệt kê tại [PSR-4][psr4] với mục đích cung cấp một chuẩn cho file 
, class và namespace cho phép sử dụng lại code (plug-and-play code).

Tháng 10 2014 PHP-FIG phản đối chuẩn dành cho autoloading trước đây: 
[PSR-0][psr0], được thay thế bởi
[PSR-4][psr4]. Hiện tại, cả hai vẫn có thể được áp dụng.
PSR-4 yêu cầu PHP 5.3 và nhiều project chạy trên PHP 5.2 áp dụng PSR-0, nhưng ngày càng ít đi. 

Nếu bạn muốn dùng chuẩn autoloading cho ứng dụng mới thì bạn nên tìm hiểu về PSR-4.

* [Đọc thêm về Namespaces][namespaces]
* [Đọc thêm về PSR-0][psr0]
* [Đọc thêm về PSR-4][psr4]


[namespaces]: http://php.net/language.namespaces
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
