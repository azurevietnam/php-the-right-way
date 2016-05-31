---
anchor: dependency_management
---

# Dependency Management {#dependency_management_title}

Giả sử bạn đang tạo ra một trang web sử dụng các thư viện như Bootstrap và 
jQuery. Cách làm thông thường là vào website chứa những thư viện đó, download các package và đặt nó 
ở 1 folder nào đó trong project của bạn. Nhưng bây giờ, bạn sẽ làm gì khi muốn update lên phiên bản mới 
nhất? Bạn lại làm lại các công việc trên, ghi đè vào phiên bản cũ ?
Hãy giả định bạn muốn roll back chúng về phiên bản cũ nhưng roll back về đâu? Bạn sẽ phải 
tìm các phiên bản cũ hơn và thử chúng lần lượt cho đến khi tìm được phiên bản đúng.
Thậm chí nếu liệt kê tất cả ra, có lẽ bạn sẽ nhầm lẫn nó với project của người khác. Liệu họ có đang 
sử dụng thư viện không? Nếu có, nó được cài đặt ở đâu và đó là phiên bản nào.
Vấn đề có vẻ không lớn lắm đối với một project nhỏ nhưng hãy thử tưởng tượng một project 
với 8-10 dependencies - mà đó vẫn chưa phải là nhiều. Quản lý mọi thứ theo một module xem chừng 
rất khó khả thi hay ít nhất là sẽ tốn thời gian.
Dependency Management giải quyết những vấn đề này bằng cách automating (tự động hóa) 
và standardizing (tiêu chuẩn hóa). Việc cài đặt các dependencies như Foundation, jQuery, Twig, Symphony, 
logging modules được thực hiện một cách tự động. Các phiên bản ưa dùng cũng có thể được chỉ định để 
chống xung đột cho từng project.
Một dependency manager chuẩn hóa cách các package được lưu trữ và nơi chúng được sử dụng. 
Trong thực tế điều này có nghĩa là mỗi project sử dụng cùng một dependency manager 
sẽ có cấu trúc folder của các dependency giống nhau. (trích [http://fsd14.com/])

Có hai phiên bản quản lý cho PHP - [Composer] và [PEAR]. Composer hiện tại là phổ biến nhất cho PHP.
Tìm hiểu về lịch sử của PEAR cũng là một ý hay.


[Composer]: /#composer_and_packagist
[PEAR]: /#pear
