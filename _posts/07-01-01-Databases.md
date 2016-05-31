---
title:  Databases
anchor: databases
---

# Databases {#databases_title}

Trong quá trình làm việc, PHP sẽ cần database để lưu trữ và truy xuất thông tin. Có một số cách để liên 
kết và tương tác với database, trước **PHP 5.1.0** các h được khuyến khích là dùng các native driver như 
[mysqli], [pgsql], [mssql], ...

Native driver là lựa chọn tốt nếu bạn chỉ sử dụng một loại database trong ứng dụng, nhưng ví dụ nếu bạn 
vừa dùng MySQL vừa dùng MSSQL, hay bạn cần kết nối tới database Oracle thì bạn sẽ không thê nào dùng chung một driver. 
bạn sẽ cần học thêm API mới cho mỗi loại database.


[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
[mssql]: http://php.net/mssql
