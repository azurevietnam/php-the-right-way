---
title: Server ảo hay Dedicated Servers
isChild: true
anchor:  virtual_or_dedicated_servers
---

## Server ảo hay Dedicated Servers {#virtual_or_dedicated_servers_title}


Nếu bạ có thể làm việc với các hệ thống administration, hoặc muốn học nó, Server ảo hoặc Dedicated Servers 
cho bạn toàn quyền điều khiển môi trường ứng dụng.

### nginx và PHP-FPM

FastCGI Process Manager (FPM) có sẵn trong PHP, tương thích với [nginx], một web server nhẹ, hiệu năng cao, 
dùng ít bộ nhớ hơn Apache và quản lý nhiều request tốt hơn. Điều này cực kỳ quan trọng vì trong máy chủ ảo không có nhiều bộ nhớ.

* [Xem thêm về nginx][nginx]
* [Xem thêm về PHP-FPM][phpfpm]
* [Xem thêm về cài đặt nginx và PHP-FPM an toàn][secure-nginx-phpfpm]

### Apache và PHP

PHP và Apache có lịch sử lâu đời cùng nhau. Apache có nhiều thiết đặt và có sẵn nhiều [modules][apache-modules] 
để kế thừa các chức năng. Là lựa chọn phổ biến cho các shared server và dễ cài đặt cho các PHP framework hay ứng 
dụng mã nguồn mở như Wordpress. Nhưng không may Apache dùng nhiều tài nguyên hơn nginx và không thể quản lý nhiều 
visitor cùng lúc.

Apache có vài thiết đặt cho PHP, thông dụng và dễ nhất là [prefork MPM] với mod_php5. Mặc dù không phải là 
hiệu quả nhất cho bộ nhớ, nhưng đơn giản nhất để dùng. Ghi chú nếu dùng mod_php5 bạn phải dùng prefork MPM.

Nếu bạn muốn siết chặt hơn nữa hiệu năng và sự ổn định bên ngoài Apache, sau đó bạn có thể tận dùng các ưu thế của 
cùng hệ thống FPM như nginx và chạy [worker MPM] hoặc [event MPM] với mod_fastcgi hay mod_fcgid. Thiết đặt này sẽ 
tận dụng bộ nhớ hiệu quả hơn và nhanh hơn hiều nhưng phải set up nhiều hơn.

* [Đọc thêm về Apache][apache]
* [Đọc thêm về Multi-Processing Modules][apache-MPM]
* [Đọc thêm về mod_fastcgi][mod_fastcgi]
* [Đọc thêm về mod_fcgid][mod_fcgid]


[nginx]: http://nginx.org/
[phpfpm]: http://php.net/install.fpm
[secure-nginx-phpfpm]: https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/
[apache-modules]: http://httpd.apache.org/docs/2.4/mod/
[prefork MPM]: http://httpd.apache.org/docs/2.4/mod/prefork.html
[worker MPM]: http://httpd.apache.org/docs/2.4/mod/worker.html
[event MPM]: http://httpd.apache.org/docs/2.4/mod/event.html
[apache]: http://httpd.apache.org/
[apache-MPM]: http://httpd.apache.org/docs/2.4/mod/mpm_common.html
[mod_fastcgi]: http://www.fastcgi.com/mod_fastcgi/docs/mod_fastcgi.html
[mod_fcgid]: http://httpd.apache.org/mod_fcgid/