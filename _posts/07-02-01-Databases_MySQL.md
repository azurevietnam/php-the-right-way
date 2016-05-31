---
isChild: true
title:   MySQL Extension
anchor:  mysql_extension
---

## MySQL Extension {#mysql_extension_title}

[Mysql] cho PHP khá là lỗi thời và được thay thế bởi: 

- [mysqli]
- [pdo]

[Mysql] đã bị ngừng phát triển, và [ngưng hỗ trợ trong PHP 5.5.0]
[mysql_deprecated], và **bị [chính thức loại bỏ trong PHP 7.0][mysql_removed]**.

Xem xét các cài đặt trong file `php.ini` để thấy các module nào đang được sử dụng. 
Tìm kiếm `mysql_*` trong project, nếu các hàm như `mysql_connect()` và `mysql_query()` hiện ra thì 
`mysql` được dùng trong project đó.

Ngay cả khi bạn không dùng PHP 7.0 yet, nếu không cập nhật các thay dổi này sớm thì sẽ dẫn tới nhữ khó khăn 
 không nhỏ khi PHP 7.0 được nân cấp. Lựa chọn tốt nhất là thay thế mysql bằng [mysqli] hay [PDO] trong  
ứng dụng của bạn.

**Nếu bạn đang nân cấp từ [mysql] lên [mysqli], bạn chỉ cần thay thế `mysql_*` bằng `mysqli_*` trong các 
hàm cũ. Nhưng không chỉ có vậy, mysqli còn cung cấp các tính năng mới như parameter binding, 
tính năng này cũng có trong [PDO][pdo].**

* [PHP: Choosing an API for MySQL][mysql_api]
* [PDO Tutorial for MySQL Developers][pdo4mysql_devs]

[mysql]: http://php.net/mysql
[mysql_deprecated]: http://php.net/migration55.deprecated
[mysql_removed]: http://php.net/manual/en/migration70.removed-exts-sapis.php
[mysqli]: http://php.net/mysqli
[pdo]: http://php.net/pdo
[mysql_api]: http://php.net/mysqlinfo.api.choosing
[pdo4mysql_devs]: http://wiki.hashphp.org/PDO_Tutorial_for_MySQL_Developers
